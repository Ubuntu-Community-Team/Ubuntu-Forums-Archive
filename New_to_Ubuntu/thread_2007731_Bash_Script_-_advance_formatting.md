---
title: "Bash Script - advance formatting"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by Deepak Jindal on 2012-06-21
I am trying to write a script in bash to search whole drive and search video file properties for its resolution and report in terminal

example: train.avi is 1920x1080
============================================================
Deepak@AMD64:~/Videos$ mminfo train.avi
train.avi
|       type: AVI 
|      media: MEDIA_AV
|     artist: By Noir
|       mime: video/avi
|       hash: 17144162f503dc13
|     length: 5632.04
|      delay: 0.0
|   software: VirtualDubMod 1.5.10.2 (build 2540/release)
+-- Video Track #1
|    |      media: MEDIA_VIDEO
|    |     length: 5632.04
|    |      codec: DivX v5
|    |      width: 640
|    |     height: 272
|    |        fps: 25.0
|    |     fourcc: DX50
+-- Audio Track #1
|    |      media: MEDIA_AUDIO
|    |   channels: 2
|    | samplerate: 48000
|    |      codec: MPEG Layer 3
|    |     fourcc: 0x55
===============================================================
Now, I just want line 1, 14, and 15 from this output. It should be like "train.avi 640x272"

any suggestions how to do this (through cut, egrep etc).

---

### Post by amauk on 2012-06-21
Pipe the output into sed, then instruct sed to only print certain line numbers

```

mminfo train.avi | sed -n '1,14,15p'

```

I'd suggest a different method, though
I can see the line numbers being different depending on the video container format and/or codecs used

You may want to check this out
[http://ubuntuforums.org/showthread.php?p=9539967#post9539967](http://ubuntuforums.org/showthread.php?p=9539967#post9539967)

---

### Post by Lars Noodén on 2012-06-21
I would try it with Awk or Perl.

Here's an attempt with [Awk](http://manpages.ubuntu.com/manpages/precise/en/man1/awk.1posix.html):

```

mminfo train.avi \
| awk 'NR==1 {NAME=$1 }; \
  $3 == "width:" {WIDTH=$4} ; \
  $3 == "height:" {HEIGHT= $4}; \
  END {print NAME " " WIDTH "x" HEIGHT}'

```

---

### Post by codemaniac on 2012-06-21
Would be a good idea to choose "|" as separator .

```
mminfo train.avi | awk -F"|" 'NR==1{print} NR ~ /1[4-5]/{print $3}'
```

however amauk's idea to use sed saves few keystrokes .

---

### Post by Deepak Jindal on 2012-06-21
Thanks guys for quick reply, exactly what I wanted, closing as solved.:KS

---

