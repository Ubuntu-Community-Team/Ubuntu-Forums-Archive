---
title: "Ubuntu from thumb drive doesn't save anything"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by Bob_Dennis on 2013-10-18
I am running Ubuntu 12.04.3 LTS from a thumb drive (don't seem to be able to install on hard drive, also can't install Windows.) Nothing seems to be saved, including wireless logons, downloaded progrms, data in default locations.  In each session Ubuntu seems to run just fine, I can download and use Skype, Chrome etc, create documents, save them to external drives, etc.  But after reboot I have no Skype or any other downloaded program, I have to reenter password for wireless, and default saving locations for documents seem empty.

I am running directly from the thumb drive with the installation package I downloaded.  Should I have tried to use the installation procedure to install it to another thumb drive, since the hard drive installation doesn't work?  I don't see thumb drive install as an option in the installation menu.

Background:  All provoked by an irretrievable crash of Windows. Memory check and multiple hard drive checks OK.   Windows 7 reimage doesn't work.  Clean install of Ubuntu on hard drive from thumb drive looks as if it's working, but takes about 3 hours (on a quad-core hp pavilion laptop with oodles of memory) even with no updates, and then Ubuntu won't start from the hard disk.  I've pretty much assumed that there's some cryptic hardware problem--the laptop runs very hot--and given up on hard disk installation.  But maybe this background will give some clues.

Thanks for your help.

---

### Post by verymadpip on 2013-10-18
Hi there.
To save things in a Live Environment you would have had to make the thumb drive with a persistence file.  You'll want at least a 2GB flash drive for that.
I believe this can be done with Startup Disk Creator & Unetbootin.
I know that's no help *now*, unfortunately that's all I've got :/

I wonder if you can download the iso again & burn it in the Live Session..?  I'm sure someone brighter than me can answer that.

---

### Post by Bob_Dennis on 2013-10-18
Thanks, this gives me something to look for.  I've found several ways of getting a persistent file on the thmb dr,  at [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent). Not sure I understand everything, but I can experiment. Can anyone suggest which would be easiest for a Linux newbie?

---

### Post by verymadpip on 2013-10-18
Hey again.
I'd suggest Startup Disk Creator.  It's bundled with the distro, so you won't need to download it, & it's pretty easy to use.

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

---

### Post by Bob_Dennis on 2013-10-31
Thanks very much to both of you.  Now I know about persistence, successfully installed Ubuntu Studio.

---

### Post by kurt18947 on 2013-11-01
One thing about persistence.  You can save network logins and things.  I've never been able to install any O.S. updates though.  Well, I could but the live USB would fail after an update or two.  It is possible to create a "real" install on a USB drive, it'd be slower to load than off a hard disk but it is possible.

---

