---
title: "HOW-TO encode wma into ogg"
date: 2005-11-20
forum: Outdated Tutorials &amp; Tips
---

### Post by jrincon87 on 2005-11-20
This is a simple script which will allow you to convert all the files in a folder into ogg format.

First create a file called wma2ogg with your favorite text editor:

Code:
> gedit wma2ogg.sh

Copy the following script:
> #!/bin/bash
 
# Remove spaces
for i in *.wma; do mv "$i" `echo $i | tr ' ' '_'`; done
 
# Remove uppercase
for i in *.[Ww][Mm][Aa]; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done
 
# Rip with Mplayer / encode with Oggenc
for i in *.wma ; do
mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && oggenc -q 6 audiodump.wav -o $i; 
done
 
# Convert file names
for i in *.wma; do mv "$i" "`basename "$i" .wma`.ogg"; done
 
rm audiodump.wav


Save and close.

Make the script executable:

Code:
> chmod +x wma2ogg.sh

Copy the file into /usr/bin

Code:
> sudo cp wma2ogg.sh /usr/bin

Now you can change to the folder in which you have the wma files and execute the program.

Code:
> sudo wma2ogg.sh

This will automatically encode ALL the wma files in the folder into Ogg, quality = 6 (around 160kbps and 210kbps), and OVERWRITE them, which means you don't have to manually erase the original files after you have converted them (if not desired, make a copy of the original wma files).

Dependencies:
- mplayer
- vorbis-tools

That's all. Start converting files!

---

### Post by WiLLiE on 2005-12-02
ehhmm.. noway. They'll sound even worse.

---

### Post by db0 on 2005-12-02
You will be able to play them natively on Linux though. And WMA is a crappy format anyway

---

### Post by SlugO on 2005-12-02
I think encoding from an already encoded (lossy) file format is always a bad idea. Sound quality just gets worse.

Although I've done it myself since I couldn't get wma's to work with amaroK... Damn the fools who encode to wma :rolleyes:

---

### Post by DaMasta on 2005-12-06
As I expected, this does not work for drm'd wma's. :(

---

### Post by db0 on 2006-02-18
Just used this for some new files. Worked flawlessly.
Thanks

---

### Post by K.Mandla on 2006-05-19
Excellent! It works great under Dapper and I'm finally free of those awful wma files. Thanks for this! :mrgreen:

---

### Post by UbuWu on 2006-05-19
For those that don't love the console: there is a program called soundconverter in the repositories that does this job perfectly. ([http://soundconverter.berlios.de/](http://soundconverter.berlios.de/))

---

