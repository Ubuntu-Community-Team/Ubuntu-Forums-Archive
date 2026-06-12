---
title: "Ubuntu 8.04 installation problem?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by mypetduck on 2008-04-27
After a lengthy installation process, I rebooted my system. I got the start screen with Ubuntu, and the orange bar ran through all the way...then the screen went blank except for a blinking cursor in the upper-left center of the screen. Machine is a Toshiba Portege 7200CT, 320MB Ram, 6GB HD, Pentium III.

Any ideas what went wrong?

---

### Post by Crafty Kisses on 2008-04-27
> **mypetduck said:**
> After a lengthy installation process, I rebooted my system. I got the start screen with Ubuntu, and the orange bar ran through all the way...then the screen went blank except for a blinking cursor in the upper-left center of the screen. Machine is a Toshiba Portege 7200CT, 320MB Ram, 6GB HD, Pentium III.

Any ideas what went wrong?

You have really low RAM, you may want to look into Xubuntu, or try the alternate CD installer.

---

### Post by Riffer on 2008-04-27
Really?  I thought the minimum specs were PIII and 256 megs of ram.  Though the specs do say 10 gig of space needed.  With a 6 gig HD I wonder if this could be the problem.

edit;  I was wrong you only need 4 gigs.  But it says you need a minimum 256 megs of ram.

---

### Post by Michael.Godawski on 2008-04-27
I would also suggest trying out Xubuntu and using the alternate CD for the installation. Did you encounter any error messages during the installation or during the booting process? If no, try Xubuntu.

[http://www.easy-ubuntu-linux.com/ubuntu-system-requirements.html](http://www.easy-ubuntu-linux.com/ubuntu-system-requirements.html)
I wonder how you did install Ubuntu because the Live CD needs 384 MB of Ram

---

### Post by mypetduck on 2008-04-27
I did use the alternate CD. I'm trying Xubuntu 8.04 instead at any rate.

---

### Post by tyronenguyen on 2008-05-15
> **mypetduck said:**
> I did use the alternate CD. I'm trying Xubuntu 8.04 instead at any rate.

I had the same issue you described for my portege 3500.  

What fixed it for me was to try the steps to install ubuntu off the hard drive.  I had to install winxp first to do this.  

I can try to find you the tutorial if you want, but I just search on google for it.

One question, how is your CD connected to your laptop?  is it through a pcmcia card and the cd drive is a dongle that plugs into it?

If so, you might want to eject the pcmcia card before you hit enter on 'install ubuntu'.  This may get you past the blinking cursor issue.  You can plug the pcmcia card back in once ubuntu asks for the install cdrom.

---

