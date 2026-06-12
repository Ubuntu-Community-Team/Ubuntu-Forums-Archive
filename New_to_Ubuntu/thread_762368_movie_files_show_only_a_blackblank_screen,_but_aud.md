---
title: "movie files show only a black/blank screen, but audio is okay"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by hanzj on 2008-04-22
I've tried playing movie (m4v) files with mplayer, mplayer-gui, and totem (gstreamer). 

The sound comes out fine, but all i see is a black/blank screen.

Help.

i'm on xubuntu 8.04 beta.

---

### Post by subzero316 on 2008-04-22
Try with VLC player.:KS

---

### Post by hanzj on 2008-04-22
could you tell me why my setup currently doesn't work? I'd like to figure that out first, before i install more programs?

---

### Post by hanzj on 2008-04-22
anyway, i've installed VLC, and it's the same problem.

---

### Post by subzero316 on 2008-04-22
Does this happen with other video formats?

---

### Post by hanzj on 2008-04-22
yes, it happens with avi and mov formats, too.

---

### Post by russo.mic on 2008-04-22
Are you running Compiz?  If so, do you have the Video Plugin enabled?

Russo

---

### Post by subzero316 on 2008-04-22
I guess the problem is not with the player or codecs cause VLC has everything in built. You have the new beta ubuntu maybe some problem with that..try reinstalling the related libraries

---

### Post by nicedude on 2008-04-22
Hans you need to add the Medibuntu restricted repositories so you can download codecs that for legal reasons they can't include in Ubuntu. Copyright reasons I believe. hold on a sec and Ill find the guide here and post the link to it here

---

### Post by nicedude on 2008-04-22
uh maybe not sorry just saw you are using hardy so maybe go into your synaptic package manager and search to see if you have w32codecs

---

### Post by Saint Angeles on 2008-04-22
+1 for medibuntu and ubuntu-restricted extras!!

hurrah!

---

### Post by nicedude on 2008-04-22
If you haven't added the medibuntu repositories to your sources list yet then you should. below are the commands

Just copy the 2 command lines 1 at a time when you copy each one paste in terminal window and execute first the sources then the key.

Ubuntu 8.04 "Hardy Heron":

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

Then, add the GPG Key:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add - && sudo apt-get update


now you will have more multimedia playback related and other software in your synaptic

---

### Post by Ace_Of_Days on 2008-08-22
> **hanzj said:**
> anyway, i've installed VLC, and it's the same problem.

go into vlc in program and click quick settings and video then click on ¨set video mode to openGl¨
that workt for me i gott the same problem before:d

---

### Post by specialk1st on 2010-05-28
> **Ace_Of_Days said:**
> go into vlc in program and click quick settings and video then click on ¨set video mode to openGl¨
that workt for me i gott the same problem before:d

THANK YOU SO MUCH FOR THIS TIP!!!!  I've tried all the other method listed on here and on Google, but this is the one that actually works!  :P

---

### Post by hanzj on 2010-05-28
I've marked this thread as solved, even though I  recall my reaching a solution on Xubuntu 8.XX  (I'm now on Ubuntu 10.04).

---

