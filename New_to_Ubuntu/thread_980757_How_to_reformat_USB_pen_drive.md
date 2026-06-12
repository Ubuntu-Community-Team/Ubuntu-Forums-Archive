---
title: "How to reformat USB pen drive"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by peakshysteria on 2008-11-13
I have an 8GB OCZ USB pen. The pen pops up when I attach it to my hub. But there's now disc icon on the desktop as with all other USB devices I try. It shows up in Places along with my other discs. It's also impossible to work with it since it seem to disappear when least expected. And since I can't find it nowhere (except in Places) I can't unmount it. How can I reformat and hopefully fix the pendrive?

It doesn't show up when I:```
lsusb
``` Even though it is working. Sometimes I can work with it sometimes it's impossible. Meaning it's quite unstable and untrustworthy.

I would really like to reformat it and install a persistent Ubuntu on it.

---

### Post by Jose Catre-Vandis on 2008-11-13
SUggest you visit [www.pendrivelinux.com](www.pendrivelinux.com) for answers to all your queries, or if you are running 8.10 there is a USB Creator built in, although I understand persistent mode is currently broken

---

### Post by peakshysteria on 2008-11-13
Thanks man. My first priority is of course to get the pen drive up and running again (if it is possible). The USB Creator feature in 8.10 seems like my kinda choice. Tombuntu had a nice article about it this morning: [Create a Bootable USB Drive the Easy Way in Ubuntu 8.10]("http://tombuntu.com/index.php/2008/11/12/create-a-bootable-usb-drive-the-easy-way-in-ubuntu-810/")

---

### Post by zzHanks on 2008-11-13
Did you try formatting it with Partition Editor (gparted)?

Or is it more complicated than that?

---

### Post by Paqman on 2008-11-13
Yep, Gparted will reformat your device if you want. However, from what you've described there's a good chance that it's faulty. USB flash drives only have a limited lifespan, and are mass-produced pretty cheaply.

---

### Post by peakshysteria on 2008-11-13
Hmm, any chance to found out if its broken forever or not?

---

### Post by ByteJuggler on 2008-11-13
Hmmm.  There can be many issues here.  The drive may be worn out, the drive connector may be loose, the PC USB port may be loose/faulty etc.

When you say it's unreliable, what do you mean exactly?    Have you tried moving the stick to another USB port?  Have you tried using it on another computer?  Does it behave the same there?

We need to establish it's not something physical (such as connector troubles) first, IMO, before deciding what we might try from a software side.

---

### Post by Jose Catre-Vandis on 2008-11-13
Here is vanadiums decent little howto on formatting a USB Stick

[http://ubuntuforums.org/showpost.php?p=2705255&postcount=6](http://ubuntuforums.org/showpost.php?p=2705255&postcount=6)

---

### Post by Jose Catre-Vandis on 2008-11-23
> **ByteJuggler said:**
> Hmmm.  There can be many issues here.  The drive may be worn out, the drive connector may be loose, the PC USB port may be loose/faulty etc.

When you say it's unreliable, what do you mean exactly?    Have you tried moving the stick to another USB port?  Have you tried using it on another computer?  Does it behave the same there?

We need to establish it's not something physical (such as connector troubles) first, IMO, before deciding what we might try from a software side.

Yes, if you are plugging it in via a hub, I would try direct into a USB port on your PC to see if that helps. Regarding gparted, I have found that unless the thing is properly mounted it won't show up (but then weirdly you have to unmount it to do any work on it!), so it could be that Places is finding something connected but not doing anything with it other than throwing up an icon.

---

