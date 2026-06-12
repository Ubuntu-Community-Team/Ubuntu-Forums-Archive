---
title: "Installing Sound card"
date: 2007-11-22
forum: Ohio Team - US
---

### Post by Tunene on 2007-11-22
I am very new to Linux and every time that I try playing audio cd using Amarok I get error message about the :
output engine is unavailable 
Xine Parameters
The I realized that no sound is installed on my system and I don't even know how to determine which sound card came with my computer (I am using Dell Latitude D830); but what I figured is that sound card is not installed on my system. Pls how can I go about resolving the problem?

---

### Post by linuxwizard on 2007-11-22
look over this
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Also have you installed all multimedia codecs you need?

---

### Post by Tunene on 2007-11-25
After removing the old installation of alsa package then I run  sudo apt-get install to install alsa utils package again and rebooted my system but unfortunately when the system is up-running the 
sudo aplay -l
aplay: device_list:204: no soundcards found...
Then I followed the instruction about manually compiling the driver by running
sudo apt-get install build-essential linux-header-$(uname -r) module-assistant alsa-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
build-essential is already the newest version.
E: Couldn't find package linux-header-2.6.22-14-generic
This is where I stopped when I got the error message. Pls what can I do?

---

### Post by linuxwizard on 2007-11-25
Look on this page for  Fixing sound on Gutsy. Hope this may help you. 

[https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD830](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD830)

---

### Post by anjoze on 2007-11-26
I just instaled Ubuntu 7.10 on my Dell Latitude D830 and then:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Reboot computer and it's perfect

---

### Post by Jack_Green on 2010-11-27
> **anjoze said:**
> I just instaled Ubuntu 7.10 on my Dell Latitude D830 and then:
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

Reboot computer and it's perfect


hello, friend. 
sudo m-a a-i alsa      is   not work for my ubuntu 10.10.
today I upgrade my  ubuntu 10.04 to 10.10, and then I remove the old kernel.
Now , my laptop has  no sounds at all.   I cannot install the soundcards hardware 
could you help me?
 if someone   could  help me solve the problem , please send  me an e-mail
[email]595528092@qq.com[/email]

---

