---
title: "running from live cd"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by skiddly on 2008-11-14
Hi getting more and more confused,i want vista on one hd and ubuntu on other,i did have ubuntu as stand alone and then inserted new hd and had to disconnect the ubuntu one till windows was restored on new hd,now i have asked how to get both working but couldnt understand the answer i had to disconnect one to get other to work went to my local pc shop and they say because vista is the original os you can not run another from a seperate drive,surely there must be a way and in easy (idiot proof)step by step instructions to achieve this, as a last resort if i just run from live cd is there any way to save changes i make ie to installed progs via add remove etc. ty col

---

### Post by Chesamo on 2008-11-14
First: punctuation, line breaks and capitalization are your friend.

Next: set your BIOS to boot from the disk that has Ubuntu installed on it. After you've done that, you have to configure GRUB (the Ubuntu bootlader) to see both drives as bootable, and mark them appropriately. A useful tool for this is called GRUBconfig. You can download GRUBconfig [_here_](http://freshmeat.net/projects/grubconfig/), or you can use [_RIP Linux_](http://rip.7bf.de/current/) (which is a boot disk that has GRUBconfig preconfigured).

---

### Post by aeiah on 2008-11-14
on the whole its good practice not to listen to most people who work in pc shops about software when linux is concerned. same goes for hardware if you're asking about linux compatibility although they tend to know what they're talking about with concerns to general hardware info.

having both OSs on different drives is a wise way to do it, although an even better way would be to have the linux swap on the windows hdd and the windows pagefile on a partition on the linux hdd, but that's unnecessarily complicated if you're just starting out. anyway, you shouldnt have any problems with the solution posted but if you do mess everything up, rest assured that if you reinstall ubuntu now that windows is installed, ubuntu will automatically detect vista on the other hdd and add it as an option to the boot menu.

---

