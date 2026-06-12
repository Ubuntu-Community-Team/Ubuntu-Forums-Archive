---
title: "Is it me or MP4Box?"
date: 2011-10-11
forum: Programming Talk
---

### Post by xzero1 on 2011-10-11
This bash code snippet is intended to concurrently run 2 copies of ffmpeg overwriting the old files then after both complete, remove the old MP4VID.mp4 file and finally run MP4Box to combine raw.mp3 and raw.h264 into MP4VID.mp4.

The problem is sometimes it works and sometimes MP4Box returns "cannot find H264 start code" even though I use the *same* source file. Is there a problem with the code? Could it possibly be something to do with the pipes?:confused:

If more context is required see this [long] post: [http://forums.precentral.net/hp-touchpad/302824-tp-mediatomb-streaming.html]("http://forums.precentral.net/hp-touchpad/302824-tp-mediatomb-streaming.html")


```
video_common() {
PATH1="/media/tempStorage"
PATH2="/dev/shm"
ffmpeg -i "$1" -vcodec copy -y -f h264 "$PATH1"/raw.h264 & ffmpeg -i "$1" -acodec libmp3lame -ac 2 -ab 256k -y -f mp3 "$PATH2"/raw.mp3
rm -f "$PATH1"/MP4VID.mp4
MP4Box -fps 59.940 -add "$PATH1"/raw.h264 -add "$PATH2"/raw.mp3 -inter 100 -tmp "$PATH1" "$PATH1"/MP4VID.mp4; cat "$PATH1"/MP4VID.mp4 > "$2"
}
```

---

### Post by Bachstelze on 2011-10-11
Probably a race condition.

---

### Post by xzero1 on 2011-10-11
Please elaborate.

---

