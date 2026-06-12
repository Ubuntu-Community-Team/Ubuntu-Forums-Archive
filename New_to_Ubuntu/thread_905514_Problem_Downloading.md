---
title: "Problem Downloading"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by 3DGE on 2008-08-30
I have been trying to download Ubuntu from different servers all morning and I have been having no luck. I keep getting an error saying it could not be downloaded once it gets to around 80% complete. Is there something wrong with all the download links or is it just my computer. Also how long does it take for the CD to be shipped out because I am starting to get annoyed by the error.
Or is there some other place I could download it from I am located in Hamilton, Ontario, Canada.

---

### Post by gmxgeek on 2008-08-30
CD shipping takes anywhere from 1 - 10 weeks depending on various conditions. Don't know about download errors.

---

### Post by cariboo on 2008-08-30
Have you tried one of the torrent downloads, make sure you have something like µTorrent installed. You can get it from most popular download sites.

Jim

---

### Post by Sarah L on 2008-08-30
It's very unlikely that many or all of the servers are experiencing an error at the same time, especially the same error.

The likely reason that your download always stops at around 80% is because you're running out of disk space before the download is able to complete. CD images are around 650-700 MB in size, so make sure you have at least that much free space on your hard drive.

---

### Post by 3DGE on 2008-08-30
Ok well I restarted my computer and I just tried downloading the file in Firefox, I was using Internet Explorer before and somehow it worked. Thanks for the help though and I have 20 GB free on my computer so it wouldn't be a  disk space problem. One more question though will I be able to use a program on Ubuntu that will allow me to use MSN?

---

### Post by k8bopibu on 2008-08-30
Yes, you can use Pidgin or aMSN... there are more but these two pop up.

~k8

---

### Post by drubin on 2008-08-30
> **3DGE said:**
> Ok well I restarted my computer and I just tried downloading the file in Firefox, I was using Internet Explorer before and somehow it worked. Thanks for the help though and I have 20 GB free on my computer so it wouldn't be a  disk space problem. One more question though will I be able to use a program on Ubuntu that will allow me to use MSN?

Pidgin comes standard on ubuntu.  [http://pidgin.im](http://pidgin.im)

---

### Post by shankhs on 2008-08-30
> **3dge said:**
> ok well i restarted my computer and i just tried downloading the file in firefox, i was using internet explorer before and somehow it worked. Thanks for the help though and i have 20 gb free on my computer so it wouldn't be a  disk space problem. One more question though will i be able to use a program on ubuntu that will allow me to use msn?

ie sucks!!!!
Hence Proved!!!
 
:lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by 3DGE on 2008-08-30
Okay I am using Ubuntu now and when I try to play a song in mp3 format it wont play still. Could someone help

---

### Post by drubin on 2008-08-30
[http://www.psychocats.net/ubuntu/mp3](http://www.psychocats.net/ubuntu/mp3)

---

### Post by 3DGE on 2008-08-30
I did that but there is still no sound.
And I know my speakers are plugged in and working proprely because I just went back to XP and it worked.

---

### Post by drubin on 2008-08-30
No sound for any thing or just mp3's?

---

### Post by eybaby on 2008-08-30
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by 3DGE on 2008-08-30
No sound for anything

---

### Post by 3DGE on 2008-08-30
I made sure the volume on Rhythmic Music Player and I also tried the mp3 in Movie Player. Even at startup I get no sound of anything and I also tried playing a game and I turned the sound on but still nothing.

---

### Post by kansasnoob on 2008-08-30
I always start by installing gnome-alsamixer which is in synaptic or from terminal:

```
sudo apt-get install gnome-alsamixer
```

It then shows up in Sound and Video. Here's mine:

[ATTACH]83427[/ATTACH]

[ATTACH]83428[/ATTACH]

Lots of toggles!

---

### Post by kansasnoob on 2008-08-30
Oh, it may not be necessary but I'd also add ubuntu-restricted-extras which is also in synaptic, or:

```
sudo apt-get install ubuntu-restricted-extras
```

---

