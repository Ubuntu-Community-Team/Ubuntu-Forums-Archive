---
title: "TIP: wma audio preview in nautilus"
date: 2006-10-31
forum: Outdated Tutorials &amp; Tips
---

### Post by LinAsH on 2006-10-31
Hi,

I found a useful trick to get a 'preview' of wma audio files under nautilus, using ffplay. (same as for mp3 and ogg when ogg123 and mpeg123 installed)

1) FFmpeg install:
```
sudo apt-get install ffmpeg
```2) add the following bash script in /usr/local/bin/play: (sudo gedit /usr/local/bin/play)
```
#! /bin/sh
ffplay -nodisp -
```3) make it runnable:
```
sudo chmod +x /usr/local/bin/play
```4) enjoy wma preview in nautilus!

---

### Post by dommyOZ on 2007-04-30
> **LinAsH said:**
> Hi,

I found a useful trick to get a 'preview' of wma audio files under nautilus, using ffplay. (same as for mp3 and ogg when ogg123 and mpeg123 installed)

1) FFmpeg install:
```
sudo apt-get install ffmpeg
```2) add the following bash script in /usr/local/bin/play: (sudo gedit /usr/local/bin/play)
```
#! /bin/sh
ffplay -nodisp -
```3) make it runnable:
```
sudo chmod +x /usr/local/bin/play
```4) enjoy wma preview in nautilus!

I tried this on Feisty 7.04 but it wouldn't work. If I executed the command and gave it a file name then I got a file read error ( so ffplay -nodisp somefile.wma  --> read error ) if I changed it to mplayer instead then it worked like a charm except that any wav file now no longer plays in preview :(  Win some loose some. Out of curiosity how did you find this method ??

---

### Post by LinAsH on 2007-04-30
Hi dommyOZ

The trick still working on Feisty for me, though some particular files failed. (or maybe you've got a lot of this kind of files)

How I find this method? I ran nautilus in a terminal in a non-gnome environment (xfce), I saw that nautilus was trying to run a command named 'play' to preview audio files with no known 'previewer' . Then I noticed that nautilus provides a raw stream of the previewed files instead of the path to it. Same as in "cat somefile.wma | ffplay -nodisp -".

Just thought that I use the medibuntu version of ffmpeg, your problem may come from the regular version.
To install medibuntu pachages: [http://medibuntu.sos-sts.com/repository.php](http://medibuntu.sos-sts.com/repository.php)

---

### Post by fragmented_user on 2007-05-08
also, for flac files use flac123

---

