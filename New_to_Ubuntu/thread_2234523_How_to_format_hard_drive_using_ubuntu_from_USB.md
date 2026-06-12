---
title: "How to format hard drive using ubuntu from USB?"
date: 2014-07-15
forum: New to Ubuntu
---

### Post by cracktor on 2014-07-15
Hello all!

Since i am new to ubuntu i need some help!
Just bought a brand new PC without windows, since its a waste of energy imo. But now i ****ed up within 1 day!
So i installed ubuntu 14-4. But i need to use windows some time (for sketchup, i am pro carpenter and need it!) So decided to create a dual boot system.
Installed XP pro after installing ubuntu. 
Tried to install ubuntu again but with partitions. Cancelled installation somewhere. Now nothing will install, only ubuntu from USB runs (using it right now)
Can't start or install any system now!

So what i want is to format the hard drive again and create a partition for ubuntu and for windows.

Any help appriciated!

Thx :)

---

### Post by nerdtron on 2014-07-15
Can't you boot windows from a DVD? Best way to dual boot is install windows first and then install Ubuntu.

Anyway, on Ubuntu there is program called GParted that work similar to partition editor of Windows. Since you don't care for any data on the hard drive now, you can try experimenting with gparted and layout the partitions that you want.

---

### Post by cracktor on 2014-07-15
ok burned GPart on a cd and going to work with that!

@ nerdtron: windows won't boot from the disc i installed it from earlier! I think its because i cancelled an installation of ubuntu somehow..

No data can be lost since its all new..

---

### Post by nerdtron on 2014-07-15
You burned GParted on CD? You can just boot ubuntu and open Gparted or install it from the software center (if it is not installed yet).

---

### Post by cracktor on 2014-07-15
Ok got it with gpart so far..

Another problem is that my windows XP disc won't boot.It say
s something like ' will now look your hardware configuration' and after that black screen nothin happens.
So making a new XP bootable USB now.

My ubuntu 14-4 bootable usb wont install ubuntu just run it from usb. No idea why!

So now i want to install XP first, after that ubuntu in order to create a dual boot system.
Would be nice to have some way to complete wipe out earlier installations! Because when i installed ubuntu and xp first time they worked fine. Problems started when i aborted an ubuntu instalation somewhere i shouldnt..

Thx for the help so far!

-edit: startup disc creator cant make a bootable usb says gnu/linux string error or some ****!

---

### Post by SuperFreak on 2014-07-15
Not sure if this is what you are looking for, If you use the GParted disc you can delete your NTFS partition and start all over again with the XP install and then Ubuntu install. You must realize that XP is not supported for security updates so it would be best if you do not use that OS online
You may need to reformat a partition for the XP install

---

### Post by Bucky Ball on 2014-07-15
Welcome. If you just want to start again and install Windows and Ubuntu:

Boot from a LiveDVD/USB. Delete all partitions with Gparted when at the desktop.

Install Windows. Reboot to make sure it is working.

Install Ubuntu. Reboot to make sure it boots and so does Windows.

Done.

PS: Please attach large images by 'Go Advanced' or 'Adv Reply' and use the paperclip icon. Spare a thought for those with slow connections and vision issues, among other considerations. ;)

---

### Post by yancek on 2014-07-15
In your original post, you indicate that you installed xp after installing Ubuntu.  Your GParted output shows one partition, ntfs which would be xp.  That would mean your xp install has overwritten the original Ubuntu.  Since you aborted the Ubuntu installation and don't remember at what point, there is really no way for us to know what was done.  I don't know why you would not be able to boot and install Ubuntu.  Do you get any warning/error messages when you try or does it just not boot at all?  Do you have it set to boot first priority from the usb/flash drive?

Windows may have a problem if non-windows boot code is in the mbr.  A simple fix might work.  Try booting Ubuntu from the flash drive, open a terminal and enter this command and hit the Enter key.  It will overwrite the master boot record.  Hopefully, this will help and since you have no data on the machine, should not cause any problems.  I don't know if you have multiple drives but the GParted output shows the partition on sda so this should work:

```
dd if=/dev/zero of=/dev/sda bs=512 count=1
```

---

### Post by cracktor on 2014-07-15
Ok now i installed XP (its xp pro and should be updated till 2018 or so..)
Next is to install ubuntu. I have an bootable usb stick with ubuntu 14-4 (worked earlier!)
But when i load it (boot usb) it loads ubuntu from usb but wont install on my computer!
When i click the icon install ubuntu on the desktop nothing happens.

Any thoughts?

---

### Post by Bucky Ball on 2014-07-15
Have you tried booting from the USB and clicking 'Install' from there rather than going to a desktop? Are you booting in UEFI or Legacy? How many partitions do you currently have on that drive? Is there free space on the drive?

---

### Post by yancek on 2014-07-15
> But when i load it (boot usb) it loads ubuntu from usb but wont install on my computer!

A standard windows install usually takes up the entire disk.  Did you manually create a partition or partitions for xp?  Boot the Ubuntu flash drive, open a terminal and post the output of:  sudo fdisk -l(Lower Case Letter L in the command) or open gparted and post an image of what it shows.  In all likelihood, you will need to shrink the xp partition with gparted to create room for Ubuntu.

---

### Post by cracktor on 2014-07-15
@ bucky ball It doesnt show this option anymore for some strange reason! It just opens the desktop and when i click the install ubuntu item there it doesnt react. 
Don know the difference between [COLOR=#000000] UEFI or Legacy. How do i find out?
I have the partitions as in the pic above.
All space (500GB) is free as it is a brand new PC.

@ yancek i entered the code, but i think i shouldnt have since windows was already installed at that moment. Did not start anymore since i entered your code! Installing it again right now.

So for now i will install windows, and after that try and reinstall ubuntu 14-4!


[/COLOR]

---

### Post by cracktor on 2014-07-15
Ok i made a new USB stick with ubuntu and now everything is fine.

Thank all for the great effort!

---

### Post by yancek on 2014-07-15
> [COLOR=#000000]@ yancek i entered the code, but i think i  shouldnt have since windows was already installed at that moment. Did  not start anymore since i entered your code! Installing it again right  now[/COLOR]

I'm not sure what you did but I'm sure entering the command I suggested didn't affect booting in any way.  All that command does is output to the terminal information on drives/partitions making no changes to anything.  Glad you got it working anyhow.

---

