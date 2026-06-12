---
title: "iso's preprocessing and isohybrids"
date: 2015-05-22
forum: Programming Talk
---

### Post by bobbicat on 2015-05-22
I reported a bug for Gparted-live. Their iso file is isohybrid but only works for BIOS, it will not work for UEFI when a copy is made to a thumb drive. Apparently they do not know how to create a fully functioning isohybrid. I seem to have been seconded to find an answer.
I am not a programmer, coder or geek, but have been a user of a Kubuntu for many years. Is it possible to explain to me in layman's terms how to create an iso and then convert it into an isohybrid which will boot from a usb pen drive in both BIOS and UEFI modes? 
Gparted-live also complains of a recursive partition in the thumb drive version. It only appears to be the isohybrid part that is malfunctioning. I think the two problems are, the installation begins at sector0 and no proper funtioning of UEFI is enabled. I'm guessing that the parameters to create an isohybrid need to be set correctly.
I ask here because I use a Ubuntu based system, Gparted-live is Debian based and so is Ubuntu, but most of all, because Ubuntu can create a properly formed isohybrid in their distributions, so it must be possible.
The actual file I am working with is an AMD64 iso, on an UEFI based machine.
I have Googled and read a bit about iso's and preprocessing to create an isohybrid but I am in no way knowledgeable about any of this.
Is it possible to point me in the right direction?

---

### Post by sudodus on 2015-05-22
I'll try to help you, but I am not sure that I understand your problem.

There is a program called isohybrid, that you can run yourself. Use it to modify an iso file, that works when burned to a CD or DVD, but not when cloned to a USB drive. After the modification, the iso file can be cloned to a USB boot drive. I have used isohybrid many times.

But isohybrid has nothing to do with UEFI. You need other methods to make an iso file boot in UEFI mode.

On the other hand gparted comes with most Ubuntu and Ubuntu flavour iso files. So ***when you boot a DVD or USB drive with Ubuntu in UEFI mode, gparted is there*** (only one click away in Ubuntu's menu system). ***gparted*** comes with standard Ubuntu and I thought all Ubuntu flavours (in the live system).

---

### Post by bobbicat on 2015-05-22
I imagine that Gparted would be a part of the Ubuntu live distribution, but Kubuntu uses its own KDE based application, instead.
Gparted-live is a utility that boots from a CD as a standalone, in a similar fashion to Ubuntu live. When booted it presents a graphical interface that contains one or two utilities, including Gparted.
This standalone is based on Debian live and should present as an isohybrid capable of booting in BIOS and UEFI modes - similar to the way that Ubuntu live and Kubuntu live do.
However, although the CD version does work, dding the iso to a thumb drive creates errors and does not work properly.
I suspect that there is something in the setup of the hybrid that has not been covered.
I would like to work through the process. First to create a bootable iso from the files present on the Gparted live distribution. Then to apply whatever 'magic' that is necessary so that when it is dd copied to a thumb drive it will become a viable bootable object, in the same way that a bootable Ubuntu or Kubuntu iso can do.
I'm sorry I am not at all well versed in the vocabulary of programming, so my explanations are probably not good. I am sure that if Ubuntu can produce a bootable hybrid iso that will boot as (k)ubuntu Live from a thumb drive in both BIOS and UEFI, then that principle could be applied to the issue I have with Gparted live.
Thank you for your time sudodus.

---

### Post by sudodus on 2015-05-22
If gparted is not already there in Kubuntu, you can install it with the following command line in a terminal window 'konsole':

```
sudo apt-get install gparted
```

I think it is still easier than to re-make the Gparted-live iso file.

-o-

Anyway, you can run isohybrid, but if the iso file was already treated with isohybrid, I think it will be destroyed, and isohybrid works in-file, overwrites the source file, so make a copy and save the original iso file.

Example (I don't know the exact name)

```
cp -p gparted-live.iso gparted-live-isohybrid.iso

isohybrid gparted-live-isohybrid.iso
```

If this new file **gparted-live-isohybrid.iso** still does not work correctly, the problem is somewhere else, and it is probably easier to get help from the developer or maintainer of Gparted-live.

---

### Post by sudodus on 2015-05-22
The very easiest way might be to download a ***Lubuntu desktop 64-bit iso file*** and run it live. ***gparted*** will be there, and it works in UEFI mode if it is a current (supported) version of Lubuntu, 14.04 LTS or newer).

---

### Post by oldfred on 2015-05-22
Is even the Ubuntu live installer when dd'd to a flash drive bootable in UEFI mode?
I thought those were not partitioned. 
But then how does UEFI boot a DVD? That I do not know.

UEFI expects to find an /efi/boot/bootx64.efi on a FAT32 partition with the correct MBR or GUID code so it is know as the ESP or efi system partition.

       For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].

