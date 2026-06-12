---
title: "Constant crackling in notebook"
date: 2013-04-29
forum: New to Ubuntu
---

### Post by Riftyful on 2013-04-29
Hello Ubuntu Forum!
I am currently facing a problem. I installed Lubuntu 12.10 in my sister's laptop few months ago, and now she wanted me to install it on the whole disk. (Deleting Windows XP) I have tried to install Lubuntu 13.04 from the LiveCD, but the installer either froze or crashed, probably due to somehow damaged DVD drive. So, I took the harddisk out of the laptop, connected it to my desktop and installed Lubuntu on it through my computer. So far everything works fine, but whenever the PC is not connected to a recharger, it keeps making strange crackling sounds, probably coming from the harddisk, since muting sounds doesn't help. It only stops when I play some sound or music, or when I connect it to the recharger. It did the same thing with the Live CD, too.
Here is the system information:

-Computer-Processor        : Intel(R) Pentium(R) M processor 1.60GHz
Memory        : 491MB (260MB used)
Operating System        : Ubuntu 13.04
User Name        : excised
Date/Time        : Po 29. duben 2013, 22:40:50 CEST
-Display-
Resolution        : 1280x800 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel

Thanks in advance!

P.S.: I have been using Linux for but a few months, I only understand some basic things about Linux, terminal and computers in general.

---

### Post by s1baker on 2013-04-29
I'm no expert, but when you install an .iso, I thought that the machine you would be running the OS on
would have to be the one to use for installation, because the install would need to check certain aspects
of the machine for proper libraries, etc.

 That said, do you have an external SD disk that you can put the install .ico on, attach to the laptop, and
then set the bios to boot the .iso from the SD disk? You might be able to install from there.

 I get a popping noise from my laptop if it gets to close to the wireless router.

---

### Post by Riftyful on 2013-04-29
I would prefer to install it on the laptop itself, but I believe that the BIOS doesn't support booting from usb, only harddisk, cd/dvd and netboot... Now when I think about it, netboot might have worked. However, I think you still ned a CD/DVD for that.

I'm going to wait a bit to see if this can get somehow solved, and if not, then I'll just try the netboot. 
Thank you for your time~

---

### Post by kamranm1200 on 2013-04-29
Netboot doesn't do anything. I tried it before. It just checks your ethernet card or something. But, is your computer close to a wireless router or anything? If not, then don't mind the crackling, even if the crackling is not supposed to happen. But, do you have any trouble with installing Lubuntu 13.04 other than the crackling in your laptop?

---

### Post by Impavidus on 2013-04-30
Could that sound be the hard disk repeatedly spinning down? If your sister plays something the system keeps reading from the disk, preventing it from spinning down, and if she connects the charger it comes out of the power saving mode, also keeping the hard disk spinning. This is consistent with the symptoms.

---

### Post by Riftyful on 2013-04-30
> [COLOR=#000000]But, do you have any trouble with installing Lubuntu 13.04 other than the crackling in your laptop?[/COLOR]
Generally, no. I only had problems on this specific laptop. Installation went smoothly on all the other computers so far.

> [COLOR=#000000]Could that sound be the hard disk repeatedly spinning down? If your sister plays something the system keeps reading from the disk, preventing it from spinning down, and if she connects the charger it comes out of the power saving mode, also keeping the hard disk spinning. This is consistent with the symptoms.[/COLOR]
That might be it. So far I only tried playing music on YouTube, but I noticed that it stops whenever the video is just loading or the tab with the video stays open. (I guess data about the video are being written to the disk?) If it's really the disk spinning, do you know of any not too risky way or program to stop it? Before, when she had 12.10, this crackling only happend once, when she would turn on the laptop and Lubuntu would load. (And it still does, but then it keeps going)

Also, is there any way to make Lubuntu re-detect the hardware or re-configure intself? (Since I installed it on my PC and when I put the hard disk back, the GRUB still displayed the operating sysems I had on my PC, although I already fixed that, but there might be more things like this)

EDIT: P.S.: Father says that the sound is coming from reproductors, (built-in reproductors, however they are called) if that might help in solving the issue.
EIDT: P.P.S.: I just validated that. When I connected headphones, the crackling played from the headphones instead. Muting the sound in alsamixer doesn't help.

---

### Post by Riftyful on 2013-05-01
After some searching on the internet, I found the solution! It probably had something to do with the sound card.
In case anyone has the same problem or wnts to know solution, I found it here:
[http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers](http://askubuntu.com/questions/160882/popping-noise-from-laptop-speakers)

Thanks everyone for help! SOLVED!

---

