---
title: "Advanced User With Basic Problems"
date: 2012-07-13
forum: New to Ubuntu
---

### Post by kigconker on 2012-07-13
I just got a new laptop for school.(Samsung series 7 Chronos 15.6) The computer is awesome, blazing fast, ultralight, and beautiful. The machine is a dream to work with.

But I truly hate windows, and if it wasn't for the industry support I wouldn't use it. So naturally I decided to use my personal favorite flavor of LINUX, Ubuntu. I love Ubuntu, it's such a pleasure to work with. It is a nice easy transition for the average windows user, and is still open enough to keep even the most hardy LINUX user entertained. I was running the 12.04 release. I used the desktop install just so I din't have to muck about with live images and boot cycles. I got it up and running, the same wonderful Ubuntu I Have on my desktop.

The fist time I closed my laptop, it did not resume from suspend. I had to force a shut down, I looked it up, I thought it was my swap partition. My swap partition is 32gigs. I only have 8gigs of ram, my swap partition had plenty of space, not the problem.

I did some research and the two codes featured here [http://ubuntuforums.org/showthread.php?p=11926504]("http://ubuntuforums.org/showthread.php?p=11926504"). No dice, neither of the codes worked so I made my own. I was very similar to the second code on that thread. Still didnt work. So I gave up.

I then decided to try and replace the standard Unity desktop with the one I have on my other LINUX machine, Cinnamon. I got it to install to without a hitch. Until I logged in using it. I wasn't Cinnamon. No extensions, no applets, and the menu bars were standard Gnome. None of my setting would keep.

So after accidentally closing my lid, My OS corrupted again. So once again I ran a disc check and after the repair I just uninstalled Ubuntu.
The way it is running it is unusable. None of the documented fixes are working. I am not a LINUX noob. I have fixed the suspend problem on Linux laptops before. After working on this for around 20 hours, I can't figure it out, so now I'm distressed because I love Ubuntu. I don't wanna have to use a different flavor. I appreciate any help I can get.

---

### Post by z3nhakr on 2012-07-13
i assume you installed the 64bit edition? have you tried changing your standby state in the bios?

[http://blogs.msdn.com/b/omars/archive/2004/05/11/129553.aspx](http://blogs.msdn.com/b/omars/archive/2004/05/11/129553.aspx)

---

### Post by kigconker on 2012-07-13
> **z3nhakr said:**
> i assume you installed the 64bit edition? have you tried changing your standby state in the bios?

[http://blogs.msdn.com/b/omars/archive/2004/05/11/129553.aspx](http://blogs.msdn.com/b/omars/archive/2004/05/11/129553.aspx)
Yes I am, I have an Intel 64bit cpu. 
Hmmmm no, the crash log would support that.

---

### Post by z3nhakr on 2012-07-13
when it hangs on the resume can you get to the command line with ctrl+alt+f1?

---

### Post by kigconker on 2012-07-13
> **z3nhakr said:**
> when it hangs on the resume can you get to the command line with ctrl+alt+f1?
No I can't, Also my boot state is S3, I cant change it, but that is the state it needs to be anyways.

---

### Post by z3nhakr on 2012-07-13
Check these files and see if you can find an error

/var/log/pm-powersave.log
/var/log/pm-powersave.log.1
/var/log/pm-suspend.log
/var/log/pm-suspend.log.1

---

### Post by kigconker on 2012-07-13
Looking at the files in my last corrupted install, Actually my swap partition seemed to have been re-sized. I'm going to try re-installing and changing the swap partition size manually.

---

### Post by z3nhakr on 2012-07-13
ok. good luck! (y)

---

### Post by kigconker on 2012-07-13
Well I have no Idea why suspend wont work, I'll post the powersave and suspend logs and you can look through them if you want.
EDIT: Well I got it to work. I installed the latest dailly build of 12.10. Now I'm of course trying to get outdated ppa's to update on my new system :>

---

### Post by z3nhakr on 2012-07-15
ok. so 12.10 fixed the problem? btw how stable is it? just curious ;)

---

### Post by kigconker on 2012-07-15
The only problem I'm having is the AMD drivers for my card will not work. But it is completely incapacitating and I'm gonna have to downgrade.

---

