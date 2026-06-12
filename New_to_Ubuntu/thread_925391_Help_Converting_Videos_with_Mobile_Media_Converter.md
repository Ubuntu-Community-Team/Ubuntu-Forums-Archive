---
title: "Help Converting Videos with Mobile Media Converter"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Dah_joKA on 2008-09-20
Hi there, I just recently switched to Ubuntu from Windows and I love it, I love the customization, the cube, everything, but I have ONE problem.

I have a blackberry curve and I would like to convert videos from my computer and put it onto my Blackberry, I've tried mobile media converter in every single way shape and form for over 3 days straight and I can't seem the get the video the way I want it.

I can get everything else fine, the audio, the format and such, BUT I want to know is there a way that I can convert my video to 320 x 240? Everytime I use it it converts my videos to 352 x 288 or something close to that nature.

ANY help is appreciated, thanks in advance

---

### Post by SuperSonic4 on 2008-09-20
Have you tried avidemux instead? ```
sudo apt-get install adivemux
``` although it is in repos if you prefer synaptic.

I guess you should look for a custom size option

---

### Post by Dah_joKA on 2008-09-20
> **SuperSonic4 said:**
> Have you tried avidemux instead? ```
sudo apt-get install adivemux
``` although it is in repos if you prefer synaptic.

I guess you should look for a custom size option

I didn't even know that there was another converter for Ubuntu, I tried running the code in the terminal but it said the package couldn't be found?

help! :lolflag:

---

### Post by SuperSonic4 on 2008-09-20
Oops I made a typo, try ```
sudo apt-get install avidemux
```

---

### Post by c-shadow on 2008-09-20
> **Dah_joKA said:**
> I didn't even know that there was another converter for Ubuntu, I tried running the code in the terminal but it said the package couldn't be found?

help! :lolflag:

Because it's avidemux :-)
SuperSonic4 got a bit of a typo here...

---

### Post by Mornedhel on 2008-09-20
Typo.

It's "avidemux". [Edit : c-shadow beat me to it]

You may also want to check out mencoder (command line tool).

---

### Post by sneeks on 2008-09-20
yup avidemux should do it for you or winff,these two always get me out of a pickle..

---

### Post by Dah_joKA on 2008-09-20
WHOA! thanks for all the help guys, i really appreciate it, I've managed to install avidemux onto my computer but I still need help because I fail at life =[.

I have NO clue how to use avidemux, I've been toying with it for over 30 mins and I still can't seem to get the video the way I want it. May I ask for extra help please?


I'm trying to get a video with the dimensions 320 x 240 in MP4 format, 15 fps, 16000 Hz, MPEG-4 ACC Audio.

Can somebody pleeease help me out on how to configure it? Again thanks SO much in advance, sorry to be a nuisance

---

### Post by netcyrax on 2008-09-22
Just use Mobile Media Converter, select the "More" button, and in the Video Size enter "320x240". This will pass the appropriate parameter to the ffmpeg backend resulting in your desired video! :) hope i helped..

---

### Post by tcpankon on 2008-09-22
Check this other post for another idea:

[http://ubuntuforums.org/showthread.php?t=819346&highlight=blackberry+video]("http://ubuntuforums.org/showthread.php?t=819346&highlight=blackberry+video")

My post towards the end has a script for changing a directory full of .avi files to mp4 files to be played on the blackberry.  you may have to tweak the resolution depending on your phone, but it should work.  The only thing it relies on is mencoder.

This requires the CLI, but its pretty simple to create a script, make it executable, copy the script to the appropriate directory and run it.  Let it go over night and come back to have all of your videos transcoded to be compatible with your phone.

---

