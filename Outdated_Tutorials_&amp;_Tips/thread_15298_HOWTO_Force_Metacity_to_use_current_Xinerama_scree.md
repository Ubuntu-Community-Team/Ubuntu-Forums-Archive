---
title: "HOWTO Force Metacity to use current Xinerama screen"
date: 2005-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by evangelion on 2005-02-13
Using Gnome with Metacity and Xinerama (or Twinview) can be a pain, especially if you're using tv-out and your second screen is a television.  Windows seem to randomly be placed on whichever screen Metacity thinks is least crowded at the time.   This leads to windows popping up on your tv or second monitor when the second monitor may not even be turned on!

To remedy this, I've found a patch after some heavy googling,  I'm posting it here for posterity and to help others who may be annoyed with this problem.

If you're unsure about how to patch and/or build something yourself it's very simple

```

##Before you start you'll need the packages
## **libxml-parser-perl**, **libgtk-2.0-dev**,**libgconf2-dev**
#and their respective dependencies (which will be handled for you by
#the magic of apt-get or synaptic

# Grab the sources (latest as of 2/13/05, subject to change)
**wget http://ftp.gnome.org/pub/gnome/sources/metacity/2.8/metacity-2.8.8.tar.bz2** 

#Unpack them (x is for extract, v is for verbose, j is because it's a bzip file, 
#p preserves permissions and f points it to the file, 
#in case you were wondering)

**tar xvjpf metacity-2.8.8.tar.bz2**  

#Change to the source's directory

**cd metacity-2.8.8**

#The actual patch procedure, it's just a plain text patch compressed with bzip2
#hence bzcat to display it,  if you ever have an uncompressed .diff or .patch file 
#you can just use "cat"

**bzcat /path/to/metacity-2.6.3-xinerama-place.patch | patch -p1**

#It will display
[b]
patching file src/place.c
Hunk #2 succeeded at 768 (offset 9 lines).
[/b]

```
now just ./configure --prefix=/usr && make && sudo make install and you'll be good to go.  Now windows should always be placed in the active screen.

Enjoy

---

### Post by terasurfer on 2005-03-01
Thank you so very much.  I was gritting my teeth and dealing with this for a while, and I was about to switch back to KDE.  I'm glad i searched for a solution one more time before switching. :D

---

### Post by Ettorix on 2005-03-18
Hi

Thanks a lot for this howto, but i have tried this and have a problem :
i am in ubuntu warty but i have upgraded to xorg from hoary, have a nvidia card.
When  i restarted X after have followed the instructions, gnome began to load but blocked after the message in the splashscreen "loading metacity" or something similar. So gnome doesn't load completely. currently i have metacity 2.8.6
perhaps metacity 2.8.8 doesn't work in warty ?

---

### Post by cybersaga on 2006-05-05
Confirming that this works with Metacity 2.15.2

---

### Post by TLE on 2006-11-19
Hey
I don't mean to be hogging the momentum here. But I have a HOWTO with the same purpose with readymade .debs. Which is updated for Edgy also. Maybe we can work together in the future?

My HOWTO is [here]("http://ubuntuforums.org/showthread.php?t=242502")

Regards TLE

---

