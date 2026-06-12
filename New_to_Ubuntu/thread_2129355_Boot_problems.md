---
title: "Boot problems"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by CadMasterAdam on 2013-03-26
did dual boot full install
then i used boot manger to format the windows side

now wont boot

only boot with live USB key.

but i need to recover my pictures on other partition.

how can fix the ubuntu i already installed? like repair MBR?

thanks! help please.

---

### Post by carl4926 on 2013-03-26
When you say you can only boot with the USB, you mean that it boots the installed system or it just runs the Live system?
This matters, because some people have written grub to the USB. But it doesn't sound like that from what you said.
It sounds like you mean you can just boot the live USB

Also, did you just format windows or did you delete any partitions?

---

### Post by CadMasterAdam on 2013-03-26
correct i can only boot to the live USB

i'm not sure what i did to be honest. in gparted i tries to just boot to ubuntu but now won't boot.

but i can see a bunch of the partitions on there that were there . before i gparted.

i think my data is on /sda5  but not sure.  i just want to boot back into the unbutntu i actually installed because i know my pictures are in there...

 but i can't seem to find them in the live USB mode... does that make sense?

i can do screen shot of gparted if you want?

thanks!

---

### Post by carl4926 on 2013-03-26
You need to identify where Ubuntu is installed
You can examine the partitions from the live session. What I am about to post for you will fix it, but you need to change the partition number to match your install. In my example we use sda1

* Open a terminal and type


 ```
sudo fdisk -l

```

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt


 ```
sudo mount /dev/sda1 /mnt

```

    * Now mount the rest of your devices


 ```
sudo mount --bind /dev /mnt/dev

```

    * Now chroot into your system


 ```
sudo chroot /mnt

```

    *


      When that is done you need to run update-grub to create the configuration file.


 ```
update-grub

```

    *


      To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda


 ```
grub-install /dev/sda

```

And your done

---

### Post by carl4926 on 2013-03-26
And just to be clear. If you do examine your partitions, be sure to unmount them before proceeding with the above. Or just reboot the live session and then follow the directions

---

### Post by CadMasterAdam on 2013-03-26
thanks... i get this @ step 2

sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist

sorry i'm super noob

---

### Post by carl4926 on 2013-03-26
try again
You may have to start from scratch. Make sure you don't make any typos

One way to be sure is to copy and paste using your mouse. But remember to change the sda number to match your install

---

### Post by CadMasterAdam on 2013-03-26
chanks carl.

i'll pick this up tomorrow or something.  

i'm tired and not getting anywhere... would something like [this]("http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html") work for me thanks!

---

### Post by carl4926 on 2013-03-26
Check this

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by AndyOpie150 on 2013-03-26
+1 the Boot-Repair Disk.iso.
Saved me quite a few times.

Also: If you need the Windows partition to boot but it doesn't show up in the grub menu after using the Boot-Repair Disk then Burn Hirens Boot CD.iso to a CD.
Use the Mini XP or Windows 7 OS to run the chkdsk utility to repair missing files to allow boot up. Then use Boot-Repair Disk to repair grub and or MBR.

---

