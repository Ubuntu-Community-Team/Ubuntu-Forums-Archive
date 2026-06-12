---
title: "how to convert DVD to mpeg file?"
date: 2012-10-26
forum: New to Ubuntu
---

### Post by bakelitedoorbell on 2012-10-26
Hi

I have a couple DVDs that I want to watch on a netbook that has no optical drive.  So I figured that I might be able to rip the disks and turn them into movie files (mpeg, avi, ogv, etc) copy them to the netbook and then watch with a movie player.

I tried using a couple of the programs in the software center for ripping DVDs (like dvd::rip).  What I want to do seems like a simple task but these are complex programs.  I was able to copy the tracks into dvdrip but coudn't figure out how to export them into mpeg files.

Can someone point me to a guide for doing this?

Thanks

---

### Post by ajgreeny on 2012-10-26
If you are prepared to use the terminal it may be possible to directly convert the .vob files from the DVD with either **ffmpeg** or **avconv**, depending on which version of ubuntu you are using.
```
ffmpeg -i file.vob -vcodec mpeg2video -sameq -ab 128k outfile.mpg
```
or
```
avconv -i file.vob -vcodec mpeg2video -q# -ab 128k outfile.mpg  
```
    -q# is vbr quality - 1(high) - 9(low)

You will, of course, need all the codecs necessary for decoding and encoding the files, but that would also be the case if you used any of the GUI applications available, none of which I have any experience of.

---

### Post by oldos2er on 2012-10-26
> **bakelitedoorbell said:**
> Can someone point me to a guide for doing this?
Thanks

Once upon a time in Ubuntu you could right-click on the DVD icon and choose 'Copy.' I've never used Unity, but if this is no longer the case, you can use the program K3b to copy the DVD to an *.iso file.

---

### Post by bakelitedoorbell on 2012-10-26
> **ajgreeny said:**
> If you are prepared to use the terminal it may be possible to directly convert the .vob files from the DVD with either **ffmpeg** or **avconv**, depending on which version of ubuntu you are using.
```
ffmpeg -i file.vob -vcodec mpeg2video -sameq -ab 128k outfile.mpg
```
or
```
avconv -i file.vob -vcodec mpeg2video -q# -ab 128k outfile.mpg  
```
    -q# is vbr quality - 1(high) - 9(low)

You will, of course, need all the codecs necessary for decoding and encoding the files, but that would also be the case if you used any of the GUI applications available, none of which I have any experience of.

Thanks, it would be ffmpeg on my system.  I assume the -ab sets the audio quality?  I know there are 4 videos on one dvd, but when I look at the files there are 7 large vob files, so I'm not sure which is which.  I was hoping the GUI program would sort that out for me.

Maybe there isn't a quick and easy way to do this, and I should just watch it on a TV.  Watching on the netbook would just be more convenient.

---

### Post by sandyd on 2012-10-26
Have you tried Handbrake?

You can get the deb from [http://www.liberiangeek.net/2012/10/install-handbrake-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/10/install-handbrake-in-ubuntu-12-10-quantal-quetzal/)

---

### Post by squakie on 2012-10-27
+1 on Handbrake.  I've used that to convert DVD movies to mpeg so I could watch them on my tablet.  I assume you already installed things like libdvdread4 (or whatever the version is now), and also installed via the script file it provides tha ability to watch copy-protected DVD's via libdvdcss (?).  If you still need to install those, be sure you are aware of your country's copyright laws before you install and use them - they are not legal in a lot of places so you would be using them at your risk.

EDIT:  It's been a little while since I did my last, but it sticks in my mind there are 2 options I use - the option for mpeg (I think it says something like ipod compatible or some such thing) and large file size.

---

### Post by bakelitedoorbell on 2012-10-27
**Handbrake** worked for me, thanks.  I found this article helpful also: [http://lifehacker.com/5773000/how-to-rip-dvds-with-handbrake](http://lifehacker.com/5773000/how-to-rip-dvds-with-handbrake)

---

### Post by andrew.46 on 2012-12-10
You can do it 'by hand' if you have a little time and are keen to learn. My own method here:


FFmpeg and 'Fist of Fury'
[http://www.andrews-corner.org/fist.html](http://www.andrews-corner.org/fist.html)

It is more fun than it looks :)

---

