---
title: "I can't enter windows after installed ubuntu 8.04"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by amazingjxq on 2008-06-14
Yesterday i installed it on my laptop. This morning when i tried to enter windows it showed a blue screen and then rebooted. Several months ago it was ok to install 7.10. I don't know why. Need someone's help. Thanks.Maybe there's something wrong with grub or something else?

---

### Post by EtniesBMX on 2008-06-15
Did the blue screen say anything?

You may want to look into reinstalling Windows to the MBR to see if Windows works at all, and if it does, then reinstall GRUB. You can find instructions for these procedures on Google.

---

### Post by amazingjxq on 2008-06-15
That blue screen just splashed and i couldn't see anything on it.

---

### Post by cheesypoof on 2008-06-15
You might want to try restoring your xp bootmgr. Assuming you still have the xp install cd, boot it up, click repair, cmd prompt, and type these commands.

bootrec /fixmbr
bootrec /fixboot
bootrec /rebuildbcd

---

### Post by amazingjxq on 2008-06-15
I don't want to reinstall xp.

---

### Post by bumanie on 2008-06-15
In terminal > sudo fdisk -l from ubuntu or from the live cd. Are you sure you didn't overwrite xp?

---

### Post by amazingjxq on 2008-06-15
Yeah.I chose guided use largest continous free space to install it. I deleted disk f:

---

### Post by bumanie on 2008-06-15
You could try to get it back with testdisk or use ntfsundelete, which is one of the ntfsprogs tools, or use the ntfsundelete from Trinity Rescue Kit.

---

