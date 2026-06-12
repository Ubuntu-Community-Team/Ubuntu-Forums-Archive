---
title: "HOW TO: Convert any audio to an mp3"
date: 2006-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by aarbear26 on 2006-07-18
I have spent weeks trying to figure out how to convert my .rm and .ram files to mp3.  I finally found it by searching for something to encode an mp3 from a wma.  This works for wma, RealMedia or any other format that your mplayer is set up to play.

Also so everyone knows I did not come up with this on my own, I found it [here]("http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Convert_WMA_to_MP3") and had to make some changes to make it compatible with enhancements in mplayer.

1. open gedit to a blank document (Applications >Accessories>Text Editor)

2. copy this text into it, then save it as wmamp3 (or whatever format you use it for)

#!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.ram; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.ram; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for i in *.ram ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names
for i in *.ram; do mv "$i" "`basename "$i" .ram`.mp3"; done

rm audiodump.wav

3. For wma use this, or for other formats anywhere you see .wma change it to .rm or .ogg or.mov, use it for anything mplayer can play

4. Open a terminal (Applications>Accessories>Terminal) and make sure you are in the directory the file was saved in

5. make it executable with:
            chmod +x wmamp3 (or for other to use it too use a+x for +x)

6. and copy it to your script folder with:
          sudo cp wmamp3 /usr/bin/
(you'll want to rename other iterations things like rmmp3, movmp3 and change the line accordingly)

7. Then use it by going to the folder in terminal and typing wmamp3

WARNING!! This will change ALL your files in that folder of the type specified to an mp3 and remove the old files.  Create backups of your files first and test it on your system to make sure you have everything configured properly!!

Notes:
I'm not sure I like the quality of the files made by lame, i may change later to toolame or if anyone knows of a better mp3 encoder I'm all ears for better options.  Also, you can use this to convert to ogg, wma or anything you have an encoder for. I hope this helps anyone looking for a quick solution to convert large amounts of files.

On my system it took about 15 seconds to convert each rm file to mp3.

Good luck!

---

### Post by evaristegalois on 2006-07-23
The perl audio converter pac will do the job as well, although it is rather a grief to install

--evaristegalois

---

### Post by evaristegalois on 2006-07-23
FANTASTIC! I spent hours trying to re-install the perl audio converter pac which once upon a time I had working but couldn't get re-installed, and now you have given such an elegant solution for the problem. Thanks!

--evaristegalois

---

### Post by standards on 2006-09-03
great how-to. using it right now and it's working fantastically. 

however, i think there might be a typo under point 3. the script you've written is NOT for wma files, it's for .ram (real audio? i have no idea) files. easy enough for most to figure out, but still.

---

### Post by finferflu on 2006-09-10
Thanks a lot for this very useful script, I really appreciate your how-to :D

---

### Post by Adam Golebiewski on 2006-10-10
it's just GREAT! :)

Adam

---

### Post by Maximinus on 2006-11-03
Brilliant - just used it to convert a bunch of FLACs created by Sound Juicer from an audio CD :D

---

### Post by jstrubberg on 2006-12-29
I must be missing something.  Evertime I execute the script I get the following:



-aofile is deprecated. Use -ao pcm:file=<filename> instead.
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2500  @ 2.00GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.

---

### Post by tetrafuran on 2008-08-20
I got something similar but then I fixed the parts that say ".ram" into ".rm" in the script. If you are converting wma files then your .ram should say .wma.

---

### Post by newbuntuxx on 2011-06-11
Can't thank you enough aarbear26. Simple, elegant and it works, five years after. :)

I'll just put it in code tags and remind the users to first install mplayer and lame, if you don't already have them. To do so, simply run the following commands from the terminal/command line:

To install MPlayer:
```
sudo apt-get install mplayer
```

To install LAME:
```
sudo apt-get install lame
```

Here is the script in code tags:

```


#!/bin/bash

current_directory=$( pwd )

#remove spaces
for i in *.ram; do mv "$i" `echo $i | tr ' ' '_'`; done

#remove uppercase
for i in *.ram; do mv "$i" `echo $i | tr '[A-Z]' '[a-z]'`; done

#Rip with Mplayer / encode with LAME
for i in *.ram ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader $i && lame -m s audiodump.wav -o $i; done

#convert file names
for i in *.ram; do mv "$i" "`basename "$i" .ram`.mp3"; done

rm audiodump.wav


```

If you want to convert from "rm" to mp3, simply change all the instances of "ram" to "rm".

I am running Ubuntu 10.10 and this worked perfectly.

---

