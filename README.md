# ClassificationOfDrumSound

## このレポジトリの目的
機械学習で音を扱うための練習を行ったのでその共有です。

## 使用環境とライブラリ
- Google Colaboratry
- データの保存、処理にnumpy
- 音源データの前処理にLibROSA
- 機械学習モデルにSklearn

## 手法と結果
ドラム音の分類をSVMを使い行いました。
- Kick 66個
- Snare 81個
- openHihat 42個
- closeHihat 57個
- Crash 22個
- Tom 65個

の合計333個のwav形式のone-shotで、44100HZのデータを使い学習、テストを行いました。

まず、すべてのドラムデータの時間を0.2秒に調整。
LibROSAを使い、その音源データをMFCCという音声特徴量に変換。     
MFCCは最終的にサンプリングレートを176400、次元数を40にしたときに良いパフォーマンスを得られました。

最終チューニングでの結果は、ランダムに訓練データとテストデータを8:2で分けて訓練しテストするというのを100回行った時、平均正答率が84％でした。

ドラム音源の特性上、人間でも判別が付かないような音もあるので100％に近いパフォーマンスは期待できません。
しかし、無音区間の除去やデータの質、量の確保、他の機械学習モデルの使用などの改善点は挙げられるので、他のアプローチも試したいです。
