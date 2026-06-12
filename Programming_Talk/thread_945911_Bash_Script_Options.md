---
title: "Bash Script Options?"
date: 2008-10-12
forum: Programming Talk
---

### Post by RATM_Owns on 2008-10-12
I'm making a simple YouTube video to MP3 script (in bash) and is there any way that if I enter
[quote]yt2mp3 --keep-vid[/code]
It will also keep the downloaded YouTube video?

Current script:
```
#!/bin/bash
echo "Enter the URL of the YouTube video to start downloading."
read VIDEO
echo "Downloading..."
rm -rf "tmp.flv"
youtube-dl $VIDEO -o "tmp.flv"
clear
echo What is the artist of the song?
read ARTIST
echo
echo What is the name of the song?
read NAME
echo
ffmpeg -i "tmp.flv" "${ARTIST} - ${NAME}.mp3"
rm -rf "tmp.flv"
echo
echo "YouTube video converted! Yay!"
```

---

### Post by Sam on 2008-10-12
```
#!/bin/bash
echo "Enter the URL of the YouTube video to start downloading."
read VIDEO
echo "Downloading..."
rm -rf "tmp.flv"
youtube-dl $VIDEO -o "tmp.flv"
clear
echo What is the artist of the song?
read ARTIST
echo
echo What is the name of the song?
read NAME
echo
ffmpeg -i "tmp.flv" "${ARTIST} - ${NAME}.mp3"
[COLOR="Red"]if [ "$1" != "--keep-vid" ] ; then[/COLOR]
    rm -rf "tmp.flv"
[COLOR="Red"]fi[/COLOR]
echo
echo "YouTube video converted! Yay!"
```

---

### Post by FakeOutdoorsman on 2008-10-12
I recommend changing:
```
ffmpeg -i "tmp.flv" "${ARTIST} - ${NAME}.mp3"
```
to
```
ffmpeg -i "tmp.flv" -acodec copy "${ARTIST} - ${NAME}.mp3"
```
Now ffmpeg will copy the mp3 audio stream instead of re-encoding it.  This will be faster and will preserve the quality.

---

