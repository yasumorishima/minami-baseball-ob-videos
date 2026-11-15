# minami-baseball-ob-videos

横浜市立南高校野球部OB会サイト（https://minami-baseball-ob.vercel.app/）に載せる短い動画の置き場です。
GitHub Pages（https://yasumorishima.github.io/minami-baseball-ob-videos/）から配信します。

- 置き場所: `<年>/<月日>-<内容>/NN.mp4`
- 1 ファイル 100MB 未満（GitHub の上限）・Pages のサイト全体で 1GB まで。Git LFS は Pages から配信されないので使わない。

## サイトに出すまで

1. 動画を `ffmpeg -i in.mp4 -c copy -map_metadata -1 -movflags +faststart NN.mp4` で整える（再エンコードなし・メタデータを落とし、先頭から再生できる形にする）。
2. `<年>/<月日>-<内容>/NN.mp4` に置いて commit・push する。Pages に反映されたら、URL が 200 を返すかを確かめる。
3. サイトの DB（`videos` 表）に、試合結果か予定に紐付けて `video_type = 'upload'`・`storage_path = <Pages の URL>` の行を作る。サイトはその URL をそのまま `<video>` で再生する。

DB への登録の手順と決まりは、サイトの repo（`yasumorishima/minami-baseball-ob`）の `CLAUDE.md` §3.4b にあります。長い映像（ライブ配信のアーカイブなど）はここに置かず、YouTube の URL で登録します。
