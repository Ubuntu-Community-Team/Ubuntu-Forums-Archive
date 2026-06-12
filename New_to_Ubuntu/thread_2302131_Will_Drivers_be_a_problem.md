---
title: "Will Drivers be a problem?"
date: 2015-11-08
forum: New to Ubuntu
---

### Post by Weboh on 2015-11-08
I'm thinking about installing Linux on my Lenovo Thinkpad  Edge E540 laptop. I checked on Lenovo's drivers page for it, and I don't  see any Linux drivers there. I'm pretty sure it has one of those  specialized GPUs where a default driver won't *quite* work.I see it's [certified by Canonical for Linux]("http://www.ubuntu.com/certification/hardware/201309-14166/")...  Ubuntu 12.04. Does that mean that all versions of Linux will be able to  pick up the drivers? Or does that just mean that Linux can be  preinstalled by OEMs if they have the drivers (I noticed there weren't  links to download them there either)?

---

### Post by sudodus on 2015-11-08
If it is certified by Canonical for Linux, it is very likely to work with the Ubuntu family iso files.

I don't know the specific details of your computer. But you should always [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Bucky Ball on 2015-11-08
Many drivers are included in the Linux kernel, not like Windows. It's rare you need to install drivers for every little thing. :)

Lenovo is very Linux friendly. As sudodus suggest, burn and ISO, create a disk or USB, boot from it and 'Try *buntu' from the install media. See what gives and if all is well, go ahead and install it. Try a few flavours, though, if you don't like the first. Xubuntu and Lubuntu are simple desktop environments while Ubuntu uses Unity, loved or loathed depending on taste it seems, and Kubuntu is different again. 

Have a look around, enjoy, if you have questions, just ask. :)

PS: It is generally wireless or graphics that are a problem if there is going to be one and the drivers for those won't be on the Lenovo page. They'll be on the graphics and wireless card manufacturers' pages. Boot to a live session ('Try Ubuntu' from install media) and if wireless doesn't work 'automagically', with an ethernet cable plugged in, run an update (Software Updater) and see if you are offered an available driver for you card. If not, check additional drivers. 

If there are drivers there, that's great, BUT, as you are on a live session, if you install them and they will work for the session they will be gone on reboot. They'll only stick around if installed on a hard drive install.

Hope that's not 'too much information'. There's a start. :)

---

### Post by David_Medeiros on 2015-11-08
You will probably be just fine. you don't need to care about drivers on Linux. They come with the kernel.

---

### Post by mastablasta on 2015-11-09
if it is certified for 12.04 it means all will work well with that version. 14.04 - you can try it in live session. it should work out of the box but no one guarantees it. as they often do changes to drivers in kernel. the reason why there are no drivers in lenovo site is because other people made opensource drivers for various components and stuck them in the kernel.

---

### Post by brian106 on 2015-11-10
I had exactly the same concerns in trying to extend the life of my Compaq 110c mini-laptop, which came with Win XP. I ran a full install of Win 10 TP, hoping that I would then be able to upgrade when the final version was available. I signed up for the MS Insider programme and made my contribution to the development of the product. Even so, MS kicked me in the whatsits, when they terminated Win 10 TP and the laptop would not even boot. HP told me they could not provide drivers for Win 7 and they suggested I try Linux. I decided to download Ubuntu and installed it easily. The only hiccup was that I could not make a wireless connection. A bit of searching revealed that I needed a Broadcom driver that was available from the Ubuntu Software Centre. I download that and the problem was resolved immediately. This was only two days ago and I am finding it great fun. As others have said, you should have no problem so good luck with your installation.

---