With gpt you use boot flag to assign correct GUID with parted or gparted. Or with gdisk you use code ef00.

Update, found this:
[https://wiki.freebsd.org/UEFI](https://wiki.freebsd.org/UEFI)
The approach for creating a bootable CD/DVD image for UEFI is to create a  FAT filesystem image containing your loader code as it would be laid  out in an EFI System Partition. This image is then attached to the  CD/DVD image as a non-emulation El Torito boot image. To make an image  that is bootable under both legacy BIOS and UEFI, the BIOS image is  placed first and the UEFI image is placed as an alternate. More  information can be found [here]("http://fedoraproject.org/wiki/User:Pjones/BootableCDsForBIOSAndUEFI"). 
[http://fedoraproject.org/wiki/User:Pjones/BootableCDsForBIOSAndUEFI](http://fedoraproject.org/wiki/User:Pjones/BootableCDsForBIOSAndUEFI)

---

### Post by bobbicat on 2015-05-22
>  [COLOR="#0000FF"]from oldfred:--[/COLOR] Is even the Ubuntu live installer when dd'd to a flash drive bootable in UEFI mode?

Yes it most certainly is - and has been for a number of releases. I have been installing that way for quite some time - burning CD's and DVD's is a thing of the past. This is why I thought that making something similar for Gparted live should not be insurmountable.
Unfortunately the maintainer and developer there don't know how to approach the problem and have, after I submitted a bug report, turned it around and back to me.
As I mentioned before, I am not a coder and so I am in well over my gumboots.

I will check out your suggestions oldfred and, though I don't know where I'm headed, I'm always open to a learning experience.
...and yes, I suppose there are other routes that avoid gparted or gparted live, or alternative implementations, but that is walking away from something that really needs an answer.

Anyway, thanks guys for your input.

*addition*
>  [COLOR="#0000FF"]from oldfred:--[/COLOR] I thought those were not partitioned. 
On the Ubuntu live thumb drive they appear to be one bootable fat32 partition taking up the entire thumb drive. However, from info I have come across while Googling this might be a fake partition, the iso file is actually an optical disk file, so the computer has to be 'tricked' into handling it, as the thumb drive, obviously, is not actually an optical drive. Of course I am not knowledgeable and might have misunderstood what I have read.
The isohybrid process, as far as I understand it, that creates a hybrid-iso, makes structures that are non-standard, but thereby enable the boot process. What appears is not exactly what is there.

However it is done and there must be a method. It is this that I seek out.

---

### Post by sudodus on 2015-05-22
> **oldfred said:**
> Is even the Ubuntu live installer when dd'd to a flash drive bootable in UEFI mode?
I thought those were not partitioned. 
But then how does UEFI boot a DVD?

Yes, *oldfred*,

 All current Ubuntu and Ubuntu flavour iso files, including the current mini.iso files are hybrid iso files. I know this well, because my mkusb is using the cloning/flashing/copying method. mkusb is really only a wrapper around dd to make it safe (help avoid overwriting the wrong drive).

It works with the ISO-9660 file system. The isohybrid process provides what is necessary for it to boot from USB.

Look at the iso file when cloned to a pendrive with 'standard' tools, and look at the iso file with a hex editor. I think you understand better than I what you see in the hex editor (at the head of the iso file). I don't understand ***how*** it works, but I know ***that*** it works :-P

---

### Post by sudodus on 2015-05-22
*Also: *Yes also in UEFI mode - the 64-bit versions. But I made  Xubuntu 32-bit boot in UEFI mode today using the following method by  Andre Rodovalho.[URL="http://ubuntuforums.org/showthread.php?t=2276498"]

How to Create a EFI/UEFI GRUB2 Multiboot USB drive to boot ISO images[/URL]

Looking at the details how he makes it work, can help us understand it better.

-o-

I used another method, started with the Ubuntu live systems and added  some more things to boot, and made systems that boot in both BIOS and  UEFI mode. But those systems are not cloned from the iso files, because I  had to add and edit files, which is not possible in the read-only  ISO-9660 file system.
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
Portable installed system that boots in UEFI as well as in BIOS mode[/URL]                 
[URL="http://ubuntuforums.org/showthread.php?t=2259682"]
One pendrive for all PC (Intel/AMD) computers[/URL]

---

### Post by bobbicat on 2015-05-22
Using isohybrid (from syslinux-utils) with various expert options such as --uefi, used on a standard iso file might achieve  the target, but I am, as I said, well out of my depth.
Someone somewhere knows how it comes together, that is sure.

---

### Post by sudodus on 2015-05-22
> **bobbicat said:**
> Yes it most certainly is - and has been for a number of releases. I have been installing that way for quite some time - burning CD's and DVD's is a thing of the past. This is why I thought that making something similar for Gparted live should not be insurmountable.
Unfortunately the maintainer and developer there don't know how to approach the problem and have, after I submitted a bug report, turned it around and back to me.
As I mentioned before, I am not a coder and so I am in well over my gumboots.

I agree that it works. And I understand your situation.

So either you take the shortcut and use gparted in Kubuntu live (where you have to install it, but it takes only a few seconds), or in Lubuntu live, where it is installed and only one click away,

or you accept the challenge, and make a USB boot drive from the gparted-live iso file.
> 
I will check out your suggestions oldfred and, though I don't know where I'm headed, I'm always open to a learning experience.
...and yes, I suppose there are other routes that avoid gparted or gparted live, or alternative implementations, but that is walking away from something that really needs an answer.

Anyway, thanks guys for your input.

*addition*

On the Ubuntu live thumb drive they appear to be one bootable fat32 partition taking up the entire thumb drive. However, from info I have come across while Googling this might be a fake partition, the iso file is actually an optical disk file, so the computer has to be 'tricked' into handling it, as the thumb drive, obviously, is not actually an optical drive. Of course I am not knowledgeable and might have misunderstood what I have read.
The isohybrid process, as far as I understand it, that creates a hybrid-iso, makes structures that are non-standard, but thereby enable the boot process. What appears is not exactly what is there.

However it is done and there must be a method. It is this that I seek out.

When you create USB boot drives with Unetbootin and the Ubuntu Startup Disk Creator, a FAT32 file system will be created and the files from the iso file will be copied to this file system. Finally the bootloader will be installed and there will be some modifications of the configuration files. But when you clone/flash/copy with dd, the ISO 9660 file system will be copied to the pendrive, also when it it treated with isohybrid. It is easy to see (it is reported by for example lsblk).

```

$ sudo lsblk -fm
NAME   FSTYPE  LABEL              MOUNTPOINT        NAME     SIZE OWNER GROUP MODE
sdd    iso9660 Lubuntu 15.10 i386                   sdd      3,7G root  disk  brw-rw----
&#9492;&#9472;sdd1 iso9660 Lubuntu 15.10 i386                   &#9492;&#9472;sdd1   692M root  disk  brw-rw----

```

---

### Post by sudodus on 2015-05-22
> **bobbicat said:**
> Using isohybrid (from syslinux-utils) with various expert options such as --uefi, used on a standard iso file might achieve  the target, but I am, as I said, well out of my depth.
Someone somewhere knows how it comes together, that is sure.

Sometimes trial and error will prove what your intuition tells you :-)

---

### Post by bobbicat on 2015-05-22
Just to add a little complication to the issue - Gparted live is also provided as a zip file. Using this and something very similar to your method above does indeed provide a working object.
So I could if I really wanted to, but...
When you try to use the 'natural' method (dd'ing the iso to thumb drive) it all falls about. Its not that it can't be done another way, its just that the perfectionist within wants me to follow the dd method successfully.
Thanks for being there to bounce this off.

---

### Post by sudodus on 2015-05-22
Yes, there are several ways to do it. Have you tried to treat the iso file with isohybrid yet (according to post #4)?

And after that use dd (or [mkusb (GUI) or mkusb-nox]("https://help.ubuntu.com/community/mkusb") (command line)) to avoid mistakes?

---

### Post by bobbicat on 2015-05-22
@sudodus
Yes, but there are two problems, the first is that it is already a hybrid iso but not functioning as it could, the second that using isohybrid on an already 'treated' iso doesn't produce good results, apparently.
So I need to create for myself a standard 'untreated' iso, then apply isohybrid to it and see what happens. I'm still at the 'create a bootable iso' stage, but working on it.
I'm happy to use dd though I understand your warnings, I have been creating Kubuntu installation disks that way for some time and using it to zero a thumb drive after some of these crazy experiments too..
I'm sure your application will win many takers, it takes the risk out of what is a very powerful operation and that can only be a good thing.

---

### Post by bobbicat on 2015-05-23
The maintainer at Gparted live has at last acknowledged the problem. He is still of the opinion that dding an hybrid iso to give a bootable thumb is the wrong direction to take but at least he is looking into the issue.
Am I so 'bleeding edge' in using this method, I was under the impression that was how things were done these days. I'll mark this thread solved if a viable solution is achieved.

---

### Post by sudodus on 2015-05-23
> **bobbicat said:**
> The maintainer at Gparted live has at last acknowledged the problem. He is still of the opinion that dding an hybrid iso to give a bootable thumb is the wrong direction to take but at least he is looking into the issue.

This sounds promising :-) Maybe you can ask him to provide a 'test iso file' for you: an iso file without the isohybrid treatment, and let you try various options with the isohybrid tool.
> 
Am I so 'bleeding edge' in using this method, I was under the impression that was how things were done these days. I'll mark this thread solved if a viable solution is achieved.

No, not really, most main linux distros provide hybrid iso files. It is the standard nowadays :-)

If you want to, you can start from the following 'How to' link and create your own iso file. It will not be a hybrid iso file, you must add the isohybrid treatment to it, but it is only one line.

 Will Haley's blog post [http://willhaley.com/blog/create-a-custom-debian-live-environment/](http://willhaley.com/blog/create-a-custom-debian-live-environment/)

I used it to create [9w]("https://help.ubuntu.com/community/9w"), which is further developed into [ToriOS]("http://torios.net/").

---

### Post by bobbicat on 2015-05-23
> If you want to, you can start from the following 'How to' link and create your own iso file. It will not be a hybrid iso file, you must add the isohybrid treatment to it, but it is only one line.
Will Haley's blog post [http://willhaley.com/blog/create-a-c...e-environment/](http://willhaley.com/blog/create-a-c...e-environment/)

I think the above might well be what I was looking for. I will give it a whirl and see where it take me. I should get a better, hands on, idea of what is involved.
ToriOS - looks very interesting.
Thanks again for the support.

---

### Post by oldfred on 2015-05-23
Someone posted that if you want a UEFI only Ubuntu flash drive, you just have to extract the ISO to a pre-formatted FAT32 partition on the flash drive. That does not have syslinux which is the BIOS boot loader and then is a standard partitioned flash drive.

I have not tried that with gparted. I normally use grub2's loopmount and just copy ISO to flash drive. Then I can have several ISO on one drive.

---

### Post by bobbicat on 2015-05-25
The maintainer has now produced a version of the GpartedLive iso that does behave properly under UEFI.
So I think I can mark my query Solved.
...but there is a little more, as the interesting comments I have read here are prompting me to explore portable systems and the way they boot.
I've been taking a look at DebianLive which hasn't quite got into UEFI yet and Puppy Linux which has just produced its first 64bit UEFI bootable version. 
Thank you to those who gave me such constructive feedback.

---

### Post by sudodus on 2015-05-26
Thanks for sharing your result (that the maintainer has now produced a version of the GpartedLive iso that does behave properly under UEFI).

And I'm glad that we could help you :-)

---

