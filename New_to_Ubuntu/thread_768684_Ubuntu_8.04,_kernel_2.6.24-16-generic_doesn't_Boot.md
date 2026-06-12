---
title: "Ubuntu 8.04, kernel 2.6.24-16-generic doesn't Boot!!!"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by ALex! on 2008-04-26
Hi guys!

My Ubuntu 8.04, kernel 2.6.24-16-generic doesn't boot, but my Ubuntu 8.04, kernel 2.6.22-14-generic does!

What should I do?

---

### Post by ptn107 on 2008-04-26
So you upgraded then.  Make sure the following files exist in /boot

abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic
System.map-2.6.24-16-generic
vmlinuz-2.6.24-16-generic

Also check your /boot/grub/menu.lst file to make sure it's pointing to those files.  Here's mine:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=55738474-5892-47aa-b791-5b574f4f4901 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

Note: Your root device UUID will be different.

If your still having problems you may need to run update-initramfs and update-grub.

---

### Post by ALex! on 2008-04-26
> **ptn107 said:**
> So you upgraded then.  Make sure the following files exist in /boot

abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic
System.map-2.6.24-16-generic
vmlinuz-2.6.24-16-generic

 
how do I?

> **ptn107 said:**
> Also check your /boot/grub/menu.lst file to make sure it's pointing to those files.  Here's mine:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=55738474-5892-47aa-b791-5b574f4f4901 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

Note: Your root device UUID will be different.

If your still having problems you may need to run update-initramfs and update-grub.

```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

```
it's the same... isn't it?

---

### Post by ghost_ryder35 on 2008-04-26
remove "quiet" and "splash" from the end of the kernel line and under the initrd line.  then see what the error is on bootup and report back to us :)

---

### Post by ALex! on 2008-04-26
> **ptn107 said:**
> So you upgraded then.  Make sure the following files exist in /boot

abi-2.6.24-16-generic
config-2.6.24-16-generic
initrd.img-2.6.24-16-generic
System.map-2.6.24-16-generic
vmlinuz-2.6.24-16-generic



YES I HAVE THEM! :???:

---

### Post by ALex! on 2008-04-26
> **ghost_ryder35 said:**
> remove "quiet" and "splash" from the end of the kernel line and under the initrd line.  then see what the error is on bootup and report back to us :)

excuse me... i don't get you...

---

### Post by ALex! on 2008-04-26
my ubuntu 8.04 doesnt start
it hands with an error message saying

[12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1
[12.95975] ACPI: EC: read timeout, command = 128

---

### Post by ALex! on 2008-04-26
> **ghost_ryder35 said:**
> remove "quiet" and "splash" from the end of the kernel line and under the initrd line.  then see what the error is on bootup and report back to us :)

I've done this and there are several errors... how do I make a print screen of this or how do i copy this???

---

### Post by ghost_ryder35 on 2008-04-26
if you can boot into recovery mode (or use the live cd) you can mount the drive, go into the var/logs directory and post the relevant log files, or you could take a picture with a digital camera and post here :)

---

### Post by ALex! on 2008-04-26
my ubuntu 8.04 doesnt start
it hands with an error message saying

[12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1
[12.95975] ACPI: EC: read timeout, command = 128

---

### Post by ALex! on 2008-04-26
> **ghost_ryder35 said:**
> if you can boot into recovery mode (or use the live cd) you can mount the drive, go into the var/logs directory and post the relevant log files, or you could take a picture with a digital camera and post here :)

which log should I post?! there are way too many! :???:

---

### Post by ptn107 on 2008-04-26
Try adding pci=noacpi acpi=noirq to your kernel line in /boot/grub/menu.lst

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro quiet splash **pci=noacpi acpi=noirq**

This will disable the PCI IRQ routing in the new ACPI system.  It may help.

---

### Post by Cris(c) on 2008-04-26
I have the same problem...I've been trying all types of things (all those suggested in this forum) and so far: nothing...

---

### Post by ALex! on 2008-04-26
> **ptn107 said:**
> Try adding pci=noacpi acpi=noirq to your kernel line in /boot/grub/menu.lst

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro quiet splash **pci=noacpi acpi=noirq**

This will disable the PCI IRQ routing in the new ACPI system.  It may help.

thank you! but... what's this for?

---

### Post by ALex! on 2008-04-26
> **ptn107 said:**
> Try adding pci=noacpi acpi=noirq to your kernel line in /boot/grub/menu.lst

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f2ce2503-be68-41f0-a986-9224b7a68c66 ro quiet splash **pci=noacpi acpi=noirq**

This will disable the PCI IRQ routing in the new ACPI system.  It may help.

didn't work... :( :cry: but thanks! :mrgreen:

---

