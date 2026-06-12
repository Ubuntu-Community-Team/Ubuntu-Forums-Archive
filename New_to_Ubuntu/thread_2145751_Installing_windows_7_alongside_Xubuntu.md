---
title: "Installing windows 7 alongside Xubuntu"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-05-16
Hello my fellow Linux users, I would like to ask you for help.
I am running Xubuntu 12.10 alongside MS Windows Xp Sp3. I want to upgrade my Xp to Windows 7. Now the question at hand. I have C: partition which is NTFS partition and thats where my Ubuntu is installed as well, but in its own partition thats is ext4. Will my Xubuntu be erased as well if I delete or upgrade my Windows? 

Thanks. :D

---

### Post by Mark Phelps on 2013-05-16
Unless you have TWO copies of Ubuntu installed, it can not BOTH be in C: (NTFS) and a different Ext4 filesystem partition -- it has to be one or the other.

If it is installed inside the NTFS partition, there will be a root.disk file.  If that file is there, overwriting XP with Win7 will likely corrupt that file and render Ubuntu unusable.

If that file is not there, the installation of Win7 over XP will not affect the Ubuntu installation, although it will remove GRUB from the MBR -- requiring that you reinstall GRUB to be able to boot back into Ubuntu:  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by LinuxUser666 on 2013-05-19
Ok thanks bro, appreciated your help.

---

