---
title: "Installing Ubuntu from Windows failed after rebooting and selecting Ubuntu"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by SoWhat.lv on 2011-10-21
Hello!

Yesterday for first time I tried to install Ubuntu using windows installer. Installation went smoothly but after rebooting and selecting Ubuntu OS there was error, but it dissapeared so quick that I couldnt read it, but after that there was only a blinking "_" sign on the screen.

---

### Post by shadytv on 2011-10-21
im assuming you're using wubi.exe, have you tried uninstalling and reinstalling?

---

### Post by SoWhat.lv on 2011-10-21
Yes,I have tried that.

I managed to read error message which appears after selecting Ubuntu in boot menu:

**Try (hd0.0): NTFS5: error: "prefix" is not set.**

---

### Post by shadytv on 2011-10-21
[http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.com/2011/08/missing-rootdisk.html)
i did a little googleing see if this link helps a lot of people have referenced it
hope it helps :)

---

### Post by SoWhat.lv on 2011-10-21
Thanks, but it didn't help. My "D:\ubuntu\disks\root.disk" file isn't missing and error checking also didn't show any errors.


My feeling is that in some config file there is wrong path to Ubuntu files, but I have no Idea where Linux keeps such information. In windows it would be boot.ini.

Sadly I can't use USB Flash drive to install Ubuntu, because my laptop doesn't reckognise it, so Wubi is my only chance

Here is my disk configuration, in case it helps:
[IMG]http://dl.dropbox.com/u/2691093/untitled.JPG[/IMG]

---

### Post by SoWhat.lv on 2011-10-21
I also did some googling and found out that *"The message about the 'prefix not being set' is innocuous (happens on every 11.04 wubi install on every boot)."*

:(

---

### Post by varunendra on 2011-10-25
WUBI Megathread must be able to help you: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

If not, please download and run [boot info script]("http://bootinfoscript.sourceforge.net/") as described on the download page, and post the contents of the generated RESULT.txt file here.


**EDIT:**
Forgot the official WUBI Guide page: [https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

---

