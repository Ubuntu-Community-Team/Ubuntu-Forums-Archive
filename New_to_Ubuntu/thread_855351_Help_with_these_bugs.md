---
title: "Help with these bugs?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Paz13 on 2008-07-10
i got these two bugs as i loaded my pc, it said a little message and...

xprop -root/grepxkb

gconftool -2 -r/desktop/gnome/peripherals/keyboard/kbd

i know one of those is the keyboard and i changed to to generic didn't work, i got these problems tinkering with the display settings i typed some reset code with xserver or something not theres a problem with it. Can anybody help me out i'm a real noob or do i need a re-install

p.s. my ubuntu just got really slow mabey thats an effect of the first one???

---

### Post by Paz13 on 2008-07-10
bump

---

### Post by Paz13 on 2008-07-10
anybody?

---

### Post by philinux on 2008-07-10
What version ubuntu you running and does it boot up and login ok.

---

### Post by Paz13 on 2008-07-10
hardy 8.4 all updates in it boots ok loading screen takes quite a while 4 times longer than before

---

### Post by philinux on 2008-07-10
I assume you mean the length of time before the login screen appears.

Press esc key when grub starts to load and select the recovery mode. At the menu prompy choose xfix.

---

### Post by Paz13 on 2008-07-10
i ment when you login it takes ages for the GUI to load with all my programs and files. i'm think it could be my computer that can't handle ubuntu. 
I did what you said but it didn't solve the problem the error message is still displayed on entering the GUI. 
any other ideas or do you think fresh install?

---

### Post by philinux on 2008-07-10
What are you're system specs.

One to try is this Browse to your home folder, then ctrl h to show the hidden files.

Highlight and delete any starting .gnome

Logout then login and these folders will be recreated for you back to their defaults.

---

### Post by Paz13 on 2008-07-10
i just tried what you said and it didn't make a differance it came up with the same errors, thanks so far for helping me.
I think i have a 256mb ram computer and i'm thinking about xbuntu since it's the faster less ram usage ubuntu

---

### Post by philinux on 2008-07-10
Well these are the specs.
System Requirements

The minimum memory requirement for Ubuntu 8.04 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.)

**With only the minimum amount of memory available, the installation process will take longer than normal, but will complete successfully, and the system will perform adequately once installed.**

So you should be ok. Whats the rest of you're spec.

---

### Post by philinux on 2008-07-10
I would run this then reboot.

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Paz13 on 2008-07-10
so you reckon xbuntu? that should fit 256 right?
i tried installing it but the cd wouldn't boot and i checked the sums but they were allways wrong

---

### Post by philinux on 2008-07-10
No if you're installed already Ubuntu as it is should run. Just no zippy.

you can install xubuntu-desktop from synaptic as well as having ubuntu-desktop installed.

At login you choose your session as either xubuntu (xubuntu-desktop environment) or ubuntu (ubuntu-desktop environment. see you can even have KDE destop available too. It just means your menu's get a bit cluttered thats all.

No need to reinstall.

---

### Post by Paz13 on 2008-07-10
ok well the type in code and re-boot didn't work, it's either re-install ubuntu now or have you more knowledge to kick to me?

---

### Post by philinux on 2008-07-10
Those errors are odd. Did you tinker with anything before those errors appeared.

Re-read first post arrggh

Go to the terminla and hit the up arrow key and see if you can see in it's history the command you gave.

---

### Post by Paz13 on 2008-07-10
i tried to get my computer working on my lcd i hit

rm -rf .gnome .gnome2 .gconfd .metacity 
sudo dpkg-reconfigure xserver-xorg

the 2nd one was like urs without the -high
these two caused the problem

---

### Post by philinux on 2008-07-10
use 

metacity --replace

---

### Post by Paz13 on 2008-07-10
sorry didn't work them bugs still displayed on the message mabey if i do the recofigue xserver choose defult all the way through or something?

---

### Post by philinux on 2008-07-10
> **Paz13 said:**
> sorry didn't work them bugs still displayed on the message mabey if i do the recofigue xserver choose defult all the way through or something?

Yes I would do that with

sudo dpkg-reconfigure xserver-xorg

---

### Post by Paz13 on 2008-07-10
can't berlive it still error messages what do you recomend?

---

### Post by philinux on 2008-07-10
> **Paz13 said:**
> can't berlive it still error messages what do you recomend?

Hope someone else can help with this, it's time for a beer.

At least your system is working, just not optimum. I would not reinstall just yet.

Someone will chime in. just dont bump too soon.

---

### Post by Paz13 on 2008-07-11
bump

---

