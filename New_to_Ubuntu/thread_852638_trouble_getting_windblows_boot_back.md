---
title: "trouble getting windblows boot back"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by pcrussell50 on 2008-07-07
hi, i've been booting between windows on one drive and ubuntu on another drive using grub at startup to decide between the two.

yesterday, i installed xubuntu as well, and used it's partitioner to make a small partition for it out of my windows drive...only now, when i boot, the grub doesn't offer windows as a choice anymore, just ubuntu or xubuntu.  

as a precaution, i mounted my windows partition while in ubuntu and copied off all my important stuff to an external drive, in case i have to reinstall windows.  which i'm really hoping not to have to do.

any ideas as to how i can get windows to show up in grub again, so i can boot back to it?

-peter

---

### Post by Rocket2DMn on 2008-07-07
You can try reinstalling GRUB with the Super GRUB Disk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
That should detect the windows install.  It should also have repair options.

Alternatively, you can manually add the entry to GRUB's menu.lst file.

---

### Post by tagra123 on 2008-07-07
if you know which drive andpartition that windows is in you can edit
```

gksudo gedit /boot/grub/menu.lst
```


then find the end automagic line
```

### END DEBIAN AUTOMAGIC KERNELS LIST
```


add something like the following after that line 


```
title Microsoft Windows
root (hd0,0)
savedefault
makeactive
chainloader +1
```

NOTE:
hd0,0 = ide1 (master) partition 1
hd1,0 = ide2  (slave) partition 2

---

### Post by Ptero-4 on 2008-07-07
You need to add the windows entry (somethin like this) to your /boot/grub/menu.lst file in the *buntu that holds it's grub in the MBR.
```

title "Windoze"
root (hdX,Y)
chainloader +1
makeactive
quiet

```
And then type (on the same *buntu)
```
sudo update-grub
``` to update the boot menu.

---

### Post by pcrussell50 on 2008-07-08
> **Rocket2DMn said:**
> You can try reinstalling GRUB with the Super GRUB Disk - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
That should detect the windows install.  It should also have repair options.

Alternatively, you can manually add the entry to GRUB's menu.lst file.

I fiddled around with this and voila!  I fixed the problem.  It's also a great learning tool...i feel like i have a tiger by the tail, as i'm barely hanging on to what it has to teach me, but that's alright.  i like it.

-peter

---

