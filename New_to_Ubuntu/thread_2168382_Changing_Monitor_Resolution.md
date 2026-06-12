---
title: "Changing Monitor Resolution"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by llmunro on 2013-08-17
Hello forum!

I just installed Lubuntu 13.04 on an aging desktop computer, which has breathed new life into it and I'm enjoying it very much. Everythng seems to be working well, except that the monitor resolution [which seemed greater upon install and initial use] has changed after a reboot to 1024X786.  I'd like to increase the resolution, just to get a bit more screen space [on a small-ish 17" monitor], but the 1024x786 is the largest shown under Display Settings (all the other settings are much lower 800x600, etc). I've tried setting it to "auto," but that seems to give me the same screen resolution [1024x786].  

Any suggestions as to how to up the resolution?

Thanks ever so much.
Best,
Lisa

---

### Post by oldrocker99 on 2013-08-17
What is your graphics card? You may need to install proprietary drivers for an ATI or nVidia card. Bear in mind that certain ATI cards have been declared "legacy" and have no proprietary drivers, in which case you'll need the open source drivers, which have gotten pretty good. nVidia cards are usually the better choice for Linux, while ATI cards are usually the better choice for Windows (according to a lot of gaming PC builds I've seen).

For nVidia cards:

sudo apt-get install nvidia-current

For ATI cards:

sudo apt-get install fglrx

If you don't know what kind of card you have:

lspci | grep VGA (grep VGA will limit the answer to lines which contain 'VGA', which indicates video circuitry.

If you have Intel graphics, all the drivers are open source and possibly already installed.

---

### Post by llmunro on 2013-08-17
Hi,

Thanks for the help! It turns out that the nVidia driver was not installed.  I installed it as per your instructions and lo and behold, I've got more monitor settings, including 1360x768 and 1152x864.   I think that for the size of my monitor, the 1152x864 is going to work best.

Thanks so much!
Best,
Lisa

---

