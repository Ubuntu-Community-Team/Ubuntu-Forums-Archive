---
title: "Ubuntu won't boot when cloned onto identical machine."
date: 2012-08-10
forum: New to Ubuntu
---

### Post by acpuck1 on 2012-08-10
Ok, so here's the setup:

I created an image on machine A. I imaged it onto machine B. Machine B will not boot. No grub loader or anything. I put the HDD from machine A into B and it does not boot. Same results. I put the imaged HDD from B into the machine I created the image on: A and it works fine.

Is there something about Ubuntu that will only allow it to work on the machine it was originally installed on?

I called HP, where the machines were purchased from and they do not have a lock of any kind on the HDDs. They were meant to be imaged.

Is there a command or something I need to do to allow Ubuntu to run on another machine?

Also, is there anything I need to do to the image because the system is EFI?

To clone the machine I'm using Clonezilla. When I boot with a Live CD, the file system is all there along with the boot partition on the imaged Hard Drive.

When I try to boot the imaged HDD on a machine other than the one the image was created on, I get a blank screen with a flashing dash in the upper left corner.

---

### Post by vexorian on 2012-08-10
Define not boot, if you specify the error message or lack thereof it will be easier to diagnose.

One time it happened to me that when moving ubuntu from a machine setup to another, the swap partition's address changed (somehow it was not using UUIDs). So I had to boot with a live CD and find out what is going on.

