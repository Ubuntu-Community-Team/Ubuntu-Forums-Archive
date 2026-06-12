---
title: "Things are going from bad to worse"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by shelbyvision on 2008-04-29
Hi,
I posted about my problems before in my previous thread, "Synaptic removed Terminal! Can't get it back". At that point, I had not yet shut down the OS, so I did not know the full extent of the damage. After shutting down and rebooting, it now goes to the login screen normally, but after logging in, I get a blank pinkish screen with a mouse pointer, and nothing else. I tried booting in diagnostic mode and reinstalling ubuntu-desktop, and it did a lot of stuff, including having me put in the install CD, and I thought all was well, but when I booted up, I got the same blank screen. Is there anything I can do to fix this, or am I going to have to do a complete reinstall?
Thank you,
Steve

---

### Post by billgoldberg on 2008-04-29
I'm sure it can be fixed, but I don't know how.

A clean install would be faster to fix the problem.

Use the ubuntu live cd to access the files on your harddrive you wish to keep and copy them to some external media or another partition.

---

### Post by jflarm on 2008-04-29
Try this:
1.Create a new user and see if it has the same problems

or

2.On a terminal after you log on (Alt + F1) remove your .gnome directory. Log out an log in again, if you don't have a .gnome directory the system will create a new one for you.

---

### Post by shelbyvision on 2008-05-01
I saw another recent thread where people were having more or less the same problem: Installation & Upgrades [ubuntu] blank screen at first login after install. I tried doing sudo dpkg-reconfigure xserver-xorg, as suggested in one of those posts, and went through the whole configuration with no problems. Now, instead of going to the ubuntu login screen, it goes to a black screen and flashes these five lines about three times, then stops flashing.
*Starting anac(h)ronistic cron anacron
*Starting deferred execution scheduler atd
*Starting periodic command scheduler crond
*Checking battery state...
*Running local boot scripts (/etc/rc.local)
There's a blinking curser here, and I can type anything I want, but I don't know what to type.
Steve

---

### Post by Ozor Mox on 2008-05-01
> **shelbyvision said:**
> I saw another recent thread where people were having more or less the same problem: Installation & Upgrades [ubuntu] blank screen at first login after install. I tried doing sudo dpkg-reconfigure xserver-xorg, as suggested in one of those posts, and went through the whole configuration with no problems. Now, instead of going to the ubuntu login screen, it goes to a black screen and flashes these five lines about three times, then stops flashing.
*Starting anac(h)ronistic cron anacron
*Starting deferred execution scheduler atd
*Starting periodic command scheduler crond
*Checking battery state...
*Running local boot scripts (/etc/rc.local)
There's a blinking curser here, and I can type anything I want, but I don't know what to type.
Steve

I have this problem when booting from the live CD, and fixed it by booting in safe graphics mode (press F4 at the boot screen). If you are not booting the CD, select 'Failsafe GNOME' from Options > Select Session in GDM for what I think is the same effect.

---

### Post by The Crazy Parrot on 2008-05-01
if you have terminal access try

sudo apt-get install xdm

I had a problem with a bugged gdm (gnome display manager) and xdm (x display manager) allowed me to log in.

---

### Post by The Crazy Parrot on 2008-05-01
P.S. if you have gdm you can use the failsafe terminal, otherwise control-alt-F1 will get you there

---

### Post by forrestcupp on 2008-05-01
Well, you could try booting to recovery mode.  If you have Hardy, it will give you a menu where you can choose to drop to root.  Then try typing
```
dpkg-reconfigure ubuntu-desktop
```Then type **exit** and if you're in Hardy, choose to resume normal booting.

---

### Post by shelbyvision on 2008-05-02
It looks like it's beyond repair. When I asked it to reconfigure ubuntu-desktop, it told me ubuntu-desktop is not installed. So I tried install ubuntu-desktop, and it told me it couldn't find it. Everything I try gets rejected. I'm giving up and re-installing from scratch.
Steve

---

### Post by shelbyvision on 2008-05-03
I used gparted and completely removed my old Ubuntu OS, and installed it again from the CD (Ubuntu 7.10). It still does what it did before, as I described earlier, it gets to these lines:
*Starting anac(h)ronistic cron anacron
*Starting deferred execution scheduler atd
*Starting periodic command scheduler crond
*Checking battery state...
*Running local boot scripts (/etc/rc.local)
and then stops.
I tried dpkg-reconfigure xserver-xorg, and set it up correctly, but when I boot it again, same thing. I tried the reconfigure xserver-xorg again, and it seems to have not remembered the info about my video card, which I had filled in previously.
This is driving me crazy! How do I resolve this?
Steve

---

### Post by GavinZac on 2008-05-03
Could you post your hardware?

---

### Post by shelbyvision on 2008-05-03
It's a Gateway celeron 1.2GB, with 256 MB RAM, ATI Radeon 7000.
It worked just fine with Ubuntu 7.10 with the first installation, until I messed it up. I do recall, though, having to fiddle with the video card setup on the first installation, in order to see it.
Steve

---

### Post by GavinZac on 2008-05-03
theres a new linux kernel in the repositories today, perhaps you could try updating to that via command line?

---

### Post by shelbyvision on 2008-05-03
Do you mean upgrade to 8.04? On the web page, [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading), it says "Be sure that you have all updates applied to your current version of Ubuntu before you upgrade." Seeing that, I realized I hadn't tried upgrading, so I had it upgrade all packages from the command line, and it went through the whole process successfully, but, unfortunately, it still does the same thing when I boot it up.
Steve

---

### Post by shelbyvision on 2008-05-12
I finally got ubuntu working properly. It turned out that in the xserver-xorg configuration, I was using information that I had written down before, but had written incorrectly. The crux of the problem was the "bus identifier" which I had incorrectly written as PCI:0:2:0. Checking back on info I had written down from Windows, I found out the numbers were supposed to be 1:10:0. I wasted a lot of time unnecessarily, while the solution was so simple. Thanks to all of you who offered help. 
Now I still have one question...I got the correct numbers from Windows. If I had not had Windows installed on this computer how would I have found the correct bus identifier numbers?
Thanks,
Steve

---

### Post by SteveNorman on 2008-05-12
I believe this would work:
from the command line

    sudo lshw

to save this as a printable html file do this:

    sudo lshw -html > name_of_file.html

where name_of_file is whatever name you give it.

open firefox, hit: 

    file>open file>name_of_file.html

then you can print the results to have on file for the next hindenburg flyby

---

### Post by shelbyvision on 2008-05-13
Thank you for that useful tip. I tried it out and it really gives a wealth of information about my computer. The odd thing is,though, the bus identifier numbers it gives for my display are different than the ones that worked in my xorg configuration, so I'm not sure it would be of help.
Steve

---

### Post by SteveNorman on 2008-05-13
try this

lspci

or
 
sudo X :1 -scanpci


see if those match up

---

### Post by shelbyvision on 2008-05-13
Thanks again. The first one uses a slightlt different system, where 10 is stated as 0a, so it shows 1:10:0 as 1:0a:0. The second one shows it in the more familiar way. Now I wonder... If it was still set up wrong like it was before I fixed it, would those files show the correct numbers or the incorrect numbers?
Steve

---

