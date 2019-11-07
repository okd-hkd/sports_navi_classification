# Sports navi から　スポーツニュースを取得してスポーツニュース識別器生成


## 学習手順

1. wakachi.pyでスクレイピングしてデータセットを作成(Dataset_all_catogories_from_SportsNavi_ftformat.txt)

2. 次のコマンドで1で作成したデータセットをシャッフルして新しいファイルを作成

```shell
shuf Dataset_all_catogories_from_SportsNavi_ftformat.txt　> train_dataset_shuffled.txt
```

3. train_dataset_shuffled.txt のうち20%程度を切り取って
test_dataset_shuffled.txt　を作成

4. 次のコマンドで学習（教師あり）

```shell
./fasttext supervised -input train_dataset_shuffled.txt -output model001
```

5. モデルの推論結果を確認
```shell
./fasttext predict model001.bin - 5
```

6. テストデータを与えてモデルの精度を確認
```shell
./fasttext test model001.bin test_dataset_shuffled.txt 
```

出力例
N  3000
P@1  0.124
R@1  0.0541
Number of examples: 3000
