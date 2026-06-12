---
title: "How do I remove windows from boot menu?"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by SwampShark on 2012-06-24
Hello all. First post. I'm a complete noob with Linux. I recently downloaded Ubuntu 12.04 and have been loving it. I want to remove the Windows Vista option from my boot options, or at least move Ubuntu to the top of the list. I haven't been able to  find any really comprehensive tips on this at all. I don't want to actually remove Windows from my laptop, just in case I ever REALLY need to run a Windows application. 

Help?

---

### Post by Paqman on 2012-06-24
Ubuntu normally is the first item on the list. Open a terminal and try running:
```
sudo update-grub
```
This will rebuild the list from scratch. Normally Linux installs will go first, and other OSes go after. The default is to boot the first OS on the list after a few seconds. If that's not what it's doing you can change the settings in the config file /etc/default/grub and force another update.

[Lots more info about Grub]("https://help.ubuntu.com/community/Grub2").

---

### Post by SwampShark on 2012-06-24
I've done the "update-grub" command. After changing one of the settings in grub2 and updating, it would say removing windows yadda yadda, but then when I restart my computer, BAM! Vista is first in the list on startup. Btw, maybe I should have mentioned I'm doing a dual-boot. I assumed it was implied by the question, but I like I said, I'm a total noob.

---

### Post by Paqman on 2012-06-24
Hmm, that's a little odd, but shouldn't be a problem. Count how many entries down the list Linux is (starting from zero, not 1), then edit the config file:
```
gksudo gedit /etc/default/grub
```
and change the "grub_default" setting. So if Linux is the second entry change the default from 0 to 1. Then update Grub again and reboot to see what happens.

EDIT: Hang on, did you use Wubi to install? If so you won't be able to remove Windows from the list because you're actually using the Windows bootloader (NTLDR).

---

### Post by Enigmapond on 2012-06-24
Install Grub-customizer and in there you have an option to set the first on the list. Removing Winblow$ from the list would be inadvisable as you will not be able to boot into Win.

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer && sudo apt-get update && sudo apt-get install grub-customizer
```

---

### Post by SwampShark on 2012-06-24
Thank you for that explanation. I tried to do that before based on something I saw in a random thread somewhere, but didn't really understand how it worked. I'll try that right now.

---

### Post by kansasnoob on 2012-06-24
No one asked if this is a true [dual boot]("http://www.psychocats.net/ubuntu/installing") or a [Wubi install]("http://www.psychocats.net/ubuntu/wubi") ;)

If it's a Wubi install and the OP follows some of the suggestions (s)he'll hate us forever :oops:

---

### Post by JKyleOKC on 2012-06-24
> **SwampShark said:**
> I've done the "update-grub" command. After changing one of the settings in grub2 and updating, it would say removing windows yadda yadda, but then when I restart my computer, BAM! Vista is first in the list on startup. Btw, maybe I should have mentioned I'm doing a dual-boot. I assumed it was implied by the question, but I like I said, I'm a total noob.I'm almost certain, from this description, that what you have is a "wubi" installation. If that menu is in all capital letters, you can strike out "almost" since the grub menu is in caps and lower case.

A "wubi" installation runs from inside Windows, and I'm not sure that there's any practical way to remove the menu item for Windows from being displayed (it's part of the Windows initialization process). A way exists, but it just might make your laptop totally unbootable so I'm not going to go into detail about it...

To achieve what you want, you need to install Ubuntu alongside Windows rather than inside of it -- but that gets quite a bit more complicated, especially if your Windows version is newer than XP. It requires re-partitioning the hard disk, and newer versions of Windows make that much more complex than it used to be.

My recommendation for now is to simply live with the boot-up menu, until you know whether you'll ever want to use Windows for anything. If you eventually decide to get rid of Windows, just back up your Ubuntu system to an external drive, and reinstall it to use the entire drive, then restore the backed up data and programs...

All of the suggestions that deal with "grub" apply only to an "alongside" (or "whole disk") installation and have no effect at all on a "wubi" install. Fortunately they don't hurt anything either, but they won't help either.

---

### Post by Mark Phelps on 2012-06-25
To see if yours is a Wubi installation, look for a file named "root.disk" in one of the NTFS partitions.  IF you find that, it is a Wubi installation.

In that case, boot sequence is being controlled by Windows, not by Ubuntu or GRUB.

To change that, type MSCONFIG in the Start area of Windows, when it opens, select the boot tab, and then select Ubuntu as the default.

When you reboot, Ubuntu will be the default -- but you'll still see the OS options menu.

---

### Post by SwampShark on 2012-06-26
Mark Phelps: I went into the start area of Windows and went into the boot options like you said, but the only option there is Windows. Am I crazy? I must be missing something...

---

### Post by exodus_ on 2012-06-26
Pictures are worth a thousand words, so does your boot screen look like [this]("http://www.google.ca/imgres?imgurl=https://wiki.ubuntu.com/WubiGuide%3Faction%3DAttachFile%26do%3Dget%26target%3Dboot-screen.jpg&imgrefurl=https://wiki.ubuntu.com/WubiGuide&h=287&w=440&sz=17&tbnid=25YB2TZzEzv-BM:&tbnh=78&tbnw=120&zoom=1&usg=__mdMB41Q5-PdKOlrTp-h57eGLH2M=&docid=1L4_Nb852vWPRM&sa=X&ei=On_qT4OMKKjF0AHLwtWwBQ&ved=0CFQQ9QEwAA&dur=358") or does it look like [that]("http://www.google.ca/imgres?imgurl=http://files.cyberciti.biz/ssb.images/uploaded_images/grub-single-user-mode-select-kernel-763178.png&imgrefurl=http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/&h=400&w=720&sz=7&tbnid=pLq0tpUlptUi_M:&tbnh=67&tbnw=121&zoom=1&usg=___nEOC7O1Ob3NVsn_tl-KTOu-EOY=&docid=ognIhJ20Cb7_hM&sa=X&ei=xn_qT9CEE6H10gG5ycDzBQ&ved=0CFgQ9QEwAA&dur=883")?

If it's "this" you're on wubi, if it's "that" then its grub we need to look at.  Also the version number will likely be different, I just did a real quick search for those images.

Hope to be able to help :)

---

