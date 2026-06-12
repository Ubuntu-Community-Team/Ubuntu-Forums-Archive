---
title: "NVIDIA GeForce4, Ubuntu does not install"
date: 2013-03-02
forum: New to Ubuntu
---

### Post by stef2222 on 2013-03-02
NVIDIA GeForce4 440 Go 64m
AMD Athlon(tm)64Processor 3000+ 798Mhz
network adapter Broadcom 802.11g


Hi, I have looked and looked through these page and the more i see the more i am confused.
I have been trying to run Ubuntu 12.10 on this laptop, ive got to the stage where it seems to load, Well, it gets to the try or install screen,.im running it from a pendrive, main os is xp. I click try and it then seems to just go to a red screen. I can see no icons and can do nothing. I am very confused. On the try/install screen there are a couple of icons in the top right corner and something pops up and says no internet connection then goes away but once i hit the try button they go and the screen is just blank red. Ive read that it may be down to the graphic driver, when i go to device manager and click the card it comes up with alist of driver files/confused.so cant give you that.This is very demanding, not what i was expecting, but ive heard great things about ubuntu so want to stick with it and learn, so any help please. Im sure you have been asked these questions time and again but as i say ive looked and just got more confused.It seems i need my hand held to make this work.Baby steps,  if anyone has the patience.Maybe im in over my head, if i should give up/ i dont want to do that but if you think i should then tell me. Many thanks

---

### Post by presence1960 on 2013-03-02
How much RAM does your machine have

Instead of choosing install or try ubuntu select check disk for defects and see what that reports

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso

This should cover some of the obvious basics. If all these check out then off to the next steps

---

### Post by Bashing-om on 2013-03-02
stef2222; Hi ! Welcome to the forum.
Let us pre-suppose that it is a grahics issue; Try this and advise:
Boot up the install medium, at the purple screen (stick figure and keyboard emblem at bottom of screen) hit any key -> language screen, escape key to accept the default -> boot option screen; f6 key for boot options list, choose the "nomodeset" option first try, f10 to continue the boot process. When you get to the desk top the launcher is on the left side of the screen ->Ubuntu Software Center ->Software sources (menu item in the task bar menu) -> Additional Drivers (tab) -> install the recommended driver. (this is supposing that you are hard wired for internet connectivity)
If "nomodeset" does not work try the other options.
[INDENT=2]

just try'n to help

[/INDENT]

---

### Post by zrdc28 on 2013-03-02
When it goes to the red screen and flags no network it could still be loading, the next time you try it just walk away from it and give it a few minutes, ubuntu
does not flag you in percentages as some other distros and is slow to load from cd/dvd.

---

### Post by presence1960 on 2013-03-02
> **Bashing-om said:**
> stef2222; Hi ! Welcome to the forum.
Let us pre-suppose that it is a grahics issue; Try this and advise:
Boot up the install medium, at the purple screen (stick figure and keyboard emblem at bottom of screen) hit any key -> language screen, escape key to accept the default -> boot option screen; f6 key for boot options list, choose the "nomodeset" option first try, f10 to continue the boot process. When you get to the desk top the launcher is on the left side of the screen ->Ubuntu Software Center ->Software sources (menu item in the task bar menu) -> Additional Drivers (tab) -> install the recommended driver. (this is supposing that you are hard wired for internet connectivity)
If "nomodeset" does not work try the other options.
[INDENT=2]

just try'n to help

[/INDENT]

it just may be graphics issue. I figure start at beginning to rule out basic iso problems. However would not surprise me a bit if it is a graphics issue

---

### Post by stef2222 on 2013-03-04
thank you for you posts, i will get onto trying these out asap, am just away working in the week. thanks again everyone

---

### Post by mörgæs on 2013-03-04
The graphics card is too old for Ubuntu, but Lubuntu is a good choice.

---

### Post by TREESofRIGHTEOUSNESS on 2013-05-13
I have an old computer with some of the same exact hardware.
Bashing-Om is correct, you will need to add the 'nomodeset' boot parameter (you will have to add this line to your /etc/default/grub)
mörgæs is also correct, you will want to use Lubuntu rather than Ubuntu ( [http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/) )
However, 12.04 should boot fine without the boot parameter. [http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/)
Though I needed the 64 bit version for my laptop to work 'out of the box'

Since I have a very similar computer you can feel free to pm if you have any specific questions.

---

