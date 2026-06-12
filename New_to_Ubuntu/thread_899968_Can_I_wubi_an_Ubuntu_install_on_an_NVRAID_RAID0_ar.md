---
title: "Can I wubi an Ubuntu install on an NVRAID RAID0 array?"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by Huzudra on 2008-08-24
I did a search of wubi and nvraid but returned no results.  

Can I wubi an Ubuntu install on an NVRAID RAID0 array?  my old system which had raid arrays was not ubuntu friendly, i couldnt even boot the livecd.  not sure if 8.04, wubi, and nvraid can be friends.

---

### Post by meanburrito920 on 2008-08-24
It should work, because the way Wubi works is that it fools ubuntu into thinking that it is running on it's own normal ext3 partition, while it really is just running as a 'file' on the windows partition. in effect, a virtual machine that isn't running on top of anything. I would back up your stuff and give it a shot.

---

### Post by Huzudra on 2008-08-24
> **meanburrito920 said:**
> It should work, because the way Wubi works is that it fools ubuntu into thinking that it is running on it's own normal ext3 partition, while it really is just running as a 'file' on the windows partition. in effect, a virtual machine that isn't running on top of anything. I would back up your stuff and give it a shot.

one more wubi question, i havent played with it much at all.

when i uninstall it from within windows, does grub vanish as well?

---

### Post by meanburrito920 on 2008-08-24
Wubi completely encapsulates the install. Everything that installed will be uninstalled, including GRUB.

---

### Post by Huzudra on 2008-08-27
its not working, rebooted in verbose mode and its just spitting stuff about
attempt to access beyond end of device
UDF-fs partition marked read only; forcing read only mount
Buffer I/O error on device fd0, logical block 0
end_request I/O error dev fd0, sector 0

so on and so on in a loop


array works 100% in windows, i guess wubi DOES NOT support nvraid yet :(


so i just tried on a hard drive NOT in a raid arry, install went fine in windows and after the reboot, however upon the 2nd reboot to enter linux for the 1st time....grub error 15: file not found. :( i was excited to actually be able to wubi linux onto my primary PC.

---

### Post by meanburrito920 on 2008-08-28
Hmmm.... Error 15 seems to be fixable. Try thi

[http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/](http://www.linuxquestions.org/questions/fedora-35/grub-error-15-431469/) although that is for Fedora, it should work.

if that doesnt work, just search the forums for grub error 15

---

### Post by Huzudra on 2008-08-28
well it just occured to me, i probably should have cleared the entry from the boot.ini that pointed to the first install, wubi maybe didnt change that and point to the right location?  i'll try from scratch this weekend maybe.

---

