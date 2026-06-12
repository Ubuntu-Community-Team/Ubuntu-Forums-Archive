---
title: "Virtualbox crashed your computer?  Problem solved!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by revun096 on 2008-07-04
Hey everybody!

I'm a complete noob to ubuntu, but I have managed to solve this problem succesfully!  For those who've dealt with the agonizing stress of re-installing ubuntu due to the virtualbox drivers, here is the solution!

Download the Virtualbox debian file from: 

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

It is for i386 or amd64.

Once you have that downloaded, it may ask you to install some library before it will install.  That's fine (as long as it's not the vbox drivers!)  Follow the instructions and install it.

No, you're probably wondering, how do I start Virtualbox?  That's easy!  Just go to the applications menu and right click.  Select 'Edit Menus.'  Then go to system tools and you will see virtualbox... checked?  

I don't understand it either.  Anyway, just select 'New Item' and fill in this information.  Case-sensative!

Name: VirtualBox
Command:  VirtualBox

You should be able to launch it now.

Now for the last problem.  When you try to run your virtual os, it will tell you you do not have access to the drivers upon startup.  Easy enough!  Go to System > Administration > Users and Groups and then unlock your user and add yourself (and root) to the vboxusers group.

Restart and it will work!

--revun096

---

### Post by ibuclaw on 2008-07-04
Tell me something I don't know :lolflag:

But seriously, this is mentioned quite often in this forum.
And the existence of the closed-source version isn't really a fact unheard of.

Thanks for the reminder, but no thanks (I prefer the speed of WINE 1.1.0 much better than a slow fully blown virtual OS).

[EDIT]
You also forgot to mention that you have to re-compile the vbox modules every time you upgrade your kernel.
Something like
```
/etc/init.d/vboxdrv install
```
I can't quite remember at this point in time.

Regards
Iain

---