### Post by Solrac924 on 2008-04-26
hola!
i'm in the same boat. i've posted the same problem an hour ago.
when you boot your pc, you should see GRUB. highlight Ubuntu Linux & press E for edit. then highlight the line that starts with kernel /boot/vmlinuz-2.6.24-16... & hit E. that's when you add that extra stuff at the end.

---

### Post by ALex! on 2008-04-26
> **Solrac924 said:**
> hola!
i'm in the same boat. i've posted the same problem an hour ago.
when you boot your pc, you should see GRUB. highlight Ubuntu Linux & press E for edit. then highlight the line that starts with kernel /boot/vmlinuz-2.6.24-16... & hit E. that's when you add that extra stuff at the end.

didn't work :(

---

### Post by ALex! on 2008-04-26
Apparently there is no solution for this bug........ :cry:

---

### Post by Cris(c) on 2008-04-27
> **ALex! said:**
> my ubuntu 8.04 doesnt start
it hands with an error message saying

[12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1
[12.95975] ACPI: EC: read timeout, command = 128

Hi Alex,

    I had exactly the same problem as you: I couldn't boot using the  kernel 2.6.24-16 while the kernel 2.6.24-14 worked perfectly fine. I tried adding **noapic acpi=off** to the kernel line in /boot/grub/menu.lst (as ptn107 suggested) which enabled me to boot but killed my wireless network and my sound. However, I sort of realized that the problem is some sort of hardware compatibility (I'm new in this so no idea what the exact problem is). So, what I did was to boot using the kernel 2.6.24-14. From there I uninstalled the following package: **linux-ubuntu-modules-2.6.24-16-generic**. I then edited my menu.lst and deleted the **noapic acpi=off** from the kernel 2.6.24-16 line (I also deleted the quiet to see what was going on) and rebooted my system using this 2.6.24-16 kernel. Once there, I reinstalled the **linux-ubuntu-modules-2.6.24-16-generic** package and rebooted once again...and voila! now the system is working perfectly, except for the fact that my wireless network lid is off! (a minor cost after all)...

Hope it helps...

---

### Post by cmcfarland21 on 2008-04-27
>I'm having the same issue..  I just been using 14

What's the difference between 2.6.24-14 and 16?

---

### Post by Cris(c) on 2008-04-27
2.6.24-16 is the lastest kernel update. It is supposed to behave better than the old one (2.6.24-14) but so far it is been the opposite...

---

### Post by Jadephyre on 2008-04-27
the 16 Kernel is keeping me from booting the Live Environment... no Hardy for me if the Kernel is not swapped out with an earlier or later Kernel which irons out the obvious existing bugs.

---

### Post by AbEx on 2008-04-28
Same problem here.

Amd64 
Asus M2NPV-VM
2.6.24-14 works
2.6.24-16 does not work

Both clean install and upgrade install exhibits this issue.

Had this issue with older linux kernels and the ACPI=off fixed the issue. This was a workaround until I was able to perform a bios update to correct the issue. My bios has been updated since so this really should not be an issue anymore. However, the 2.6.24-16 kernel brought the issue back.

---

### Post by Solrac924 on 2008-05-03
my Hardy install with 24-16 never worked the first 3 days until i installed Gutsy (not sure what Kernal is used). worked fine. i updated with Hardy & everything was all good. two days later i rebooted & noticed there were 2 Ubuntu 8.04's: one with new Kernal & one with older. funny thing is, the newer one didn't work once during a cold boot. both seem to be ok now.:wink:

---

### Post by evkefalas on 2008-05-04
I keep having the same problem
i am really annoyed how is it possible an older version to work and a newer one to cause all these problems and it is supposed to be LTS
how did the developers not catch this one
and more seriously what would it say to a newcomer to linux?

---

### Post by Solrac924 on 2008-05-06
you know what, my 24-16 kernal failed to boot up twice now. it's just hit & miss. i guess i was wrong earlier. the 22-14 kernal, however, is very reliable & boots up all the way everytime. :?

---

### Post by Cris(c) on 2008-05-06
Still the same here. I can boot with no problems wih my 22-14 kernel but booting with newer ones (26-16 and 26-17) gives the same problems as you guys have described. Booting with 24-16 is random: sometimes it does it with no problems and others gets stuck with the same error ([12.959696] ACPI : EC : acpi_ec_wait timeout, status = 0, expect_event = 1 and [12.95975] ACPI: EC: read timeout, command = 128). With 24-17 is even worse: when I am able to boot I get no audio and no wireless! 

So, I finally opted for keeping my 22-14 kernel and wait until someone figures a way out of this...bad thing because it appears this problem is affecting lots of machines, not just mine...

---

