---
title: "Upgrade crashed - need disk space back on a dual boot"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by dlm93436 on 2012-06-13
Ok, pretty funky message title - but.

I setup a dual boot windows XP/ubuntu 10.* on an old laptop. When I tried upgrading Ubuntu the upgrade crashed. Pretty sure it choked on the video card, it's an 8 year old pc and when I first tried installing Ubuntu it was 11.* and it didn't like the video card. Not a big loose since I plan on setting an Ubuntu only machine in the near future.

My question is about recovering the disk space from the Ubuntu installation. I do not have the product code for my windows xp cd so I can't clean everything off in a civilized manner. If I trash the grub setup I can't boot into windows.

There were two partitions created during the Ubuntu installation; a 1gb and a 22gb. 

Am I correct in assuming the 1gb is where grub resides and that I can repartition 22gb without killing grub?

Also, is there a utility I can run to see if a pc has the necessary hardware to run the current version of Ubuntu?

Thanks

David Morris

---

### Post by Mark Phelps on 2012-06-14
The problem you're going to run into is that GRUB is actually installed in TWO places.  A small part of the code is written to the MBR; the rest of the code is written to a Linux partition.  Both parts are needed to boot using GRUB.

If you remove or reformat the Linux partition containing the GRUB code, you won't be able to boot anymore.

---

### Post by mapes12 on 2012-06-14
I would try and clone or image the windoze partition off the machine first. Try this:-

[http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)

Once you've rescued it then you can start again.

EDIT: Here's something else that may help:-

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Mark

---

### Post by dlm93436 on 2012-06-15
thanks guys,

---

### Post by drs305 on 2012-06-15
You can try to restore the Windows bootloader via an Ubuntu LiveCD. Once it's restored and you know it works you can do whatever you wish with the Ubuntu installation. You can always reinstall GRUB to get the MBR pointing back to your Ubuntu partition.

If the Windows boot files are all intact and the boot flag is on your Windows partition, the following should restore the Windows bootloader. It assumes your Windows drive is 'sda'. Only run these two commands. It will request you run additional commands to fully install lilo, but do not do that. Note this will remove your ability to boot Ubuntu until your reverse the steps by writing Grub information back to the MBR. This would be done as part of a normal installation if you reinstall Ubuntu at a later date:


```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

