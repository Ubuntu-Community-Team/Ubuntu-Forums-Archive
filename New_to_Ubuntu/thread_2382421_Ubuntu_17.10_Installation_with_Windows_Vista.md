---
title: "Ubuntu 17.10 Installation with Windows Vista"
date: 2018-01-13
forum: New to Ubuntu
---

### Post by Kusho on 2018-01-13
Hi I built a new AMD Rizon7 pc but used an older 1 TB 7200 hd that still had windows vista on it.  I chose to keep vista but vista quit working with the motherboard upgrade.  It wants me to boot off of my vista disk and fix the vista install.  Problem with that is when I boot of my vista disk it will not detect my keyboard or mouse.  I also bought a new wired usb keyboard and mouse but vista disk won't detect those either.  I don't want help with that as this is not vista support which no longer exists.  I just want to delete the vista partition and use the whole hd for ubuntu.  Is that possible without reinstalling ubuntu?  I've been using it for a while and would rather not have to reset everything up.

Thanks in advance for any support.

---

### Post by cruzer001 on 2018-01-13
It can be done, but chances are you will grow old and gray waiting for it to happen.

Vista is probably the first install meaning you would have to expand Ubuntu forward on the HDD.  Which is a very lengthy process and one prone to failure.   Not to mention that your system will no longer boot after this and you will have to restore the boot process (grub) using the live DVD (or at least thats what I would do).

I think easier/safer just to backup your files and reinstall.

May even consider creating a separate "Home" partition.

Its late and I'm out of gas :) so maybe you could google that.

Good night

---

### Post by Kusho on 2018-01-13
Yes Vista was the first install.  Okay so not possible.  At least not practical.  Thanks for the input.

Second question if anyone reads past first question.  If I buy a copy of Windows 10 will I have to reinstall Ubuntu after i install that also?  I want Ubuntu to be the main boot option but I would like the option of booting into windows to do a few things I can't do in Ubuntu.  Can I install Windows 10 into the partition Vista is in now or will it be a clean install for windows 10 then adding Ubuntu on top of that.  Basically my question.

---

### Post by westie457 on 2018-01-13
Hi, keep your ubuntu install media handy for what follows.
Install windows 10 into the vista partition.
After that boot your ubuntu media to live mode and use Boot Repair to fix Grub. 
If I remember correctly there is no fast boot setting to change when win 10 is installed to a MBR partition table hard drive. 
Also be aware of the 4 partition limit of the partition table.

Windows 10 will create a small partition for its boot files and a big one for everything else.
Be careful and double check everything step before committing to any change.

---

### Post by yancek on 2018-01-13
You might boot Ubuntu and open a terminal and run either/both commands below which will show drive/partition information.  It would probably be possible to create another Linux partition for data for Uuntu but without details, no way for anyone to know.

```
sudo fdisk -l
sudo parted -l
```

Lower case Letter L in both commands.

---

### Post by Kusho on 2018-01-13
I'm good with the answers I got.  Thanks for all the input.  Marking this as solved.

---

