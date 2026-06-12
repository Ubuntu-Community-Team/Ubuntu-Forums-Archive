---
title: "No Windows 8 option after boot-repair"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by jchiso on 2013-01-18
I recently installed Windows 8 onto a partition that had previously housed XP, and burned a 64-bit version of secure remix and ran boot-repair.  I can now see and boot into my Ubuntu desktop, but the Windows 8 installation does not even appear on the grub menu.

[http://paste.unbuntu.com/1543563/](http://paste.unbuntu.com/1543563/)

---

### Post by Sukal on 2013-01-18
I've not had any experience with Windows 8, as I refuse to use it, but maybe try 

```
sudo update-grub
```

Just a thought.

---

### Post by oldfred on 2013-01-18
You have it, but it is calling it recovery for some reason.

But you may not see it on first grub menu page as you have too many kernels still installed. Time to house clean. You should see a tiny arrow on the right bottom of the grub menu box, that means more entries and you can just keep scrolling down. Windows is the last entry.

       Determine your current kernel, but I prefer to keep current & one older just in case:
uname -a
uname -r
In synaptic or software center search for linux-image to choose to purge old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by jchiso on 2013-01-18
> **oldfred said:**
> You have it, but it is calling it recovery for some reason.

But you may not see it on first grub menu page as you have too many kernels still installed. Time to house clean. You should see a tiny arrow on the right bottom of the grub menu box, that means more entries and you can just keep scrolling down. Windows is the last entry.

Thanks you  You are correct: selecting the Recovery Mode Windows entry does load Windows 8 successfully.  There was no tiny arrow on the screen, though.  I did the kernel cleanup and now I don't seem to have a defualt choice on the menu.  There's no countdown or auto-start ...

---

### Post by oldfred on 2013-01-18
Did you delete your current kernel?

If just deleting old kernels, it just should have updated and worked.

try:
sudo update-grub

---

### Post by jchiso on 2013-01-19
> **oldfred said:**
> Did you delete your current kernel?

If just deleting old kernels, it just should have updated and worked.

try:
sudo update-grub

I had deleted all but the two most-recent kernels.  Running update did not change anything.  Still no default or auto-start, no additional kernels displayed, Windows still shown as 'Recovery Mode'.  The startup menu only shows one Ubuntu kernel ...

---

### Post by oldfred on 2013-01-19
Whatever os-prober is seeing makes it think it is recovery partition. You can manually change it with grub customizer or just copy boot stanza to 40_custom and edit it to any name you want.

       HOWTO: Grub Customizer Updated for grub 1.99 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

    
       Copy the windows entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

    
If new entry at bottom of menu then works ok you can turn off os-prober and not have the incorrect entry:
       Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by jchiso on 2013-01-20
Still can't get this sorted out.  When I run the Customizer it indicates that the Ubuntu distribution is active as default, but it does not load at startup.  I also tried the manual edit but it indicated an error with the Windows entry ...

---

### Post by oldfred on 2013-01-21
If you copy an entry to 40_custom it has to be the entire boot stanza, so not leave off the last } also. I did that and with the new version it does not work. Also be sure not to remove first few default lines in 40_custom.

What does not load at start-up. You should get menu and then after 10 sec it will boot.

---

### Post by jchiso on 2013-01-28
> **oldfred said:**
> ... What does not load at start-up. You should get menu and then after 10 sec it will boot.

The Ubuntu distribution.  There is no 10-second countdown, no auto load.  The only way to get it to boot to an OS is to hit [Enter] ...

---

