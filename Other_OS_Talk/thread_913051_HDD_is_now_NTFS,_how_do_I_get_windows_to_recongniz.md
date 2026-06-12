---
title: "HDD is now NTFS, how do I get windows to recongnize it?"
date: 2008-09-07
forum: Other OS Talk
---

### Post by PsychedelicWonders on 2008-09-07
Alright I have formatted my ext3 to ntfs. 

Now how do I get windows to see it and allow me to access all data saved on that hdd?

---

### Post by smoker on 2008-09-07
hi, is this to install xp? did you make the partition a primary partition, and mark it as 'active'?

if just to view the files, you may have to go into 'computer management' via control panel, and designate a letter for the drive, ie, D: or E:, whatever.

---

### Post by PsychedelicWonders on 2008-09-07
I dont think so....?

I need help from the begining.

Right now, this hdd is mounted in linux.

I need steps from the very begining on getting windows to see and use it.

---

### Post by fiddledd on 2008-09-07
Just reboot and select Windows from Grub. Windows will just mount it. Unless I've got the wrong idea about what you are trying to do.

---

### Post by smoker on 2008-09-07
not sure exactly what you mean, do you dual-boot, and you want a previous ext3, but now formatted ntfs partition viewable in windows when you boot windows, or are you using a virtual machine with windows running on top of linux?

---

### Post by PsychedelicWonders on 2008-09-07
doign a dual boot, so windows will just automatically see this hdd when I reboot?

---

### Post by smoker on 2008-09-07
yes, i think windows should see the partition ok, but if not, go into 'computer management' via the 'control panel', and you should see it there, and you may have to designate a drive letter for the partition, hopefully it should see it on boot and do this automatically though.

---

### Post by PsychedelicWonders on 2008-09-07
yes since I formatted to ntfs, windows seen it right away.

thanks guys.

---

