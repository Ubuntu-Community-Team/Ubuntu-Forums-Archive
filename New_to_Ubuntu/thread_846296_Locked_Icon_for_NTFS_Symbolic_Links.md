---
title: "Locked Icon for NTFS Symbolic Links"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by andrewk8 on 2008-07-01
Set up Ubuntu 8.04 for dual boot (GRUB) on Windows XP machine.  Since I have a substantial amount of files in Windows on the NTFS partition and go back and forth between Linux and Windows, I'm keeping everything on the Windows partition.  I created symbolic links to folders like ***/media/New Disk/Documents and Settings/andrewk/My Documents*** and placed them in ~/.

When I boot Ubuntu, I am unable to access anything on the NTFS partition.  Nautilus shows a "padlock" icon on the symbolic links.  If I click on the NTFS partition (e.g. New Disk) TWICE, I can access the folders on the NTFS partiaion and the symbolic link is "unlocked".  Once unlocked, there are no issues with the symbolic links.  Ubuntu reads / writes to NTFS fine.

I'd like to avoid this work-around and get these symbolic links to auto-unlock / avoid being locked at boot time.

---

### Post by erginemr on 2008-07-10
You need to tell the computer to mount these drives at boot time and this is how you do it:

1. Install the package "ntfs-config":
```
sudo apt-get install ntfs-config
```

2. Run it with root permissions: 
```
Alt+F2 >> gksu ntfs-config
```

3. Enable both options and restart your computer.

This will make the necessary adjustments in the file "/etc/fstab", which is responsible for mounting the paritions at system startup.

---

