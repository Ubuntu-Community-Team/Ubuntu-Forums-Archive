---
title: "No audio while playing videos."
date: 2017-03-11
forum: New to Ubuntu
---

### Post by jmadiwale on 2017-03-11
Hi Guys,

I'm new to ubuntu. Just installed Ubuntu 16.04 and all is good. But when i run a video file(e.g. webm) with built-in videos or VLC there is no sound.
From settings I checked that 'Sound Test' works fine. And if i play an audio file that too works ok.

I tried a few suggestions from this forum but couldn't make this work. Please help.

---

### Post by RobGoss on 2017-03-12
Hello and welcome, I'm assuming you also checked to see it anything was muted as well?

Give this a try and see if you can get your sound going sometimes the soud level for the mixer is to low [https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)

---

### Post by jmadiwale on 2017-03-13
Thanks.
I tried this mixer settings and changed everything to unmutted. Still there is no sound for video files. If I run an audio file in VLC it works but when i run a video file it makes no sound.

---

### Post by RobGoss on 2017-03-13
>  I tried this mixer settings and changed everything to unmutted. Still there is no sound for video files.

Are you able to hear sound when watching let's YouTube videos?

Run this command:
```
 lspci  
```

This will list the hardware on your machine post the results using the **code tags**

---

### Post by sp40140 on 2017-03-16
Is your computer connected to TV or monitor?
What cable are you using to connect (HDMI, VGA, DisplayPort, DVI)?
What kind of video card do you have?

---

