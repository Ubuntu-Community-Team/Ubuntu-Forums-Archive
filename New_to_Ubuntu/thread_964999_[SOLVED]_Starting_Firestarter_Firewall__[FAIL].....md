---
title: "[SOLVED] Starting Firestarter Firewall  [FAIL]............help!!!"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Teabicky on 2008-10-31
I keep getting this message every time I boot up my computer "Starting Firestarter Firewall  [FAIL]".  This means that I have to manually start firestarter every time I turn my computer on.  I understand that it is just a front end for iptables but does it have to start on start up for my configuration to work? 

:guitar:

---

### Post by Nepherte on 2008-10-31
No, you don't need a running firestarter. In general, you don't need to change the firewall configuration either.

The reason why it is giving that error is because you might run it at boot before gdm is loaded. Since it is a graphical application, it has to come after gdm (system > preferences > sessions). It will also ask you for your password as it needs sudo priviliges to run.

But again, you don't need firestarter running at all.

---

### Post by Zzl1xndd on 2008-10-31
Firestarter normally requires root access to run so that is likely the issue during start up. As far as I know the only way to correct it is to give yourself full root access but I wouldn't recomend that. 

You are correct that Firestarter is just a front end for IPtables and IPtables retains the settings that you configured with Firestarter even if Firestater is not running. If you worried about it though head on over to GRC.com and check out Shields up it should give you the same results regardless if firestarter is running or not.


[www.grc.com](www.grc.com)

---

### Post by Teabicky on 2008-10-31
Thanks:).  I have just tried putting the command "sudo firestarter --start-hidden" in System> Sessions> Startup Programs and nothing seemed to happen so i tried "gksudo firestarter" and that works (although it asks me for my password on startup).  

I think I'll probably trust you guys and just leave it off though seeing as every time I inquire about needing to have firestarter running I get the same answers.  I'll just stop being so paranoid!!!!!

:guitar:

---

### Post by bodhi.zazen on 2008-10-31
Ubuntu switched to UFW as of 8.04. UFW is a command line application to configure iptables and comes with a gui, gufw.

[uhelp]community/Uncomplicated_Firewall_ufw[/uhelp]

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

GUI : [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html) (although gufw is in the intrepid repos).

---

### Post by noobie_1 on 2008-11-20
thanks for the heads-up on this;i'm having the same issue,but will just get rid of firestarter.

---

### Post by CLomax on 2008-11-20
There's also the graphical version of UFW... GUFW!

It isn't in Add/Remove but it is in .deb form in the tubes somewhere.

I find it far superior to Firestarter.

---

### Post by dhbmarcos on 2010-02-19
For disable Firestarter Firewall in boot, rename the file relative to Firestarter in **"/etc/rcS.d**" with "**K**" before.

For example: In my system, the file is "**/etc/rcS.d/S65firestarter**". Rename to "**/etc/rcS.d/[SIZE=2]_K_[/SIZE]S65firestarter**".

*Note: You need a root previlegies.*

---

### Post by ade4krist on 2012-11-08
> **dhbmarcos said:**
> For disable Firestarter Firewall in boot, rename the file relative to Firestarter in **"/etc/rcS.d**" with "**K**" before.

For example: In my system, the file is "**/etc/rcS.d/S65firestarter**". Rename to "**/etc/rcS.d/[SIZE=2]_K_[/SIZE]S65firestarter**".

*Note: You need a root previlegies.*


It works for me. Thanks

---

### Post by wildmanne39 on 2012-11-08
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

