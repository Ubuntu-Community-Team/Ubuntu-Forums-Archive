---
title: "Video Format Converter"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by dan93z28 on 2008-08-13
Hello i have a real basic and simple question.  I would like to convert some videos that i have in .avi format to a format that i could burn to a dvd or vcd and play on a dvd player.  What programs work well for this kind of task.

---

### Post by halitech on 2008-08-13
if it is a single movie or show, I use Devede (in the repos). If it is multiple episodes or you want something with a menu, ManDVD is the way I'd go (not in th repos but found on getdeb)

---

### Post by Crafty Kisses on 2008-08-13
> **dan93z28 said:**
> Hello i have a real basic and simple question.  I would like to convert some videos that i have in .avi format to a format that i could burn to a dvd or vcd and play on a dvd player.  What programs work well for this kind of task.

There is mencoder, you can install mencoder by doing the following:
```
sudo aptitude install mencoder
```
Then after that's installed, you can convert the video by doing:
```
mencoder -idx input.ogg -ovc lavc -oac mp3lame -o output.avi 
```
That's just an example, but you get the point.

---

### Post by dan93z28 on 2008-08-13
Thank you, Devede worked great

---

### Post by halitech on 2008-08-13
glad to hear :) if that solved it for you, don't forget to mark the thread solved :)

---

