---
title: "howto convert aac to flac or mp3"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by Old Jimma on 2012-02-21
Hi Ubuntu Community:

I am using streamripper to rip music from radio stations to play on my mp3 player. Here is the code I use:

[PHP]
NOW=$(date +"%y-%m-%d")
cd "/home/philipsmith/Music/RADIO STATIONS/KPLU"
rm *.aac
rm *.flac
streamripper "http://icy1.abacast.com:80/kplu-jazz24aac-64" -d "/home/philipsmith/Music/RADIO STATIONS/KPLU" -s -a -A -l 10800
rm *.cue
mv *.aac "KPLU - $NOW.aac"
[/PHP]


For the radio station in this code, an aac file is ripped.

My mp3 player plays flac and mp3 files but not aac files. [-X

I want to add one line of code at the end of this to convert the ripped aac file to a flac or mp3 file.

I've scoured the web to learn how to do this, but can't find it or can't understand it.

Can somebody suggest a line of code that will convert the aac file I rip to either an mp3 or flac? 

:?

Thank you!
Phil de Duluthistan

---

### Post by _0R10N on 2012-02-21
Hi, follow the first answer given here [http://askubuntu.com/questions/35457/converting-aac-to-mp3-via-command-line](http://askubuntu.com/questions/35457/converting-aac-to-mp3-via-command-line)

I used that tool some months ago to convert mp3 files to m4a, and it worked pretty well.

---

### Post by ron999 on 2012-02-21
Hi
The method suggested by _OR1ON above will probably be OK. :)
```
ffmpeg -i "KPLU - $NOW.aac" -acodec libmp3lame -ab 128k "KPLU - $NOW.mp3"
```

---

### Post by Old Jimma on 2012-02-22
Hi Guys:
Thank you very much for your replies. 

When I tried the ffmpeg code, it didn't run... when I pressed return after entering the line of code you suggested, it have me a carrot... and did not produce the desired mp3 file.

Is there an option of flag that I need to set for ffmpeg?

Here is the code with the carrot:



[PHP]
$ ffmpeg -i "KPLU - $NOW.aac" -acodec libmp3lame -ab 128k "KPLU - $NOW.mp3
> 
[/PHP]


Thanks,
Phil

---

### Post by yetiman64 on 2012-02-22
You are missing the closing quotation marks at the end of the ffmpeg code line. That causes the effect showing in your results.

I'd suggest try again with the quotes closed, it looks as though that should work.

---

