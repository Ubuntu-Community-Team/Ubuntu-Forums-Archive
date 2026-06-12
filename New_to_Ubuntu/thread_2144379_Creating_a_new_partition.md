---
title: "Creating a new partition"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by pikman on 2013-05-11
I am running ubuntu 13.04 64bit on my 128gb SSD. I want to create a partion on that drive, with just enough space to run windows xp 32bit. Is there a tut on how to do this, or, can someone please help me with this?

---

### Post by carl4926 on 2013-05-12
You'll probably regret even doing it
You should post for us a gparted screen of your SSD
And is the SSD the boot drive and are there other drives?

---

### Post by nsync on 2013-05-12
you can install Gparted using ubuntu software center and you  will be able to create a partition..

---

### Post by pikman on 2013-05-12
The ssd is the boot dive, and I have 2 others that are storage drives, but sats hdd's.

[http://i39.tinypic.com/2zq4u3r.png](http://i39.tinypic.com/2zq4u3r.png)

Why would I regret it?

---

### Post by carl4926 on 2013-05-12
Whatever you do - make sure you backup stuff you need
Regret... Because XP sucks. Well it was a good OS but it's so history now.

If it were me, I'd want to start again and I'd wipe the drive. Create my partitions in Parted Magic > Install XP > Re-install Ubuntu

But as it is
You would have to shrink sdc1 from the right.
And create space to make a NTFS Primary and Install XP to that Partition.
Afterward you will need to repair grub (I would use the Ubuntu disc to chroot the system)
Not sure if adding the partition for XP will change the extended table numbers....Re: swap

---

### Post by pikman on 2013-05-12
hmmm...sounds complicated...lol but I have gotta learn. I only want xp, for some basic software anyways.

---

### Post by carl4926 on 2013-05-12
Why not use it in a VM
Virtual Box...

---

### Post by pikman on 2013-05-12
never used it. is it easy? I just need it for iTunes, really. will that work for iTunes, to put music on my nano?

---

### Post by carl4926 on 2013-05-12
Well, it's easy for me. But I've used it before. You need to install the version from here
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

And you need the Extension pack [http://download.virtualbox.org/virtualbox/4.2.12/Oracle_VM_VirtualBox_Extension_Pack-4.2.12-84980.vbox-extpack](http://download.virtualbox.org/virtualbox/4.2.12/Oracle_VM_VirtualBox_Extension_Pack-4.2.12-84980.vbox-extpack)
see [https://www.virtualbox.org/manual/ch01.html#intro-installing](https://www.virtualbox.org/manual/ch01.html#intro-installing)

---

### Post by carl4926 on 2013-05-12
You may also need to read
[http://download.virtualbox.org/virtualbox/UserManual.pdf](http://download.virtualbox.org/virtualbox/UserManual.pdf)

---

### Post by pikman on 2013-05-12
Thanks. will the iTunes work, though?

---

### Post by carl4926 on 2013-05-12
> **pikman said:**
> Thanks. will the iTunes work, though?
Absolutely it will

---

### Post by pikman on 2013-05-12
that's perfect, then! Thanks!

---

### Post by pikman on 2013-05-12
OK, so I was able to get VB running windows XP, and itunes installed, but I am unable to get itunes to detect my ipod. Is there something I have to do to detect usb ports?

---

### Post by carl4926 on 2013-05-12
You need to setup USB support and set it in the VM settings
Check the manual

---

### Post by pikman on 2013-05-13
I have. When I go to user groups, and check mark "[COLOR=#000000]use virtualbox virtualization solution", under advance settings, and close the window, it unchecks that box beside "[/COLOR][COLOR=#000000]use virtualbox virtualization solution". I have administration rights, and when I check mark it, it doesn't give me the "ok" option, so I just click the "x" to close it. I have googlde the ***** out of this, to no avail.[/COLOR]

---

### Post by carl4926 on 2013-05-13
I'm not using VBox hese days but IIRC
[COLOR=#333333]To use a USB device - Simply plug it in, launch Virtual Box but not the machine. Select the machine and then it's USB settings and add. When you click add it will show you a list of available devices on your  host, select what you require and proceed to start the Virtual Machine.[/COLOR]

---

### Post by pikman on 2013-05-13
Thanks for all the patience and the help. I was finally able to figure it out.

---

### Post by carl4926 on 2013-05-13
> **pikman said:**
> Thanks for all the patience and the help. I was finally able to figure it out.
Pleased to hear it

---

### Post by wildmanne39 on 2013-05-13
Hi, please use thumbnails or url for images, because many people have an slow internet connection and it can make it very hard for them to load pages with large images.
Thanks

---

### Post by pikman on 2013-05-13
No problem, and sorry. Used tinypic.com, and it said that the link I copied was for forums.

---

