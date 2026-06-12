---
title: "Toshiba NB100 with Ubuntu"
date: 2019-04-08
forum: New to Ubuntu
---

### Post by palayhala on 2019-04-08
Hello,

I have purchased a Toshiba NB100 with Ubuntu factory installed on it.

This is the second time I have accidently purchased a laptop with Ubuntu installed this week.
(I have managed to replace Ubuntu with windows 7 on the Advent 5411, thankfully).

I really don't know much about Ubuntu and it seems way too much and too complex to learn to operate it as I have been a Window user all my life. Feels like to me, it's some Operating System designed  maybe for Developers.

After spending hours and hours researching and watching a lot of YouTube videos, I eventually managed to replace Ubuntu on the other laptop (Advent 5411). I got some feel of using Ubuntu. But on Toshiba NB100, I feel like I am having to start from scratch again because the layout is so different to what it was on Advent 5411.

Toshiba NB100 already has a User account created for it which I have managed to update the password for. However, it seems to have some sort of an Admin (root?) password that prevents me from making any major modifications and I don't know how to go about it.

I have Ubuntu 8.04 (I think) installed on the Toshiba NB100. It has hundreds of updates waiting to be installed but when I try to install them, it comes back with an error

What I am willing to try is learn to use Ubuntu (maybe I will like it), factory reset my Toshiba NB100, install the latest software and make a brand new start on it. But I am unable to restore it to factory settings at the moment.

Please can you advise where do I start the factory reset process. At the moment I can't even find the "Terminal" from the menu.

Thanks

---

### Post by Autodave on 2019-04-08
Without knowing for sure what version is installed on that, I can't really help much.  IF it is 8.04, that is 11 years old and way past any support.

If you reset the password, then that is your root password.

From what I am finding, that is a single core processor which means that you are very limited in what you can install on there since 32 bit support is quickly vanishing.  My suggestion would be to download a copy of Xubuntu 18.04 32 bit and install that.  Xubuntu has a lower RAM requirement than Ubuntu. Plus, it is a little simpler (at least in my opinion) to use.  Once you download it, you need to put it onto a DVD or thumb drive as an .iso file.  You cannot simply copy the file onto it.  Boot the machine with that installer and follow the instructions on the screen.

---

### Post by palayhala on 2019-04-08
Thanks. I'll try this and post the outcome here.

---

### Post by DuckHook on 2019-04-08
Not to step on Autodave's toes (because his is excellent advice), but Xubuntu uses a compositing window manager. On your ancient machine, 32-bit Lubuntu may be the better choice. Your graphics subsystem is very underpowered and could do without the overhead imposed even by compositing.

You could try out both and see which is most responsive. However, plain Ubuntu or Kubuntu are definitely too resource-intensive for your system.

Because you are new to Ubuntu and dealing with very underpowered HW, please see the links in my sig: *Linux is not Windows* and *Resurrecting Old Hardware*. For a survey of the various flavours and a brief description of each: [What is the Best Ubuntu Flavour?]("https://ubuntuforums.org/showthread.php?t=2415676")

---

### Post by Impavidus on 2019-04-08
Now I wonder how a laptop from around 2008 with Ubuntu 8.04 factory-installed came to be in the same configuration 11 years later. You'd expect someone to install a more modern operating system at some point.

If I get the specs right ([https://www.notebookcheck.net/Toshiba-NB100.12668.0.html](https://www.notebookcheck.net/Toshiba-NB100.12668.0.html)), that thing has an Intel Atom N270 processor, which is indeed 32 bit, only 1GiB memory and weak graphics. I suggest Lubuntu 18.04 LTS 32 bit. Support for 32 bit is dwindling, but that should get you at least 2 years of life out of that laptop.

There's no magical factory reset button on Ubuntu & friends, the way to reset is to wipe the hard drive and fresh install. Does that scare you? You've got nothing to loose, right? At one point in my life I had been a Windows user my entire life too. Ubuntu developers make Ubuntu as they think it's best, to make a good system, not to maximise market share. That means it's indeed somewhat made for developers, but it's definitely usable for ordinary users. On Linux, you may need a bit more technical knowledge than on other systems, but in return you get a system that's more secure and gives you the freedom to use it as you want.

But 8.04 is no option. Support for that release ended in April 2011 (2013 for the parts in common with the server edition). The normal method on Linux (now also used by smartphones) is to have all software for both operating system and applications in central repositories, so an unsupported release means no security updates for anything. Bad idea. So don't attempt to somehow reset your 8.04 system. Just get that install disk and follow the instructions to wipe the hard drive and install 18.04.

---

### Post by oldrocker99 on 2019-04-08
> **palayhala said:**
> Hello,

I really don't know much about Ubuntu and it seems way too much and too complex to learn to operate it as I have been a Window user all my life. Feels like to me, it's some Operating System designed  maybe for Developers.



Linux long ago lost the "by geeks, for geeks" reputation is once had. Every distribution (except maybe for Arch) is deliberately made to be easy to use, without need for the dreaded terminal if you don't want to. It is, IMHO, easier to learn than Windows 10, and is a robust, full-fledged operating system, which accomplishes every thing I have wanted my computer to do for 9 years.

You can download any of the various versions of Ubuntu (I would suggest Ubuntu MATE), burn it to a USB; Etcher is the best program for that. Boot from the USB. It won't touch your C:\ drive, and you can take it for an extended test run. 

Give it a shot. You might even like it, and you **can** dual-boot Linux with Windows.

---

### Post by DuckHook on 2019-04-08
> **oldrocker99 said:**
> …and you **can** dual-boot Linux with Windows.
Though possible, such a Windows experience is unlikely to yield the warm and fuzzies. I have old laptops more powerful than this and they have trouble running XP, never mind W7—which will reach EoL in 9 months anyway. Good luck trying to run W10 on it.

To be really, really honest, the best use for such lovable old clunkers is none of the above. They are most useful as some form of command line server: whether file, print, torrent, vpn, backup, etc etc. The list is limited only by one's imagination. By eliminating the GUI component, they actually become useful again. However, for most general users, such advice is not really "practical", so I hesitate to go there. After all, how is a user new to Ubuntu going to jump right in to the command line?

But for what it's worth…

---

