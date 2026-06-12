---
title: "Asus EEE HELP!"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by kressha on 2008-10-11
I'm using an ASUS EEE Pc Running on Xubuntu.
I've just recently updated my laptop.

When the updates have finished, my internet connection does NOT work anymore, and it does not detect any wireless.
Nor does it detect any connections to the internet. 
whats the problem? 
I've tried trouble shooting but it does not work.

also, when I turned on my laptop again, it says that ubuntu will run on low graphics so now my screen resolution is very stretched
it says that it cannot dectect the x server?????

Im really new at this, and im really confused. Thanks! 



I've been looking around for a solution but to no avail.
Can someone please help?

---

### Post by victorbrca on 2008-10-11
Did you use the normal install or the eeexubuntu?

As far as the eeePC goes, I think most people running Linux will not do any updates to save space and HD life. 


Vic.

---

### Post by tgalati4 on 2008-10-11
As a general rule, don't update the kernel or xorg (video) unless you know what you are doing.  These two updates tend to break things.  Updating applications and libraries don't normally render a machine unbootable.

So it looks like your wireless and graphics drivers no longer work with your update.  Post the output of:

>lspci -vv

---

### Post by t0p on 2008-10-11
+1 for not updating an eeepc.  The SSD would fill up in no time!

I'm running ubuntu 8.04.1 on my eeepc, and the tweaks/scripts [here]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu%20eee%20riceeey") ensure everything works fine, including webcam and wireless.

---

### Post by richg on 2008-10-11
If no useable suggestions here, go to the Asus EEC forums.

[http://forum.eeeuser.com/](http://forum.eeeuser.com/)

Rich

---

### Post by cozmicharlie on 2008-10-11
You need to install the madwifi drivers.  This information should help [http://wiki.eeeuser.com/ubuntu:eeexubuntu:upgrading_to_8.04](http://wiki.eeeuser.com/ubuntu:eeexubuntu:upgrading_to_8.04)

If you have any problems understanding what to do post to the eeepc.com forums or post back here and we can help.

---

