---
title: "Compaq Presario 700: Problem booting Lubuntu after installation"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by dcrocker2 on 2013-10-27
Hi, I was hoping to resurrect my old Compaq Presario 700 laptop (with 384Mb RAM) for web browsing. So after some research I downloaded the lubuntu alternative install, burned it on to CD, and installed from CD. The installation appeared to go well, it even found the PCMCIA network card and connected to my WLAN. However, it won't boot properly. This is what happens when I try to boot from hard disk:
 
1. First it prints a couple of messages. They are displayed for so short a time that I can't get a photo of them. One says something about SMBUS and "Upgrade BIOS or use force-...". The other also mentions upgrading the BIOS. The machine is so old that I very much doubt it is possible to upgrade the BIOS, in any case that would probably require Windows, which is no longer on the machine since I repartitioned the disk for lubuntu. I think the messages may be the same ones mentioned in this thread: [http://ubuntuforums.org/showthread.php?t=1564846&highlight=lubuntu+smbus+message](http://ubuntuforums.org/showthread.php?t=1564846&highlight=lubuntu+smbus+message).

2. Then it clears the screen and displays a couple of messages of text. The first says "Ubuntu version 13.10 ubuntu-laptop tty1" and the second says "ubuntu-laptop logon:". At this point, if I very quickly type some characters on the keyboard, they are echoed. However:

3. Whether or not I type any characters, after about half a second the screen changes to the one shown at [https://www.dropbox.com/s/zs4ej4epdmbtmak/2013-10-27%2020.46.54.jpg](https://www.dropbox.com/s/zs4ej4epdmbtmak/2013-10-27%2020.46.54.jpg). The machine does not appear to respond to the keyboard at all - even the CapsLock key doesn't affect the Capslock light.

4. However, if I press the power button, there is some disk activity and the machine powers down after a few seconds. So maybe Ubuntu is working, but stuck in an incorrect video mode? I think the laptop screen resolution is 1024x768.

Does anyone have any suggestions? Is there a key I can press during boot that will get me into something akin to Windows safe mode to debug this? Thanks in advance.

---

### Post by mörgæs on 2013-10-28
Web browsing is a heavy task, and such old hardware is not a good foundation. I believe you have an AMD Duron without SSE2 support, so you can't run the latest Flash. Other applets can technically run, but not at a usable speed, so you will be limited to browsing light web sites. Keep your expectations low. 

Are you aware of problems upgrading the BIOS on this specific model?

Have you considered a core install of Lubuntu?
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

---

### Post by dcrocker2 on 2013-10-28
Hi mörgæs, thanks for replying. I don't need flash, all I want to do on this machine is search for and download/read technical datasheets in pdf format. Ability to run Thunderbird or another IMAP email client wold be nice but not essential.
 
The only BIOS update available (which I can't install without somehow re-installing Windows on the laptop first) is dated 2002 and the documentation for it says "Fixes intermittent issue where BIOS password would be unintentionally modified.", so I hardly think it's going to help.
 
I'll try a core install - looks like that uses a different graphic environment, so maybe that will help.

---

### Post by mörgæs on 2013-10-28
The core Lubuntu contains the same desktop environment, but with less applications and daemons. 

Are you able to boot from USB?

---

### Post by dcrocker2 on 2013-10-28
Hi, the computer is too old to boot from USB. However, I burned the standard install disk and tried the "Try lubuntu without installing" option (which I guess I should have done first). It produces what I think are the same 2 messages, this time overlaid on a graphic screen. Then the display again goes into what looks like a bad video mode, although not quite the same as when booting from the hard disk. This time, the messages lasted long enough for me to photograph them. They are:

[156,337925] vt596_smbus 0000 <something>
SMBUS: Error: Hiost SMBUS controller not enabled!- upgrade BIOS or use force=1

[160.074608] via686a 0000;00:07.4:
base address not set - upgrade BIOS or use force_addr=0xaddr

So I guess lubuntu won't work on this machine - unless anyone has any suggestions?

---

### Post by mörgæs on 2013-10-28
You already have two suggestions:

> **dcrocker2 said:**
> 
use force=1


> **dcrocker2 said:**
> 
use force_addr=0xaddr

There should be plenty of threads available dealing with these settings.

---

### Post by mike-parenti on 2013-10-28
There are other distributions of Linux that run better on very old hardware.  I have a Presario 2100 laptop that I installed Xubuntu onto, bit it ran painfully slow.  I tried to install  Kubuntu & Lubuntu on it, but the installs failed to get past the initial stages.  So I install Puppy Linux on it.  I was succesful with Puppy Racy, but if that doesn't work try Puppy Wary.  And as  stated above, don't expect too much from that lap top, but a light weight distro like Puppy might just give you what you're looking  for.

---

### Post by dcrocker2 on 2013-10-29
Thanks Mike, I hadn't heard of Puppy Linux. I'll see if I can boot it from CD.

---

### Post by dcrocker2 on 2013-11-02
I downloaded Puppy Linux (the Slackware build without PAE) and it runs fine on my old laptop. I can browse with Firefox and read PDF datasheets using the supplied PDF viewer.

Now I just need to get to to boot from hard disk so that it boots faster - but I've already found the info on how to do that.

Mike, thanks again for your suggestion!

---

