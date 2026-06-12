---
title: "Ubuntu 9.10 problems"
date: 2013-08-29
forum: New to Ubuntu
---

### Post by mike60 on 2013-08-29
Okay so basically i have a acer aspire one with ubuntu 9.10 on it, my first problem is that when starting up the notebook its takes me straight to the terminal page (no graphical log in at all) which shows at the top: ubuntu 9.10 mike-laptop tty1. Before i did have it. After trying to do an update then trying a load of commands to fix my problem but i think it made it worse.

My next problem which happened before the one above is when i tried to log in (on the graphical display where it shows my account name and that) i could log in then a black screen flashes and takes me back to the log in screen, so i cant even use the notebook at the moment.

Please help me!

---

### Post by mike60 on 2013-08-29
Someone please help

---

### Post by Impavidus on 2013-08-29
Wow, that's a quick bump. You may be a bit more patient.

9.10 is old and unsupported. Unless you've got a very good reason to stay with that version you'd better install a supported version, like 12.04 LTS (assuming you don't insist on the latest software). Troubleshooting unsupported releases is complicated as few people still remember them well enough, the repositories have been taken off line and no more updates are being released.

Anyway, it could be something very simple.In the terminal login, maybe you can check the owner of the files **.ICEauthority** and **.Xauthority**. When they are owned by root this may cause those symptoms. Chance ownership to yourself or delete them and the graphical login may work again.

---

### Post by eternal243 on 2013-08-29
Considering you aren't getting a graphical login, it might be that an update messed up the settings for your graphics card. Something similar has happened to me before and it is certainly fixable. 

However I would not spend the time required to fix such an old release if it isn't essential for you to keep using it for some reason. The best thing would probably be to boot from a live CD, then copy all essential files to an external device, a harddrive or usb-stick, then reinstall with the Ubuntu 12.04 LTS, which is supported up to 2017.

---

### Post by mike60 on 2013-08-29
if i do:
sudo apt-get update 
sudo apt-get upgrade
in the terminal would it change it from 9.10 to 10.04 or whatever?
because i dont have the CD or disc to do it like that...

---

### Post by mastablasta on 2013-08-29
what kind of hardware is it? if you want the old look and feel and if new version doesn't work too well on your maschine then try Xubutnu or Lubuntu (or better yet LXLE).

updates can make a mess if you use proprietary graphic drivers and don't disable them before updating.

edit: read here how to update end of life releases: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

update all the way to latest LTS.

EDIT2: in linux you can download the necessary files via terminal (even with torrent) and you can "burn" the image to USB using DD or CD usign some other terminal command. if you so wish ofcourse. fresh install would be better than upgrade, you would then have backup (system restore) live disk bot you should backup all important data before doing a reinstall.

---

### Post by eternal243 on 2013-08-29
> **mike60 said:**
> if i do:
sudo apt-get update 
sudo apt-get upgrade
in the terminal would it change it from 9.10 to 10.04 or whatever?
because i dont have the CD or disc to do it like that...

**sudo apt-get upgrade** won't upgrade your distribution, it can be done through the terminal, but if you have many problems in 9.10 those problems might still be present after the upgrade.

Don't upgrade to anything below version 12.04 since that is the long term support release and any earlier release is not officially supported.

I'm not confident enough in my skills to advice you on how to upgrade your distribution without a full reinstall. But I'm sure there are plenty of others who can help out. =)

---

### Post by mike60 on 2013-08-29
to be honest i just want it to work normally... and where im such a noob i have no clue what most of you are saying... i need a step by step guide what to do :/ and i can only go through the terminal as when i boot it up it always goes to.the terminal...

---

### Post by eternal243 on 2013-08-29
> **mike60 said:**
> to be honest i just want it to work normally... and where im such a noob i have no clue what most of you are saying... i need a step by step guide what to do :/ and i can only go through the terminal as when i boot it up it always goes to.the terminal...

Yes I know you can only reach the terminal, you stated that in your first post.

What we are trying to say is that a new install is always better than upgrading an existing system, and if you upgrade your problems might still be there. If you got an empty cd or usb-stick you can still download and copy the installation files necessary for a complete reinstall to that medium through the terminal. We could try to give you step by step instructions on how to do that.

If you have an old computer with low-end hardware, you should probably use lubuntu or xubuntu instead of the regular ubuntu release, this is because those are more lightweight and doesn't require as much in terms of hardware.

However, if you want to try to do a full distribution upgrade from 9.10 to 12.04 we can try to guide you through that as well, but it might not solve your problems.

Just trying to help to the best of my knowledge, and ask away if you don't understand! :)

---

### Post by mike60 on 2013-08-29
okay, so i did update and upgrade and now it still boots me to terminal but its running ubuntu 10.04, if anyone could it would be great to get a step by step guide in how to get the graphical view back and enabling me to log in using the computer (i have no other computers available so usb thing wont be available) appreciate everyones help btw.

---

### Post by dnemcanin2 on 2013-08-29
You can download .iso from terminal with **wget**[INDENT]wget  [http://releases.ubuntu.com/12.04/ubuntu-12.04.3-desktop-i386.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.3-desktop-i386.iso)[/INDENT]
 
insert USB into laptop and check drive letter with[INDENT]sudo fdisk -l[/INDENT]
 if you have only one disk then USB will probably be /dev/sdb
Then copy iso to usb with[INDENT]sudo dd if=ubuntu-12.04.3-desktop-i386.iso of=/dev/sdb
sudo sync
[/INDENT]
 
now you have bootable usb drive with live ubuntu 12.04

> **mike60 said:**
> (i have  no other computers available so usb thing wont be available
How then you using this forum??

---

### Post by mike60 on 2013-08-29
im using forum with my phone

GUYS, i installed xubuntu and it loads the graphical view! only problem is it wont let me type in my password when logging in... as if the keyboard isnt responding, any solutions?

thanks

---

