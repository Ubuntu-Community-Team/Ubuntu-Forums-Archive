---
title: "Sound from webcam using Skype"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by I-Broke-It on 2008-11-09
I am using a VX1000 Microsoft web cam it has a build in mike that I used to use on my Microsoft machine. Now with Skype I cannot seem to get the mike to work. 

I have tried to install the following packages but I cannot get it right.
sn9c1xx-1.48
sn9c1xx-1.48.tar.tar
sn9c102.tar.bz2
sn9cxxx_2.13-gutsy-1ubuntu1_i386.deb

I have also tried to set the volume controls in the Speaker Icon at the top

When web cam not plug in I get this:
[INDENT]orr@orr-desktop:~$ ls /dev/audio*
/dev/audio
orr@orr-desktop:~$ ls /dev/video*
ls: cannot access /dev/video*: No such file or directory[/INDENT]
When I plug it in I get this:
[INDENT]orr@orr-desktop:~$ ls /dev/video*
/dev/video0
orr@orr-desktop:~$ ls /dev/audio*
/dev/audio  /dev/audio1[/INDENT]

Thanks in advance

---

### Post by I-Broke-It on 2008-11-09
It seems that I have you guys stumped or not providing the correct info. Please let me know which one.

Thanks.

---

### Post by I-Broke-It on 2008-11-09
I am running the Hardy release I am sure that it is just something stupid that I am missing as the only experience I have with Linux is installing it and now trying to get this working (Well I had to install it twice since I tried a force install and to many thing stop working):).

I see there is a deb for Feisty and Gusty there is not such an install for Hardy as these two installs say I need a dependency but if I look at synaptic the files are installed.

Thanks again

---

### Post by I-Broke-It on 2008-12-19
I have loaded Intrepid to see if it will solve my problem. now it does not even create a dev/video0 file. The sound works though. So now I switch from the video that worked to the sound that works.

I am trying some more things will keep you posted

---

