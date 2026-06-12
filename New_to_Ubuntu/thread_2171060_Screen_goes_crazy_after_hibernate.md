---
title: "Screen goes crazy after hibernate"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by Jonathan_Yu on 2013-08-29
Hello everyone, I am completely new to linux.  Just started to do some research this week about linux and how to install it.  I installed Lubuntu 13.04 on to my Acer Aspire One D270 netbook and got everything running well.  I put my netbook into hibernate and when I turn it back on the screen goes crazy with these crazy stripes of different colors throughout the whole screen.  I'm not exactly sure how to explain this but it is unusable unless I power it down then back up.  Could you guys help me out here and explain to me what's going on because I use hibernate all the time and really need it working.  And on a side note I cannot adjust my brightness using my FN keys only terminal.  Could someone help me with that too.  Thanks for all the help.

---

### Post by Dennis N on 2013-08-29
Hibernate is disabled by default in 12.04 and later releases. To enable, see:

[http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation)

---

### Post by Dennis N on 2013-08-29
This has an explanation as to why it's disabled:

[http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/](http://www.howtogeek.com/113923/how-to-re-enable-hibernate-in-ubuntu-12.04/)

---

### Post by Jonathan_Yu on 2013-08-29
> **Dennis N said:**
> Hibernate is disabled by default in 12.04 and later releases. To enable, see:

[http://askubuntu.com/questions/94754/how-to-enable-hibernation](http://askubuntu.com/questions/94754/how-to-enable-hibernation)

My hibernation seems to be enabled out of the box because it appears in my power menu and when I click it, my netbook seems to go into hibernate.  The problem is when I turn it back on it looks like the picture in the link.

[https://docs.google.com/file/d/0Bwor5wwIA13hOXY4eGVDSVpja0E/edit?usp=sharing](https://docs.google.com/file/d/0Bwor5wwIA13hOXY4eGVDSVpja0E/edit?usp=sharing)

---

### Post by skitter on 2013-08-29
I have a similar problem on my 12.04 system when it comes out of suspend. Every tenth time or so, the screen has weird video corruption- half drawn windows and blank spots. My gut feeling is it's related to the Nvidia video drivers I'm using. I tried using 2d mode for a week and never ran into the problem.  If you want to see if 2d makes a difference for you, just click the 'holding hands circle' thingy at the logon on prompt and choose 2d instead of 3d.

---

### Post by Jonathan_Yu on 2013-08-30
> **skitter said:**
> I have a similar problem on my 12.04 system when it comes out of suspend. Every tenth time or so, the screen has weird video corruption- half drawn windows and blank spots. My gut feeling is it's related to the Nvidia video drivers I'm using. I tried using 2d mode for a week and never ran into the problem.  If you want to see if 2d makes a difference for you, just click the 'holding hands circle' thingy at the logon on prompt and choose 2d instead of 3d.

I can't seem to find the 2d mode. I actually think lubuntu doesn't have a 2d mode because thats what it uses right out of the box. I could be wrong though, not sure. Anyway that was no luck :( does anyone else have some other suggestions? I really want to enjoy linux but this is holding me back.

---

### Post by carl4926 on 2013-08-30
If you have this GPU, check
[https://wiki.archlinux.org/index.php/Intel_GMA3600](https://wiki.archlinux.org/index.php/Intel_GMA3600)
[http://forums.linuxmint.com/viewtopic.php?f=59&t=105091](http://forums.linuxmint.com/viewtopic.php?f=59&t=105091)

---

