---
title: "Just started using Ubuntu 8.04 and it’s great!"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by poetstorm on 2008-11-26
Hi, brand new here to the forum. About a week ago I was a solid Windows user. Me and my husband had rtied Red Hat years ago but it was about as east to use as a nuclear power plant. Well ,last week Bill Gates in his infinite wisdom (LOL) decided to install some sort of Genuine Advantage update. I do have a genuine install but apparently the update was not compatible with mylaptop hardware and it wouldn’t boot all the way and kept freezing. Tried a reinstall of XP b but discovered that SP2 was no longer supported! I thought I was up the creek when my husband suggested Ubuntu.

Let me tell you it did take a bit to install especially my wireless card but once it is working I am very, very impressed. I don’t know if I will ever go back. The gui interface is just as user friendly as Win XP with some cute new features. Mounting a USB drive or viewing a network one seems pretty straightforward and I’m not typing any commands into a terminal. Installing supported programs through Add/Remove is a piece of cake. For a non linux user, without much instruction by my husband I was able to figure out how to do everything I needed to. We even got Photoshop CS2 to work through Wine and I would have really missed that program. The only thing I can’t get working is Flash but I am sure with this forum it can be figured out. So I just wanted to shout it to the rooftops. Ubuntu rocks!

---

### Post by quinnten83 on 2008-11-26
have you tried going to the adobe website and download the .deb package there?
That worked for me.
you might have to deinstall the other flash programs like swfdeck or gnash first though. You can do that in Synaptic
system> administration> synaptic package manager.
then install flash.
it is strange though, because firefox should ask you for an install the moment you go to youtube.

---

### Post by poetstorm on 2008-11-26
Yep That's what I did. I went to youtube and followed their installation but It didn't work. I will try Synaptec tonight. A few other people recommended that to me.

---

### Post by FreewheelinFrank on 2008-11-26
You need to install ubuntu-restricted-extras for Flash and other proprietary bit and bobs:


[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by TheSerious on 2008-11-26
The restricted extras should solve your problem as well as give you some extra capabilities (DVDs, mp3s, etc.)

Type the following into a terminal:
```
sudo apt-get install ubuntu-restricted-extras
```
Be sure to say yes to all dependencies. It even works for 64bit =)

---

### Post by blazemore on 2008-11-26
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras -y
```
This installs Flash, MP3, DVD and a number of other things which aren't Free Software.

---