Try using the live CD, and see if the file systems  were copied correctly. Verify with gparted that the partitions are identical. If all seems fine, try reinstalling grub : [http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/](http://www.howopensource.com/2012/05/reinstall-recover-grub-from-ubuntu-12-04-live-cd-usb/)

---

### Post by Ghost_Mazal on 2012-08-10
Sjoe. There are a few things that can go wrong with an image , but the fact that the original drive itself doesn't work either has got me stumped. That rules out about everything that can go wrong with a clone as it is the original.
 
So you have no error message or anything ?

---

### Post by vexorian on 2012-08-10
The original drive does not work either?

How did you clone the image?

This reminds me of a time I used the command line to clone the image. But I accidentally cloned the empty hard drive on the hard drive that contained the data... Because I mistyped the syntax. The command line tool is ruthless and won't warn you that you are cloning an empty hard drive and that the result is a hard drive containing data will be removed.

So, better use the live CD to verify that your partitions are still there.

---

### Post by acpuck1 on 2012-08-10
The live CD shows the system files and boot partition are on the hard drive.

I am using Clonezilla to clone these machines.

---

### Post by audiomick on 2012-08-10
> **vexorian said:**
> The original drive does not work either?

You might like to look at the original post again. As I understand it, both drives work in the machine that was used to make the clone, neither drive works in the second machine.

To answer a question from the OP: no, Ubuntu does not do anything to stop and install being used on a different machine. There would also not really be any point to that as the license under which it is released allows as many installs as you want on any machine that you want.

What occurs to me is this business that micrsoft are pushing through with the secure boot. I gather that is related to EFI. I can't say anything definite about that though, as I have been ignoring the whole thing in the hope it would just go away...

---

### Post by acpuck1 on 2012-08-10
So you don't think there's anything I can do in Ubuntu to get this to work. You think it's a Clonzilla issue?

---

### Post by audiomick on 2012-08-10
No, I don't think there is anything wrong with the clone. It works on the original machine, doesn't it? I'm more inclined to think that there is some reason why the second machine doens't like either of the drives. 

Have made really sure that the B machine is in working oder? Excluded the possibility that it has a fault that means it just wont read any drive?

---

### Post by acpuck1 on 2012-08-10
Yes I am sure it's not just B machine. I am actually trying to set up a computer lab so I tried cloning and swapping the drives of two other machines around.

---

### Post by oldfred on 2012-08-10
One of the users here who really knew gpt said you could not copy gpt partitions, but could copy entire drives, as gpt partitions have internal data and different partition table & backup partition tables that must be synchronized. But if new drive works in first system, copy must be complete and clonezilla did it correctly.

Is second system set to boot from UEFI not BIOS mode. It could be looking for boot info in MBR not efi partition? Any other difference in UEFI/BIOS settings?

---

### Post by acpuck1 on 2012-08-10
Both systems have identical BIOS settings and both boot using EFI. They are all fresh from the factory and out of the box.

I don't know much about EFI. Does it use the UUID in some way and that's what is wrong?

---

### Post by oldfred on 2012-08-10
If you go into UEFI menu does it show the drive? 

Then does it show the efi menu of systems to boot?

Someone posted this one their UEFI, but every vendor's UEFI menu is different.

Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

You be able to read efi partition from UEFI and it should show Ubuntu/grub as a choice to boot.

---

### Post by acpuck1 on 2012-08-10
The Boot menu does show the drive (on machine B). However it is not in the 'EFI Boot Sources', it is under 'Legacy Boot Sources'. It is labeled 'ST500DM002' (the name of the HDD). When I choose the drive it does not boot, same as above.

On machine A, in the boot menu under EFI Boot Sources, it says 'ubuntu'. Booting to it works. 'ST500DM002' Also shows up in 'Legacy Boot Sources'.

---

### Post by acpuck1 on 2012-08-10
So I guess my problem is that ubuntu isn't showing as EFI bootable on any other machines.

---

### Post by oldfred on 2012-08-10
The legacy boot would be the BIOS boot from the MBR. If just installed to efi partition then you should not have anything in the MBR.

If you plug in a USB flash with the efi boot partition on the non-working one does it at least show the flash drive as efi bootable?

Not that I think it will show anything run the BootInfo report from Boot-Repair.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

If it works on one system, report should show all normal entries.

---

### Post by acpuck1 on 2012-08-10
It shows the flash drive as Legacy.

On a hunch I installed Ubuntu 10.10 and it works on both machines A and B.

Thanks everyone for their help.

---

### Post by oldfred on 2012-08-10
Even if booting in BIOS mode you may want to format to gpt and create the efi partition as well as the bios_grub partitions. The efi partition has to be first and would give you the flexibility to change to UEFI booting in the future. But if always imaging drives then it will not matter.

---

### Post by cmcanulty on 2012-08-10
i have 10 identical machines and what caused trouble is you have to change to correct host name in 2 files I forget which files each computer has it's own name usually

---

### Post by acpuck1 on 2012-08-10
Haha, I knew it had to be something this simple. Thanks a lot!

---

### Post by bodhi.zazen on 2012-08-10
> **cmcanulty said:**
> i have 10 identical machines and what caused trouble is you have to change to correct host name in 2 files I forget which files each computer has it's own name usually

/etc/hostname and /etc/hosts

---

### Post by acpuck1 on 2012-08-13
Changing the hostname in those two files did not help. Still not grub. Still no boot. Ubuntu 10.10 works though...

---

### Post by oldfred on 2012-08-13
Is it a video issue? With only one system you do not get grub menu, so grub has loaded and starts booting, but then video mode or some other boot parameter is required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by acpuck1 on 2012-08-13
It is not a video issue. when I try to boot, instead of grub or any kind of splash there is a black screen with a flashing dash in the corner.

---

### Post by Hadaka on 2012-08-13
Sounds like old fred is on the right track, if machine A boots fine with both a&b
drives but neither in machine B, it is most likely a hardware issue causing the problem
try going into bios in machine b...shut down the eth/wireless card and see if it boots.
if not, swap out the video card from machine a to machine b and see if that works.
it may also be some jumper setting difference between the two, look closely at
everything between the 2 machines for any wire  or possible jumper difference, as
always, once solved, it will be something simple.
good luck

---

### Post by JKyleOKC on 2012-08-13
> **acpuck1 said:**
> It is not a video issue. when I try to boot, instead of grub or any kind of splash there is a black screen with a flashing dash in the corner.That black screen with flashing dash IS a video issue. Any number of things could cause it, unfortunately. Try oldfred's suggestions as a starting point, and you might also try switching to an alternate virtual terminal via CTRL-ALT-F2 or CTRL-ALT-F3. Since these do not attempt to launch the X Window Server, they just might bypass the problem and allow you to troubleshoot things using only the command line.

---

