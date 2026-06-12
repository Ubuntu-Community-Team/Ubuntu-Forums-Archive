---
title: "upgrading to 11.10 produces problem"
date: 2011-07-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by srinivasan.raman@hotmail on 2011-07-01
I had a very good experience with Ubuntu for the past 3 years.  I upgraded from 9.10 to 11.04 gradually and all went well.
Recently I upgraded my system from ubuntu 11.04 to 11.10.  After all the files are downloaded the system asks for switch over of display manager to GDM to some other display manager and I gave okay.
After a few seconds the screen become completely dark and I cannot see anything.
I restarted the system after some time and I think the installation is disturbed in the half way
Now I cannot boot the original 11.04 also
Neither recovery mode nor Ctrl+Alt+F1 works and I cannot even reach command line
Is there any way to repair/fix the problem with a live CD( Ubuntu 10.04)
Thanks in advance

---

### Post by howefield on 2011-07-01
Thread moved to "*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by cariboo on 2011-07-01
The only way to downgrade to 11,04 is to re-install it.What exactly is the problem when you boot into recovery mode?

---

### Post by PhantmKllr on 2011-07-01
> **srinivasan.raman@hotmail said:**
> I had a very good experience with Ubuntu for the past 3 years.  I upgraded from 9.10 to 11.04 gradually and all went well.
Recently I upgraded my system from ubuntu 11.04 to 11.10.  After all the files are downloaded the system asks for switch over of display manager to GDM to some other display manager and I gave okay.
After a few seconds the screen become completely dark and I cannot see anything.
I restarted the system after some time and I think the installation is disturbed in the half way
Now I cannot boot the original 11.04 also
Neither recovery mode nor Ctrl+Alt+F1 works and I cannot even reach command line
Is there any way to repair/fix the problem with a live CD( Ubuntu 10.04)
Thanks in advance
If you can reach the login screen on reboot, hit Ctrl -> Alt -> F2; that should bring up a terminal screen. From this screen you can update your system:
```
sudo apt-get update && sudo apt-get upgrade
```
This is all assuming that you've set up an active internet connection; just make sure you have the Ethernet cable connected/wireless adapter turned on before you start-up your computer.

Also, please be aware that 11.10 is a development release, and some breakage can happen.

---

### Post by ranch hand on 2011-07-01
There is this that MIGHT work.  Read the whole thing and seriously consider a clean install or, if on a 2 partition setup, just formatting the / partition (backup still a real good idea but should save your data).

This is, as pointed out, not supported.
[http://www.debian.org/doc/manuals/reference/ch02.en.html#_emergency_downgrading](http://www.debian.org/doc/manuals/reference/ch02.en.html#_emergency_downgrading)

---

### Post by srinivasan.raman@hotmail on 2011-07-03
Hi 
Thanks for all for your quick response and time.  However I did the following.
01. Earlier I created a backup.gtz file one month ago for the whole system.
02. Now I created a ext4 partition and extracted the backup.gtz file in it
03. After that using a live CD I install and update grub
04. Now the system is in Ubuntu 11.04 eventhough some of the software that I downloaded and personalisation like theme are missing
05. After that I upgraded to ubuntu 11.10 and all went fine and now, I am using Ubuntu 11.10:p
Now I have some of the issues.
Gnome panel not working at all, so for me there is no direct way to logoff/ shutdown the system than using the terminal
My earliest ubuntu partition is not mounted on booting(dev/sda6)
I will be thankful if someone helped me with this.
Thanks in advance

---

### Post by dino99 on 2011-07-03
install gnome-shell & gnome-session-fallback

---

