---
title: "Getting Rid Of Dual Boot Question"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by rigel4 on 2012-03-18
I have windows 7 and Ubuntu 11.10... Dual boot!
I have an NTFS Data Partition too.

My question is: I don't need Windows anymore, I only play one game, and that works good enough with Wine. So how would i go about keeping my Ubuntu Install , but getting rid of the Windows and data partition, and the using the disk space for Ubuntu?

I'm still quite noobish but can follow along if directed to do something.

Help would be appreciated!

---

### Post by oldos2er on 2012-03-18
Moved to Absolute Beginner Talk.

---

### Post by rigel4 on 2012-03-18
For those of you in a similar situation I think I have found the answer!

[http://askubuntu.com/questions/784/how-to-i-remove-windows-but-keep-ubuntu](http://askubuntu.com/questions/784/how-to-i-remove-windows-but-keep-ubuntu)

I didn't Install with WUBI, just a normal Install.

---

### Post by jerrrys on 2012-03-18
Whats happens if you change your mind?  Reduce windows to minimum required space and keep it.

---

### Post by Gleichsnerd on 2012-03-19
> **jerrrys said:**
> Whats happens if you change your mind?  Reduce windows to minimum required space and keep it.

Because Ubuntu's open source, fully tweakable nature, there's always a high chance that you may be trying to manually change a video card driver and completely kill your system.

I strongly recommend what he said. Just uninstall as much as you can from your Windows install, shrink it in Ubuntu, and sit back and enjoy the games.

If you're absolutely set on getting rid of Windows though, you can delete the Windows partition through a partition manager in Ubuntu, resize to occupy the space or whatnot, and manually delete the GRUB entry for your Windows OS if you're really into aesthetics.
Here's a link to a video on deleting entries:
[http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/](http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/)

Happy Ubuntu!

---

### Post by Mark Phelps on 2012-03-20
If you want to retain Win7 but minimize the space it takes, do NOT shrink it in Ubuntu, that is, if you want it to remain bootable.  Linux utilities can corrupt the Windows filesystem during shrinkage.

Better to shrink it using the Win7 Disk Management utility.  It will limit the shrinkage, but it won't damage it.

---

### Post by varunendra on 2012-03-20
> **jerrrys said:**
> Whats happens if you change your mind?  Reduce windows to minimum required space and keep it.
Or even better, just create a set of so called 'Recovery Discs' from Win7's "Backup & Recovery" option in control panel, label & keep them somewhere safe, then simply use gparted to delete the win+data partition and create new ext4 ones in the recovered space.

I tried that 'create recovery discs' option once for a friend, and it took 5 DVDs (the common 4.7GB ones) to write the whole backup upon. Given the cost of DVDs, I think it should be the best and safest option for you.

---

