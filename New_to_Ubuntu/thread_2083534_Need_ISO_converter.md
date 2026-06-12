---
title: "Need ISO converter"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by vegas89 on 2012-11-12
I am using Ubuntu 12.4 Can someone suggest a good simple app to convert downloaded movies in an .flv format to an iso image format so I could burn to dvd  to watch on tv.    [-o<

---

### Post by deadflowr on 2012-11-12
Here and there I've used WinFF.
You can find it in the repos.(The Software Center)

---

### Post by vegas89 on 2012-11-12
I tried to install that but this is what comes up as error reason   The following packages have unmet dependencies:

winff: Depends: libatk1.0-0 (>= 1.12.4) but 2.4.0-0ubuntu1 is to be installed
       Depends: libc6 (>= 2.2.5) but 2.15-0ubuntu10.3 is to be installed
       Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.26.1-1 is to be installed
       Depends: libglib2.0-0 (>= 2.12.0) but 2.32.3-0ubuntu1 is to be installed
       Depends: libgtk2.0-0 (>= 2.24.0) but 2.24.10-0ubuntu6 is to be installed
       Depends: libpango1.0-0 (>= 1.14.0) but 1.30.0-0ubuntu3.1 is to be installed
 What should I do  :confused:

---

### Post by kostkon on 2012-11-12
Try with [DeVeDe]("https://apps.ubuntu.com/cat/applications/devede/"). It will convert your video files tou MPEG2 and then create an iso file out of them that is playable on DVD players.

Hopefully, it will not have a proble converting your flv files.

---

### Post by andrew.46 on 2012-11-13
It can be done by hand with a few commandline tools if you are interested in going that route. First convert your input file:

```

ffmpeg -i input.flv \
       -target pal-dvd -aspect 16:9 -ac 2 \
       output.mpg

```

Here you would need to alter the name of the input file and the *-target* option if you use ntsc rather than pal. Then create the dvd:

```

dvdauthor -t -o dvd --video=pal -f output.mpg
dvdauthor -T -o dvd

```

and finally create the iso and burn to dvd:

```

mkisofs -dvd-video -o output.iso dvd/
growisofs -dvd-compat -Z /dev/sr0=output.iso

```

Here you would need to alter the name of the iso file to suit your needs and possibly alter the path to your dvd device for growisofs. It is all not as painful as it sounds and allows great scope for alteration with each and every commandline.

---

### Post by XBMC old School on 2012-11-13
cheap and sweet. never burn again. And Hot digity, and in bluray until the format dies in 2013.

[XBMC]("http://xbmc.org/") + [Raspberry Pi]("http://www.raspberrypi.org/") = [Raspbmc]("http://www.raspbmc.com/")

---

### Post by vegas89 on 2012-11-13
Thanks for the suggestions, but I really don't understand what to do with the reply from xbmc old school and as for andrew .46 I will keep these code script commands for future use. Kostkon I tried the devede download but as before as with the other one It had an error that read like this   The following packages have unmet dependencies:

devede: Depends: ffmpeg (>= 4:0.7.2) but 4:0.8.4-0ubuntu0.12.04.1 is to be installed
What part of this line should I try to use for this install or is there another route I should try   :confused:

---

### Post by newb85 on 2012-11-13
I don't know a lot about dependency handling, but it looks like your system isn't comparing correctly.  In each of the dependency errors you've listed, what you have installed (or about to install) is in fact >= the requirement, but for some reason, doesn't seem to satisfy.

---

### Post by vegas89 on 2012-11-13
Ok all is well, Got home from work and fired up the OS and noticed there were five updates to install something about the lib-codes, did the install then tried the devede install and the program installed and runs great. I guess the little bean elfs fixed this thing while I was away.  *I will have another issue to deal with soon , I am sure of it. Thanks for ya'lls help.   **):P*

---