### Post by Cris(c) on 2008-05-07
Hi everyone,

   Please, have a look at this: [https://bugs.launchpad.net/linux/+bug/191137](https://bugs.launchpad.net/linux/+bug/191137) It may be of some help...

---

### Post by thkoukas on 2008-07-20
hello, I have the same problem
in that thread you can see that people with the same NB have the same problem
[http://ubuntuforums.org/showthread.php?t=805746](http://ubuntuforums.org/showthread.php?t=805746)
It writes Initializing gfx code...
when I boot from 8.04 disk, so I had to update from 7.10... but it boots only the 2.6.22 and the 2.6.24 doesn't boot.....
Please I want your help!!!

---

### Post by Tankerdog2002 on 2008-08-23
Yea, this kernel has some serious issues with boot. 

In any event ... Here is a work around with some other options at the end of this tutorial.

Here's what you do.............

1. Hit F2, F12, F8 or whatever you need to do on your machine to get into boot setup/startup settings. 

2. Change your SATA from IDE to RAID. (You'll change it back later)

3. Make sure to edit your PC to boot up from CD/DVD. (You'll change that back later also.)

Reboot

Hit F6 at the 'Hardly Heron splash screen and choose ACPI=OFF, NOLAPIC
You should now be able to install Ubuntu 'Hardly Heron 8.04.

After install you will reboot and then do the following:

backup your menu.lst first by running: sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
(You can always restore it by running: sudo cp /boot/grub/menu.lst_backup /boot/grub/menu.lst)

Run this in terminal (konsole): 
gksudo gedit /boot/grub/menu.lst

When your menu.lst pops up on your screen do the following:

[[]][[]][[]][[]][[]][[]][[]][[]][[]][[]][[]][[]]
Look at the part that says something like:
## ## End Default Options ##
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=3d7e8feb-a28f-4a3d-a4ed-2f53e06c1890 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet
____________________________________________________________
Add the following to the kernel line:
 acpi=off nolapic noirqpoll
____________________________________________________________
it should now look like this:
## ## End Default Options ##
title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=3d7e8feb-a28f-4a3d-a4ed-2f53e06c1890 ro quiet splash acpi=off nolapic noirqpoll
initrd /boot/initrd.img-2.6.24-19-generic
quiet
[[]][[]][[]][[]][[]][[]][[]][[]][[]][[]][[]][[]]

Save the ...  /boot/grubmenu.lst ...  file and close it.

Now...reboot again.

Hit F2 (or whatever you need to do) at boot up and reverse the changes you made in steps 1. and 2.

Uhhh.....yes, you guessed it.....reboot again.

You're done.....for now at least.

Some other options to play around with are:
acpi=off noapic nolapic
irqpoll
noirqpoll
all_generic_ide
pci=nomsi
   

I hope this helps someone.

The bottom line here is that NO ONE should have to do this with brand spanking new PC's out of the box.   :confused: 
All of our machines that we tweaked are brand new from the factory. (HP, MALIBAL,and Dell)  Oh...BTW ...  for you up and coming cynics waiting in the wings to flame this post....we got our CD's from Canonical, not some burned ISO B.S. off the net. 

Nevertheless; this does not look good to newbies that are contemplating switching to Linux.

The Canonical guys really need to nail this coffin shut and keep the skeletons from getting into the closet in the first place.:lolflag:

---

### Post by ptn107 on 2008-08-24
> **Cris(c) said:**
> 2.6.24-16 is the lastest kernel update. It is supposed to behave better than the old one (2.6.24-14) but so far it is been the opposite...

The latest Ubuntu 8.04.1 kernel is 2.6.24-19.

---

### Post by dimethylsulfoxide on 2008-08-24
for all you dual-booters out there,

i have my laptop set dual-boot with vista/ubuntu. im pretty sure booting from supergrubdisk can get you past the "status=0, expect_event=1" "command=128" error no matter if you have vista or xp. to fix the problem for good, i switched to the vista boot loader (and for that there's a help link at the end).

first and foremost, to get past that "status=0, expect_event=1" stuff here's what i did:

1. at supergrubdisk.org i burned an .iso of supergrubdisk onto a cdrom.

2. booted from the supergrubdisk.

3. once booted, "english and help" -> "linux" -> boot linux.

4. i cant remember if i had to select the partition, but its pretty straight forward. anyway i was able to boot into linux without that status/event_expected annoyance...


to set up your xp boot loader, do your own searching on the web.

to set up your vista boot loader open up browser and go to [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4") and follow the steps there.

---

### Post by Tankerdog2002 on 2008-08-27
> **ptn107 said:**
> The latest Ubuntu 8.04.1 kernel is 2.6.24-19.

Actually this kernel isn't even the latest; nevertheless, these boot problems persist with 2.6.24-19 kernel as well.

---

