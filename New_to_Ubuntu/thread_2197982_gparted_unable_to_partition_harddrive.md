---
title: "gparted unable to partition harddrive"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by 88390b08 on 2014-01-06
I was unable to find a thread dealing with this issue, but I am new so please forgive me if this has been solved already.
I wanted to partition the hard drive on my laptop to dual boot Windows 8. Right now I'm running Ubuntu 13.10. The problem is that when I open gparted, I can't select "new" from the rick click drop-down in order to create a new partition. Does anyone know what the issue is here? Is there another way or an easier way to go about doing this?

Thanks

---

### Post by Bucky Ball on 2014-01-06
Welcome. The partitions you want to manipulate must unmounted so booting from the Live media is the way to go. But to clarify, are you right clicking on free space and trying to create a new partition? You need free space to create a partition which means you may need to shrink an existing partition.

Perhaps attach a screenshot of Gparted to your next post (Adv Reply>paper clip icon>attach screenshot).

And Gparted is the easiest way to go about what you want to do .

---

### Post by oldos2er on 2014-01-06
Moved to Absolute Beginners.

---

### Post by 88390b08 on 2014-01-06
Yes, I am right clicking the free space and trying to create a new partition. However I am not able to select "new" (it's whited out). Because of this I am unable to create new partitions so I only have my /boot/efi, my root partition, and my linux-swap. This is going to sound ridiculous but I tried taking a screenshot but I can't take a screenshot while I am right-clicking. Also for some reason my Ubuntu software center has stopped working after I was looking at gparted (though I didn't do anything so I'm not really sure what happened) otherwise I would install gimp and go ahead and post a screenshot.

---

### Post by Bucky Ball on 2014-01-06
Applications>Accessories>Screenshot (or there should be a screenshot app by some other name there).

If you have /boot/efi partition and Win8 is installed, you need to be booting in EFI and install Ubuntu in EFI. That could be why you are having problems.

First you need to go to Win8 and switch of Faststart. You then need to reboot and switch off secureboot and fastboot and anything else you can spot in the BIOS and make sure you are booting the disk EFI. Some BIOSs allow you to boot just the optical drive or USB in EFI. 

Bottom line: check in the BIOS to make sure you are booting the Live media in EFI and not legacy or anything else. 

Just a few thoughts.

PS: You must select 'Something Else' at the partition section of the install when booting in EFI, NOT 'Alongside' option.

---

### Post by deadflowr on 2014-01-06
> **88390b08 said:**
> Yes, I am right clicking the free space and trying to create a new partition. However I am not able to select "new" (it's whited out). Because of this I am unable to create new partitions so I only have my /boot/efi, my root partition, and my linux-swap. This is going to sound ridiculous but I tried taking a screenshot but I can't take a screenshot while I am right-clicking. Also for some reason my Ubuntu software center has stopped working after I was looking at gparted (though I didn't do anything so I'm not really sure what happened) otherwise I would install gimp and go ahead and post a screenshot.

As stated, open the screenshot app and set a delay.That'll capture any menus or dropdowns.
5 seconds should be plenty of time to set screen as you want.

You could also take a normal shot of gparted, as is.

---

### Post by 88390b08 on 2014-01-06
Sorry, I wasn't clear about what I am currently doing. I only have Ubuntu 13.10 running on this laptop. I do not have Win8 installed. I was under the impression that how I would dual-boot Win8 alongside Ubuntu 13.10 would be to first create a partition using Gparted, then install Win8 on said partition. What I am getting from your response is that I need to first get Win8 and then move on from there (?).

I am unsure of what you mean by "booting the Live media in EFI". Sorry I am so new to this so I am struggling a bit with understanding the terminology.

Thanks so much for the help!

---

### Post by 88390b08 on 2014-01-06
[ATTACH=CONFIG]249271[/ATTACH]

Here is the screenshot of GParted.

---

### Post by Bucky Ball on 2014-01-06
Ok. All good. You can just leave free space at the beginning of the drive (if possible) for the Win8 install. It will format the free space and install itself fine. 

Win8? Think that needs about 40Gb but you might want to check. If you want to share data between Ubuntu and Win you are also going to need an NTFS data partition for that. 

As for the EFI stuff, you have a /boot/efi partition for Ubuntu already by the sounds of it which implies the disk was set in the BIOS to boot in EFI mode when you installed Ubuntu. As far as I know, you need to make sure it is set to boot EFI when installing Win8 in that case. If you've changed nothing, it would be, but you can check in the BIOS when you are setting it to boot from the Win8 CD.

I'm only just learning about the wonders of EFI (spin three times, do a little dance, mouth an incantation and cross your fingers) so hopefully someone with more knowledge of EFI will pipe up. A screenshot of Gparted will help a lot. ;)

---

### Post by oldfred on 2014-01-06
You need to make space for Windows, but it needs more than one partition. It also has a system reserved unformatted space in front of the first NTFS partition. It needs the efi partition also, but must use the same efi partition you already have so that is ok.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Windows will also make itself first in UEFI boot order, but you should be able to change that back. You still need secure boot off, fast boot off if you want to dual boot.

---

### Post by Bucky Ball on 2014-01-06
Ah, didn't see your screenshot there. You have a problem. The /boot/efi partition is in a good place, great, but there is a four partition limitation on the one physical drive. This is where you might find it complicated but I will try and keep it simple. Probably more straightforward than how I explain it. ;)

1/ You have three partitions on there already. You could shrink sda2 and leave, for example, 400Gb of free space between sda1 and sda2. You install your Win8 there and all good. But ... if you want an NTFS partition to share between the two OSs then that makes five primary partitions and that won't work. So,

2/ You can create an extended partition, three primary partitions and an extended. Fine. Inside an extended partition you can place as many logical drives as, theoretically, your hardware will handle. But ... and this is the main problem ... Windows won't exist inside an extended partition and your Ubuntu and /swap both exist as primary partitions already (although they will happily function on logical drives inside an extended partition).

3/ Have you spent much time setting up that install? If not, easiest may be to start over and install Win first (rule of thumb). Make a plan regarding how you want the partitioning to be.

Install Win8 on a 40-50Gb partition at the beginning of the disk;
Boot from the Ubuntu Live disk (install disk);
Choose 'Something Else' when you get to partitioning;
You will see your Win8 partition there, avoid it;
With the rest of the disk you can create one large extended partition;
Inside the extended partition put your Ubuntu install, /swap and NTFS data partition on logical drives.

4/ With your current setup, the only possibility is to shrink sda2 and leave a large area of free space (400Gb?) between sda1 and sda2, then install Win8 to that. Use the large Win8 partition as an OS/data partition which Ubuntu can then access. This is not ideal for a number of reasons, clumsy, and I wouldn't go there.

That easy!

* Ninja'd by oldfred. Check out some of the links in his post and they will also explain some of what I'm saying here.

---

### Post by 88390b08 on 2014-01-06
In case you can't view the other screenshot of GParted here is another. @oldfred I am unsure how to "make space for Windows" as I cannot unmount and create partitions (see the screenshot).

Sorry if this is frustrating or I am not being clear enough/giving enough information, thanks once again so much to all of you.

---

### Post by 88390b08 on 2014-01-06
Here is a screenshot of me being unable to shrink/resize sda2.

Alright, so maybe giving a little background might help. Prepare yourself for a barrage of failure:
 So this laptop came installed with Win8. I tried dual-booting Ubuntu 13.10 on it doing the typical disk manage partition >> unmount >> unpack Ubuntu onto a flash drive >> install Ubuntu after going to "try before installing" after booting from flash drive. After I did this, the installation went flawlessly until I shut my computer off fully. After I did this I was unable to boot Ubuntu (my computer would boot directly to Windows - normal, but my Ubuntu partition was not showing up when I F12'd). Anyway I tried the whole process over, but this time I screwed up in a major way and installed Ubuntu over Win8 (idiot idiot idiot idiot).
I spent a little bit of time researching what to do about this (not nearly enough, evidently) and reasoned that using GParted to create a partition for Windows from Ubuntu would be okay. Evidently that may be too difficult for someone with my limited experience.

Whenever I boot now, instead of booting directly to Ubuntu, I have to hit F12 and manually select Ubuntu to boot. This actually works fine and everything runs really smoothly, it's just that I figured that I would be able to dual-boot Win8 by using GParted in the same way that I was going to try and dual-boot Ubuntu by installing using the disk manage >> install from flash drive method. Am I completely wrong about this?

EDIT: again in response to your response @Bucky Ball:

I am completely unable to select any options/use GParted to edit any of my partitions. I can't shrink any of the partitions and sda2 is currently in use so I can't unmount it while still being able to use GParted (or am I wrong about this?). Is my only option here to install Win8 over Ubuntu and redo my Ubuntu dual-boot installation?

---

### Post by Bucky Ball on 2014-01-06
You are booting from the install disk and attempting to do this? (Sorry if silly question.) You can't change that partition, sda2, while you are running on it because it is mounted. Needs to be unmounted to resize or manipulate. That can't happen if the OS is on it.

---

### Post by 88390b08 on 2014-01-06
No, Ubuntu is installed on my computer so I am booting from the harddrive. I installed it from a flash drive. I am assuming I can't make any partitions then because my root partition is on sda2. Damn. So I probably have to start over and just install Win8 then, huh?

EDIT:
> I am assuming I can't make any partitions then because my root partition is on sda2.
This is the case right (from my GParted screenshot)? I don't want to make any more assumptions because that's how I got into this mess to begin with... :(

---

### Post by Bucky Ball on 2014-01-06
No, just boot from the USB! 'Try Ubuntu' and get to a desktop>open Gparted>shrink the partition. All partitions should be unmounted when running from the USB/LiveCD. Right click them in Gparted to confirm.

None of this tackles the point that oldfred and I are trying to make, though, which is that Win8 is going to need more than one partition, there is a four partition limitation on any one physical drive and you already have three partitions.

---

### Post by deadflowr on 2014-01-06
Try right clicking on the swap partition and select swapoff option.
That should allow/unlock the partitions.
If running on an installed system, reboot into a livecd, because you'll need the mountpoints unmounted.

Edit: Follow Bucky Ball's advice of using try.
Follow the above I stated if the parts have any lock keys next to the name.
Normally, I think it should have all the partitions unmounted, but once or twice I remember the swap was on so I had to turn it off before mucking about with the resize/move/whatever options.

---

### Post by oldfred on 2014-01-06
UEFI has to have gpt partitioning, and the limit is 128 partitions, all the same or no primary, extended or logical. And the 128 is a soft limit which can be reconfigured, by resizing partition tables.

---

### Post by 88390b08 on 2014-01-06
> **Bucky Ball said:**
> 
2/ You can create an extended partition, three primary partitions and an extended. Fine. Inside an extended partition you can place as many logical drives as, theoretically, your hardware will handle. But ... and this is the main problem ... Windows won't exist inside an extended partition and your Ubuntu and /swap both exist as primary partitions already (although they will happily function on logical drives inside an extended partition).

So the problem here is that because I already have Ubuntu existing on three of my primary partitions, I cannot install Windows because I only have one primary partition left, and Windows needs more than the one remaining primary partition?

> **oldfred said:**
> You need to make space for Windows, but it needs more than one partition. It also has a system reserved unformatted space in front of the first NTFS partition. It needs the efi partition also, but must use the same efi partition you already have so that is ok.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Windows will also make itself first in UEFI boot order, but you should be able to change that back. You still need secure boot off, fast boot off if you want to dual boot.

Thanks for the information! I am not really sure what you mean when you say that Windows must use the same efi partition I already have. Does this mean that I need to install Windows over my existing efi partition that I have already installed Ubuntu on?

> **deadflowr said:**
> Try right clicking on the swap partition and select swapoff option.
That should allow/unlock the partitions.
If running on an installed system, reboot into a livecd, because you'll need the mountpoints unmounted.

Edit: Follow Bucky Ball's advice of using try.
Follow the above I stated if the parts have any lock keys next to the name.
Normally, I think it should have all the partitions unmounted, but once or twice I remember the swap was on so I had to turn it off before mucking about with the resize/move/whatever options.

I selected swapoff but it did not unlock my partitions. Though I did boot from flash drive and was able to use GParted there. Actually I don't know whether or not selecting swapoff affected this because I selected it and then shut off the computer to boot from flash drive where I didn't have any problems using GParted.

> **oldfred said:**
> UEFI has to have gpt partitioning, and the limit is 128 partitions, all the same or no primary, extended or logical. And the 128 is a soft limit which can be reconfigured, by resizing partition tables.
If I install GRUB 2 and alter my partitions, will I be able to install Win8 without designating a primary partition? I was under the impression that Win8 needs three primary partitions to run, and I couldn't install it on any extended partitions or nonprimary partitions.

Once again, sorry for anything and everything I have made complicated or oversimplified. I really appreciate all the help!

---

### Post by Bucky Ball on 2014-01-06
> **88390b08 said:**
> So the problem here is that because I already have Ubuntu existing on three of my primary partitions, I cannot install Windows because I only have one primary partition left, and Windows needs more than the one remaining primary partition?

Yep. You need three primary paritions for Win, create an extended partition and put all Ubuntu and other parition in there on logical drives.

---

### Post by Impavidus on 2014-01-07
Read oldfred's post. The four primary partition limit is not applicable to you. You can just create the partitions, but first you must boot from your live usb and then shrink your /dev/sda2. There is free space on your drive (white), but no unallocated space (grey), which is what you need.

---

### Post by oldfred on 2014-01-07
And UEFI is not like BIOS. With BIOS there is only one boot loader in the MBR and you only boot that system.

With UEFI the efi partition has a folder for every system you install. So both Windows & Ubuntu will have folders with boot files and from UEFI menu you can choose which to boot. Grub will also let you choose to boot Windows, Windows will not let you choose Ubuntu. And Windows will often try to reset itself as first in UEFI default boot order.

---

