---
title: "Ubuntu 12.04 AND ubuntu studio 12.04"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by bumbomaquides on 2012-07-30
Hi, 

I'm trying to install ubuntu AND ubuntu studio (no windows in this computer), and still can't figure it out, considering the different kernel they use.

So when I use the Intallation CD of ubuntu 12.04, and I have to do the partitions, I want to do something like:

Primary partition (sda1), ext4: Ubuntu 12.04, mounting point??
Logical partition (sda5), ext4: Ubuntu Studio 12.04, mounting point??
Logical partition (sda6), ext4: My files, mounting point /home
Logical partition (sda7): swap.

If the mounting point for the ubuntu studio partition is "/" (root) (as I've read [here]("http://ubuntuforums.org/showthread.php?t=1868852")), then what's the mounting point for the ubuntu primary partition? 

Since it is not possible to mount different partitions in the same mounting point.

About the device for boot loader installation, should I pick "/dev/sda", for both of the OS's?

Or should I pick "/dev/sda1" for ubuntu, and "/dev/sda5" for the ubuntu studio?

I understand from [here]("http://ubuntuforums.org/showthread.php?t=1868852") that after the installation, I have to manually use the terminal in the ubuntu 12.04 partition to run: sudo update-grub

And after that it will have to work.

So the only problem for me is knowing the mounting points.

Maybe it's piece of cake for the average user, but a newbie like me...

Thanks in advance.

---

### Post by levlaz on 2012-07-30
> **bumbomaquides said:**
> Hi, 

I'm trying to install ubuntu AND ubuntu studio (no windows in this computer), and still can't figure it out, considering the different kernel they use.

So when I use the Intallation CD of ubuntu 12.04, and I have to do the partitions, I want to do something like:

Primary partition (sda1), ext4: Ubuntu 12.04, mounting point??
Logical partition (sda5), ext4: Ubuntu Studio 12.04, mounting point??
Logical partition (sda6), ext4: My files, mounting point /home
Logical partition (sda7): swap.

If the mounting point for the ubuntu studio partition is "/" (root) (as I've read [here]("http://ubuntuforums.org/showthread.php?t=1868852")), then what's the mounting point for the ubuntu primary partition? 

Since it is not possible to mount different partitions in the same mounting point.

About the device for boot loader installation, should I pick "/dev/sda", for both of the OS's?

Or should I pick "/dev/sda1" for ubuntu, and "/dev/sda5" for the ubuntu studio?

I understand from [here]("http://ubuntuforums.org/showthread.php?t=1868852") that after the installation, I have to manually use the terminal in the ubuntu 12.04 partition to run: sudo update-grub

And after that it will have to work.

So the only problem for me is knowing the mounting points.

Maybe it's piece of cake for the average user, but a newbie like me...

Thanks in advance.

Just out of curiosity why are you installing both of theses in separate partitions. You can get all of the software in ubuntu studio to work in regular ubuntu and vice versa. This just seems like a lot of trouble for no reason. 

As far as grub it needs to be on the MBR (Master Boot Record) /dev/sda

This should be pretty simple. 

1. Make 2 partitions on your hard drive. 
2. Install ubuntu 12.04 on one partition and leave the other one alone  
3. Once the install is complete... install Ubuntu studio 12.04 and rather than manually editing the partition table select "install side by side" in the GUI installer. 
4. This should install both versions of ubuntu side by side. 
5. When you reboot you should see both Ubuntu 12.04 and Ubuntu Studio in the grub menu -- select which one you want and you are ready to go. 

Best, 

Lev

---

