---
title: "how to acces other partions from ubuntu on dual boot hdd"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by carlf39 on 2008-04-29
installed xubuntu in a seperate partition on my laptop without any problems!  downloaded some applications and installed them via internet using add new software app.  Cool!!  But now would like to access some of the data files I had in the Windows (fat) partition, but ubuntu does not seem to know about the other partion, outside of the grub dual boot to start either system.  P.S. windows partition still boots up a-ok.  This was a real easy installation so far!! Just need access to old files and I&#314;l be set.  Note: I am not Linux knowledable, but willing to learn!  Traditional windows user, Be patient please.

---

### Post by dangerpl on 2008-04-29
If you go to Places menu, your other partitions should be visible. Click once to mount, and again to open. That's how it works on my computer.

---

### Post by carlf39 on 2008-04-29
nope, not there...i find...carlf39...trash...desktop...file system...floppy drive...recent documents...no hd partions mentoned...

---

### Post by carlf39 on 2008-05-02
managed to piece together what was needed, from a number of other threads.

First find out how partion is defined by doing the command line ¨sudo fdisk -l" from a terminal session.  Second had to create a folder in media, for the windows partion identified in step 1, such as ¨media/sda1¨.   Do step 2 and all rmaining steps by typing ¨gksudo thunar¨ to start a file manager session.  This will set yoou up as ROOT USER, to access and modify system files.  Third backup /etc/fstab, because this needs to be modified with the information found in step 1 (copy, paste,rename).  Fourth modify fstab to associate the /dev/ info with the /media/ folder you defined in the second step, such as ¨/dev/sda1       /media/sda1     vfat    iocharset=utf8,umask=000 0 0¨ (use open with option and select text editor).  Save modifcations and restart.  When you get back up you´ll have access to your windows files through the /media/ folder your created.   

It appears that there is a tendancy to overcomplicate the process. Key is to be in ROOT USER mode to make system file modifcations.

---

