---
title: "I am so confused"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by rabidrhino2 on 2008-06-12
Hello guys i am a new linux user and i just downloaded ubuntu from wubi and everything went ok but now after boot up i get a black screen and it won't take me to the login screen.(I am using a Inspiron 5100 that is 4 years old)
This is what the black screen says-----------------
-----------------------------------------------------------

BusyBox v1.1.3 (Debian 1:1.1.3-5 ubuntu 12) Built in shell (ash)
enter 'help' for a list of built in commands

------------------------------------------------------------
Thanks for the help guys

---

### Post by rabidrhino2 on 2008-06-12
Hello guys i am a new linux user and i just downloaded ubuntu from wubi and everything went ok but now after boot up i get a black screen and it won't take me to the login screen.(I am using a Inspiron 5100 that is 4 years old)
This is what the black screen says-----------------
-----------------------------------------------------------

BusyBox v1.1.3 (Debian 1:1.1.3-5 ubuntu 12) Built in shell (ash)
enter 'help' for a list of built in commands

------------------------------------------------------------
Thanks for the help guys

---

### Post by superprash2003 on 2008-06-12
how much RAM have you alloted for ubuntu in wubi?

---

### Post by rabidrhino2 on 2008-06-12
my computer only has 512 but it didn't ask anything about that using wubi i just dedicated 10 GB of hard drive space towards it.

---

### Post by agamotto on 2008-06-12
If you have a prompt, try the following:  sudo dpkg-reconfigure xserver-xorg

That should get you into a CLI interface to reconfigure your video.  Good luck.  I have a Dell Inspiron 4100, and I had to do this after the initial install myself.

---

### Post by brigadoon on 2008-06-12
To rule out a graphics driver issue press the <ctrl> , <alt> and F1 keys at the same time. This shall kick you out of the graphic login screen to a terminal screen. If you see a login prompt then you may have a driver conflict of configuration problem.

The key combination to switch back to the graphic interface is <ctrl> , <alt> and F7.

Please list what type of graphics driver you have. Also, let me know what happens when you press the key combinations. I have a Nvidia GForce4 420 Go on my 5 year old laptop. I also hit a black screen at one point. I may be able to give you some ideas.

---

### Post by Xiong Chiamiov on 2008-06-12
This is a duplicate of [this thread]("http://ubuntuforums.org/showthread.php?t=827492"), for anyone arriving here by search.

---

### Post by Joeb454 on 2008-06-12
And that is what the report button is for :)

And to OP - please do not create duplicate threads :)

---

### Post by rabidrhino2 on 2008-06-12
well i could not get the first method to work at all but the second when i held down the three keys it said loading please wait but just sat there forever should i wait longer?

---

### Post by wolfen69 on 2008-06-12
just reply to your own thread by typing "bump". it will bring the thread to the top of the list. but wait a little while. in the meantime, you can search google.

---

### Post by rabidrhino2 on 2008-06-12
and my computer has integrated graphics i am pretty sure thats what it said on belarc advisor

---

### Post by Ripfox on 2008-06-12
> **agamotto said:**
> If you have a prompt, try the following:  sudo dpkg-reconfigure xserver-xorg

That should get you into a CLI interface to reconfigure your video.  Good luck.  I have a Dell Inspiron 4100, and I had to do this after the initial install myself.

This will not work at a busybox prompt I do not believe

---

### Post by Xiong Chiamiov on 2008-06-12
> **Joeb454 said:**
> And that is what the report button is for :)


Did right after posting.

---

### Post by Joeb454 on 2008-06-12
> **wolfen69 said:**
> just reply to your own thread by typing "bump". it will bring the thread to the top of the list. but wait a little while. in the meantime, you can search google.

Preferably no more than once every 24 hours

---

### Post by brigadoon on 2008-06-12
I just did a google search. The Dell Inspiron 5100 comes with a 16MB or 32MB ATI Mobility Radeon 7500 AGP graphics card. I also found info on a bug report located at...

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/132716)

This link may give you some direction. Wish I could be more helpful. Good luck.

---

### Post by superprash2003 on 2008-06-13
try giving 256mb of RAM to ubuntu in wubi

---

### Post by hyper_ch on 2008-06-13
you should use a descriptive thread title that reflects the content of your problem and not a generic "noob here" or "need help".

---

### Post by eriqjaffe on 2008-06-13
> **superprash2003 said:**
> try giving 256mb of RAM to ubuntu in wubiA Wubi install uses all of the RAM in the PC, since it's not running in a virtualized environment.  You **do** have to allocate hard drive space, however, that shouldn't have an effect on the video one way or another.

---

### Post by avtolle on 2008-06-13
[https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623](https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623) may help you out.

---

