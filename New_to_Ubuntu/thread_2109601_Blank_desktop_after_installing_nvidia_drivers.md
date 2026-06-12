---
title: "Blank desktop after installing nvidia drivers"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by art_monu on 2013-01-28
I am using Ubuntu 12.10 64 bit and I my laptop has got Nvidia 525M switchable graphics card. My battery was not lasting longer and had a very high and constant fan speed. So I experimented with bumble bee and lastly downloaded graphics driver for my nvidia card from their site and installed it.
After restarting, everything seems fine till the login screen but as soon as I log in, I only get a blank desktop. The launcher and the top menu bar, everything is gone.
How, can I revert back or uninstall or do anything to get it working? I have installed and updated many softwares and I don't want to download them all again by reinstalling ubuntu.
Please help me.

---

### Post by frank604 on 2013-01-28
```
sudo apt-get install nvidia-current
```
it will say it conflicts with current nvidia drivers, do you want to replace? say yes madam!

It will remove the faulty ones and install the drivers from the ubuntu repo.

---

### Post by art_monu on 2013-01-28
I can run above command but I can't open terminal. It's just blank desktop. Also, installing driver from ubuntu repositories would involve connecting to the internet which I am not able to do as I don't have any icons or menu bars on the desktop. Please suggest some offline method, if any. Can't I just rollback to a previous date as I can in windows using system restore?

---

### Post by windscape on 2013-01-28
Hi,

I believe the NVIDIA installer has an uninstall option. To get to the command-line interface, try using Ctrl-Alt-F1.

---

### Post by frank604 on 2013-01-28
If you already had nvidia-current installed, it is in your computer.  I'm assuming you updated the nvidia driver from another website.  This means the package for nvidia-current is there to reinstall without internet.

As windscape has said, press and hold 3 buttons ctrl+alt+f1.  Login as normal. Then run the code I wrote earlier.  It should try to reinstall from the packages stored in your system.  It will say it conflicts with the current driver, do you wish to replace? say yes and reboot.

---

