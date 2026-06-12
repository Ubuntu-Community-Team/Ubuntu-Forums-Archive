---
title: "Good video converter software."
date: 2012-08-04
forum: New to Ubuntu
---

### Post by Arendyl on 2012-08-04
I am looking for a good video converter program, mostly to converter .mkv/.ogg to .3pg (my phone) formats. I need to be able to choose the audio track when selecting the files (for dual-audio files), and I need to be able to queue many videos at the same time. Preferably I would like to have it as a program in that i can open, not a command-line program, but that's optional.

My favorite Windows program to do this is freemake, so if anyone has a program similar, or can help me get it to run in wine (the problem is you have to have .net), I would be grateful. 

Thanks for your time.

-Arendyl

---

### Post by thatguruguy on 2012-08-04
> **Arendyl said:**
> I am looking for a good video converter program, mostly to converter .mkv/.ogg to .3pg (my phone) formats. I need to be able to choose the audio track when selecting the files (for dual-audio files), and I need to be able to queue many videos at the same time. Preferably I would like to have it as a program in that i can open, not a command-line program, but that's optional.

My favorite Windows program to do this is freemake, so if anyone has a program similar, or can help me get it to run in wine (the problem is you have to have .net), I would be grateful. 

Thanks for your time.

-Arendyl

Try [handbrake]("http://handbrake.fr/").

---

### Post by Bufeu on 2012-08-04
You should take a look at HandBrake.

---

### Post by HermanAB on 2012-08-04
Handbrake is a wrapper around ffmpeg.  So if you are courageous, then you can run ffmpeg directly off the command line.

---

### Post by Arendyl on 2012-08-05
Handbrake seems to be working, but there is no option for .3gp output. Any suggestions?

---

### Post by blueshead on 2012-08-05
Maybe this app?     [http://www.miksoft.net/mobileMediaConverter.php]("http://www.miksoft.net/mobileMediaConverter.php")

---

### Post by Arendyl on 2012-08-05
> **blueshead said:**
> Maybe this app?     [http://www.miksoft.net/mobileMediaConverter.php]("http://www.miksoft.net/mobileMediaConverter.php")

This app doesn't play nicely with matroska (.mkv) files. The output if what I want, but I don't have the right input for it. Also, won't let me choose audio with .ogg files.

If only I could combine Handbarke and this one. Sigh.

---

### Post by little_penguin on 2012-08-06
You could also try WinFF and Avidemux.

---

### Post by yuvraj23 on 2012-08-06
Am using Transmaggedon.. Its good if you are converting a video for a mobile device

---

### Post by Arendyl on 2012-08-06
> **little_penguin said:**
> You could also try WinFF and Avidemux.

Will not let me choose audio file. Will not let me add multiple files simultaneously.

---

### Post by FakeOutdoorsman on 2012-08-07
Refer to the *-map* option if you decide to try ffmpeg.

---

### Post by vexorian on 2012-08-07
I just use a combination of avidemux and ffmpeg. ffmpeg when avidemux can't do something. I mean, nothing stops us from using more than one tool, right?

---

