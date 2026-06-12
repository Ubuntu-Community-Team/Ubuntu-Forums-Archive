---
title: "Triple boot problem"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by Stunt Double on 2012-05-01
I can't boot into Xubuntu 12.04 when installed as a third operating system. 
On this computer, I first installed Ubuntu 12.04 with Classic and Xubuntu shells. All OK.
 I then installed Ubuntu 10.04.4. All OK with dual-boot. 
Finally, I installed Xubuntu 12.04. The auto partition (side-by-side) was used and the installation seemed to complete successfully. After I removed the installer CD and attempted to restart, I got a black screen with the message:
error: no such partition
Grub rescue>

In the past, when I got this message with a dual boot, I would run a 7-part script posted by Cariboo907.
   1. sudo mount /dev/sda6 /mnt
   2. sudo mount -o bind /sys /mnt/sys
   3. sudo mount -o bind /proc /mnt/proc
   4. sudo mount -o bind /dev /mnt/dev
   5. sudo chroot /mnt
   6. grub-install /dev/sda
   7. update-grub
I had to do this whenever I installed an updated kernel.

Running the script this time allowed the grub screen to come-up with ALL the operating systems listed.
I AM able to boot into Ubuntu 10.04 and 12.04, However, trying to boot into Xubuntu produces this message on a black screen:

error: no such drive: 2af0929c-e8ce-4ef8-9004-c28f75c3e17a
error: no such partition
error: you need to load the kernel first

   I used Gparted to check the partitions. They are all there except that a third swap partition has not been created.

With no workaround, I removed the Xubuntu installation and tried again.
This re-install produced the same result.

Is there a script that will make this work?

Thanks

---

### Post by PhantomTurtle on 2012-05-01
I've never seen anyone triple boot with all the OS's being Ubuntu. Nevertheless you can try to repair GRUB by using a live CD. Here are instructions: [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). If you want Unity and XFCE just install the xubuntu-desktop package in Ubuntu. That would be much easier.

---

### Post by oldfred on 2012-05-01
I have one or two installs :) in my sdc drive, see attached. Which install do you want to be the grub2 boot loader in the MBR. It should be the one you expect to boot the most but you can easily update, later if you want.

I prefer to partition in advance, and keep / (root) smaller. Then it will reuse an existing swap. I have all non-system type data in separate data partitions. Although I just did another install to see what an auto install does. I just let run and it just found the unallocated in sdc and created another swap. 

Best to have this in your working install or as a liveCD, so you can run the boot info script to know where everything is installed.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by Stunt Double on 2012-05-01
Thank You for your responses.
I did try Boot-Repair but without success. I still get the same error message. 
My plan is to download the Xubuntu.iso again and burn it on a separate computer just to eliminate the possibility that either the .iso or burner is at fault. I'll then re-install.

---

### Post by Rex Bouwense on 2012-05-01
I have a friend who has created partitions so he could have Ubuntu, Kubuntu, Xubuntu, Edubuntu, and Lubuntu on the same computer.  He hasn't had a problem but then again you can only have on open at a time.  I believe that he did it just to see if it could be done.

---

### Post by Stunt Double on 2012-05-01
Still no luck with the re-burn and re-install.
Same error messages. This time I used Boot-Repair right away. Same problem.

I had been thinking that it could be a hard drive issue but the installs were done on different parts of the drive so that is ruled out.

Thanks to everyone for the help.

---

### Post by oldfred on 2012-05-01
From Boot-Repair run the Boot-info and post the link to the report, so we can see your exact configuration and suggest corrections.

---

### Post by Stunt Double on 2012-05-01
URL:http//paste.ubuntu.com/961507/

---

### Post by oldfred on 2012-05-01
Boot script looks normal for three installs. You should be booting sda1 and the grub menu offers sda6 & sda10 as choices.

What is issue?

Pastebin entry not quite right, but posting the last part worked.

---

### Post by Stunt Double on 2012-05-01
The problem is that selecting sda10 doesn't work. It produces the black screen with the noted errors.
I have noticed in the last few minutes, that it may indeed be a hard drive issue. Normally, my hard drive is absolutely silent. But, when I attempt to boot into sda10, the hard drive chatters for a few seconds before the error screen appears.
At this point, I'll call it a hardware issue, but I don't understand how the boot problem can keep re-occurring despite the Xubuntu install being located on different parts of the drive.
At any rate, it isn't critical that I have Xubuntu on this computer.
Thanks to everyone for the help.

---

