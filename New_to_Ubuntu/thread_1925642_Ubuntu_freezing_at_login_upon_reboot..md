---
title: "Ubuntu freezing at login upon reboot."
date: 2012-02-14
forum: New to Ubuntu
---

### Post by JD2008 on 2012-02-14
I'm pretty rusty when it comes to linux, havent had a linux box since Fedora core 3.
 
Installed Ubuntu duel boot with windows 7, with the download and install updated packages option checked. Everything worked right off the bat, I was amazed/excited.(the last time i installed linux on a laptop it took me a week to get wireless running)
 
I surfed the web and checked out Ubuntu in general for about an hour, no problems at all. I rebooted (remembering the olden days when stuff randomly died in linux when rebooting) Booted fine, check out the software manager and other features. I was enjoying my new painless linux install. I shutdown Ubuntu and came home(I was at work) Now when I attempt to boot into Ubuntu Its freezes at the login screen, I actually did get to put in my whole password once before it froze.
 
Any ideas would be appreciated. If I need to give more info or error logs please let me know whats needed and how to get it, since i cant log in.

---

### Post by Bucky Ball on 2012-02-14
Which release are you using?

---

### Post by JD2008 on 2012-02-14
Ubuntu 11.10.
I booted with the recovery mode then did a filesystem check, dropped to root command line, then rebooted. Seems to be working fine now. hopefully its all good now. Are there any error logs I should look at for a cause to the problem? Such as .xsession-errors or some other file.

---

### Post by JD2008 on 2012-02-15
Definitely not fixed. It worked fine last night for around 2 hours. Logged out, then shut down. Now Its freezing again. No apparent pattern, sometimes freezes at login screen sometimes freezes right after login. I have gotten as far as logged in and open a terminal, before it freezes.

Ubuntu 11.10, Acer aspire 5250 2GB ram, AMD duel core, ATI Radeon HD 6310. 
320GB HDD, 60GB for ubuntu. 

Booting with grub. Using default window manager(think its unity). Have not Activated the additional ATI driver yet. (maybe this is the problem?) if so how do I boot without X, and activate with command line.

As stated before, If more info is needed please let me know. and how to get it via command line. thanks

---

### Post by JD2008 on 2012-02-16
Still having this issue. How do I disable the splash screen at boot, so i can look and see what process is hanging up. Also, how do I disable X and boot to command line. Maybe I can get this figured out soon. At least im getting reintroduced to problem solving. 

one other question, should I be running the 64bit, I noticed windows is 64bit on my machine.

Occasionally, I can boot up, log in and things work fine for hours. 99% of the time I try booting it locks up requireing a hard reboot. I have yet to install anything else besides the default install.

---

### Post by bogan on 2012-02-16
Hi!, **JD2008**,

In the grub menu, select the Ubuntu entry you want and press 'e' to get to the edit screen.

Move the cursor to the Linux boot line, where it says 'ro quiet splash' and alter it to: 'ro --verbose text'; then press 'Ctrl+x' to boot.

If you get it wrong, 'Esc' will take you back to the menu, or Ctrl+c will give a grub prompt with limited commands available, see text at bottom of grub menu screen.

If all is well you will get a tty log-in prompt, if not press Ctrl+Alt+F1 or F2; Ctrl+Alt+F7 will take you to what should be the graphics screen.

Log-in and enter password and you will get a Terminal prompt. Enter ```
sudo service lightdm start
``` to get to the full GUI screen.

A 64 bit system will run a 32bit installation OK.

Chao!,** bogan.**

---

### Post by Bucky Ball on 2012-02-16
. In error

---

### Post by topdog2009 on 2012-02-20
Hi guys
I am having the same problem - Ubuntu 11.10 freezes after entering password (get red Ubuntu screen. When first installed (fairly recently) it appeared to work OK. Not used for some time though.

Dual boot machine Windows 7 and Ubuntu. Plenty of RAM available. Previous reply indicate going to Grub menu ...HOW??

Also reference found to boot repair but if system is frozen how do I get it?

Brian

---

### Post by Bucky Ball on 2012-02-20
> **topdog2009 said:**
> Hi guys
I am having the same problem - Ubuntu 11.10 freezes after entering password (get red Ubuntu screen. When first installed (fairly recently) it appeared to work OK. Not used for some time though.

Dual boot machine Windows 7 and Ubuntu. Plenty of RAM available. Previous reply indicate going to Grub menu ...HOW??

Also reference found to boot repair but if system is frozen how do I get it?

Brian

Please start a new thread with a descriptive title rather than jumping on this one. Trying to help two OPs on the same thread becomes confusing for everyone. Post a link back here if you want. ;)

---

