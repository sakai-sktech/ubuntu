# ubuntu
Ubuntu導入後の設定等 兼備忘録

## apt-line

妙にjp.archive.ubuntu.comが遅いのでこちらに変更
非公式リポジトリではあるが速いのとIPv6対応しているので...

```
#変更前の参照先
jp.archive.ubuntu.com/ubuntu

#変更後の参照先
ftp.iij.ad.jp/pub/linux/ubuntu/archive
```

スクリプトで一気に変更するのはNet上に転がってるので、備忘録的にviでの置換をメモ

`sudo vi /etc/apt/sources.list`でsources.listを編集

`:%s`で全体置換モードにして後は、sedと同じような置換のしかた。ディレクトリの区切り文字`/`を`\`でエスケープするのを忘れないように

```
:%s/jp.archive.ubuntu.com\/ubuntu/ftp.iij.ad.jp\/pub\/linux\/ubuntu\/archive/
```

## font

PlemolJP等、フォントを持ってきた後のインストール作業

一連のフォント群を置いたフォルダに移動して下記のように実行。`FONTDIR`の設定や、`cp plemol*`の部分はインストールするフォントに合わせて変えればいい。

```sh
FONTDIR=/usr/share/fonts/plemoljp
sudo mkdir ${RONTDIR}
sudo cp plemol* ${FONTDIR}
sudo chmod 755 ${FONTDIR} -R
# ここまででフォントのコピーと権限設定終わり

# fontキャッシュを更新
sudo fc-cache -fv
```
