---
title: "Files have disapeared."
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Thiefot35 on 2011-09-14
Being completely new to ubunto as of last night i'm not sure where i have gone wrong.I have a desktop expansion drive that both me and my partner use.I can see the files on it when in ubunto but my girlfreind plugged the drive into her laptop and it wont show her files even though they are for windows.can i fix this fairly easily.

---

### Post by haqking on 2011-09-14
> **Thiefot35 said:**
> Being completely new to ubunto as of last night i'm not sure where i have gone wrong.I have a desktop expansion drive that both me and my partner use.I can see the files on it when in ubunto but my girlfreind plugged the drive into her laptop and it wont show her files even though they are for windows.can i fix this fairly easily.


Did you just unplug it or safely remove the drive from Ubuntu ?

Plug it back it in to your Ubuntu system and right click on it and choose safely remove to do a clean dismount

See if that is the problem before we dig deeper

---

### Post by Thiefot35 on 2011-09-14
I safely removed the drive beforehand.Have just booted win7 up on this pc and it shows the files as shortcuts.I think windows is having a hissy fit!!!.I've also been wondering wether i can run windows in ubuntu or vice-versa bearing in mind i have absolutely no program knowledge.I omly ask as both my ubuntu and windows are on the same drive and to switch between i have to re-boot.

---

### Post by haqking on 2011-09-14
> **Thiefot35 said:**
> I safely removed the drive beforehand.Have just booted win7 up on this pc and it shows the files as shortcuts.I think windows is having a hissy fit!!!.I've also been wondering wether i can run windows in ubuntu or vice-versa bearing in mind i have absolutely no program knowledge.I omly ask as both my ubuntu and windows are on the same drive and to switch between i have to re-boot.

Right click on one of the shortcuts and look at properties and see where it is pointing to ?


yeah you can using virtualisation. 

You can also run ubuntu in windows using virtualisation or WUBI

**Virtualisation**

Visit [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

and download latest version for your system (it is in the software centre but a bit out of date)

Also download the extension pack on the same download page

To make USB work (common question here) you need to add yourself to the Vboxusers group by doing the following:

sudo usermod -a -G vboxusers username 

Then  you are set to go

After installing your chosen OS in a VM you will need to install the VboxAdditions (not the extension pack, you should of installed this already as they are different)

The additions install inside the VM to add graphics functions and the like.

see here [http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html) for installing additions
[B]
WUBI[/B]

[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)


Have fun

Regards

haqking

---

### Post by Thiefot35 on 2011-09-14
Many thanks.Without trying to sound dense how do i go about the opening and/or implementing a sudo usermod..... so far my efforts have been a srictly point and squirt trying to get a feel for it.

---

### Post by haqking on 2011-09-14
> **Thiefot35 said:**
> Many thanks.Without trying to sound dense how do i go about the opening and/or implementing a sudo usermod..... so far my efforts have been a srictly point and squirt trying to get a feel for it.


see here for information on command line usermanagement

[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

[http://manpages.ubuntu.com/manpages/intrepid/man8/usermod.8.html](http://manpages.ubuntu.com/manpages/intrepid/man8/usermod.8.html)

---

