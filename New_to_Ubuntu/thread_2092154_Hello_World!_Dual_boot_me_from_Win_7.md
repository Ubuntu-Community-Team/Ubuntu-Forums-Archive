---
title: "Hello World! Dual boot me from Win 7"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by pjnoxon on 2012-12-06
Just bought new laptop, ASUS K55 i5 2.5Ghz 750 Gb 6Gb RAM DVDmulti etc...

This has Win 7 on C: 254Gb (205 left empty) and there's D: empty 419Gb
This is an ASUS 'remanufacture' ($349) so there is no recovery partition.

Used to work help desk at Indiana University around 2000 (AD) so comfortable with UNIX, and did my code in Assembler making music products (Intel 8031) so good to go with code. Took C and C++ in 1994 but never did anything with it so quite rusty.

Want to move my music technology teaching to Linux. Have taught on Win and Mac, all software DAW programs, 20 years teaching at university level. Look to go with Ubuntu 12.04 and KX Studio, seems like that guy (FalkTX) has it together to make things easier for me. Have to keep the Win 7 as is for other things. Could I install Ubuntu in D: for dual boot? Need to use Partition Magic-like program under Win7 maybe?

I have read a bit and this looks like it might be a problem, as Win does not play nice with other OS in the playground (HD). But would be nice to share .wav files and such between Win and Ubuntu. So have to keep NTFS - is'nt that right?

So what I am thinking is to get my feet wet, there is a nice SD card reader, it seems to work very fast compared with other card readers I have used before, is SDHC compatible. Could I put Ubuntu and KXStudio on a SD card, and put that first in boot order, then when I am in a Ubuntu mood, shove the card in before I turn the K55 on?

thanks for all - pj
[http://teachtonga.com](http://teachtonga.com)

---

### Post by levlaz on 2012-12-06
Win7 has a really nice and easy to use partition editor you can create, delete, change, and even resize partitions from within windows 7.  Its in the control panel. 

Then simply pop in the Ubuntu LiveCD and you are well on your way to a dual boot system.

---

### Post by Nightcreeper on 2012-12-06
No, you don't have to use any partitioning software. When running the CD/DVD in live mode, click install. When the partitioning scheme comes up, click something else. Setup your partitions say 100GB Root EXT4, 300GB /HOME EXT4, and the remaining as Swap. Then tell it to use the C: as the bootloader installation point, not the partition, but, the drive itself (MBR). Then you will boot and a menu will give you a choice to go to Windows or Ubuntu/Derivatitive. You have to mount the windows partition in Ubuntu after boot, I am pretty sure there is a way to make it auto mount, but I don't know how, but, you will be able to view folders from the windows side and use them, if wanting to share back and forth, use the windows partition for storage.

---

### Post by oldfred on 2012-12-06
Since it is an i5 system, it could be the older BIOS/MBR which has a maximum of 4 primary partitions, or the newer UEFI that has no partition limit but installs in a totally different way.

Even though you have a card reader not all computers will boot from a card reader. But most newer computers will boot from a USB flash drive which often is just seen as another hard drive to boot loader.

       Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Only use a Windows partition manager to shrink the Windows partition not to create new partitions. It may convert to dynamic if you exceed the 4 primary partitions in MBR. And dynamic does not work with Linux.

---

### Post by mastablasta on 2012-12-07
instead of cards USB is indeed better option. it is also good if you just install it inside virtual box [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox). so when you are in the linux mood you just double click the vbox icon and it will popup. ;-)
 
SD cards have slow read&write speed. vbox should be faster on your config.

---

### Post by Mark Phelps on 2012-12-07
> **Nightcreeper said:**
> No, you don't have to use any partitioning software. 

Actually ... UNLESS you want Win7 corrupted so it doesn't boot anymore, then YES, you DO have to use partitioning software -- in this case, the Win7 Disk Management utility.

Win7 doesn't behave well when its OS partition is messed with from "outside" -- as in, using the Ubuntu installer to shrink the partition.  That can result in filesystem corruption, which will then prevent Win7 from booting -- which will make it very difficult to repair.

---

### Post by audiomick on 2012-12-07
My 2 cents.

I wouldn't bother messing around with card readers or external drives. You have a fair amount of room on there. Use your externals for extra storage if need be. A person with your background should not have any trouble at all dealing with the install that you need.

Just by the way, have you looked at Ubuntu Studio?
[http://ubuntustudio.org/]("http://ubuntustudio.org/")

Do use the Windows tool to re-size the partition that your Win7 install is on. Sounds like you can shrink that down rather a lot. If you are really consistent about storing your data onto your data partition(s), then you wont need much room on there at all. As far as I can  tell, the Win7 install on here is using about 30GB. I should mention, though, that it practically never gets  used. There are some programs installed for various Yamaha Digital mixing desks, and I think the Soundweb Designer is on there, but that is it. Anyway, I digress. You can probably free up a fair bit of space from that partition.

When you have re-sized the Win partition, I gather it is a good idea to boot into windows a couple of times to give it the chance to run its disk repair utility if it wants to.

You'll have to decide for yourself how much room to leave to your Data partition. You do need to retain an NTFS partition to be able to store files somewhere that you can get to from both Windows and Linux. This is not a drama, though. My laptop has an NTFS partition on it for data that the windows Vista install had on it when I bought it, and I routinely store files to there from both the Linux install on there and from the Linux install on my desktop via Samba whilst my laptop is booted into Linux.

When you do your install, you might want to consider putting your /home folder on it's own partition. You already have to go into the manual partitioning mode of the installer, so making a separate /home is not much of a further complication. In fact, it is not complicated at all. Doing this brings you the advantage that you can retain your /home partition should you have to do a fresh install at some time in the future (hopefully a while in the future, but chances are you will have to do this...), and by retaining your /home, you can retain all your configurations and user preferences and what have you, as well as any data that you have saved there.

If you choose to make a separate /home partition, you could do
about 15 - 20 GB for your Linux system. Mount point /

a swap partition a little larger than the amount of RAM you have. You say you have 6GB, so maybe 6.2GB or so. Mount point is automatic when you choose "swap" as format (or vise versa?)
If you know for sure you never want to hibernate the system, you could make the swap space a bit smaller, but that is likely to be a matter of saving 4GB on a 750GB drive...

If you are consistent about saving your files to a data partition, you could leave /home fairly small. If you have a fair amount of stuff that is linux only, it will go there by default and will need an appropriate amount of space. Basically, you need to decide how to divide the drive space between your linux only /home partition (or / partition if you don't do a separate /home) and your ntfs data partition.

I refer you back to oldfred's post regarding the 4 partition limit and primary and logical partitions. If you are subject to the 4 partition limit, leave the two you have as the are (after resizing) and put everything else on logical partitions inside an extended partition. Linux does not have a problem with being installed on a logical partition as windows does.

The partition magic like tool for partitioning in the Linux world is Gparted, or at least that is one of them. ;) This is installed by default on the live environment that you get into on the live CD (or is it a DVD now?) or USB if you go that way. Using a USB stick for your installer instead of a CD/DVD has a lot to recommend it, particularly if you are likely to be doing any partitioning  work from there before you do your install. Running from a USB stick is considerably faster than from a CD or DVD. Gparted is not installed by default when you install Ubuntu, but can be had from the software centre. Don't be nervous about gparted. Just look carefully at what you are seeing on the screen, and you will be fine. It doesn't do anything final without telling you it is about to.

When you do your install, you need to get into the manual partitioning mode. That is the "something else" option when you get to the point where you an choose between "beside windows" and "use the whole drive". If you let it choose either of those automatic options, I believe it will remove your data partition.

---

### Post by pjnoxon on 2012-12-19
OK, thanks for this info everyone.

This computer is UEFI which is  good because it seems like all Linux versions really require more than  two partitions for itself: root, swap, and home at a minimum. So I will  use the  Win7 Disk Management utility to shrink the C: and D: leaving  space for the extended partition for Ubuntu. I will then reboot a few  times for chkdsk to be happy with the results.

The boot screen has a place to add a boot source in the form of 
\EFI\BOOT\BOOT[architecture name].EFI 
so I believe that it might be possible to run off the SD card, again  this built in unit seems a lot faster than ones I have used in the past,  but it's best to go on the HD I think. Still this would be a nice way  to try out new versions of Linux, which seems to be a favorite pastime  of everyone using Linux since new distributions seem to come out every 5 minutes...

There  is still a missing piece. A few days after I got my laptop it  downloaded 72 OS updates and it took all night to install them, then a  few days later it tried to load 7 more but got stuck on number 5 for 9  hours. I was given bad advice, but fortunately I found the answer was to  shut down and unplug the battery. Needless to say I don't want that  happening again, so I disabled auto-update and I don't really want to  have to re-install Win7 (like ever). So there must be a way to leave  Win7 on there and add a second option to the Windows boot loader, like  EasyBCD but free? Does the Ubuntu installation offer something like  this? I wasn't clear and have a lot to learn.

---

### Post by oldfred on 2012-12-19
Grub2 chain loads to Windows just fine. But the current efi version does not yet do it automatically. It creates the old BIOS version chain load. Boot-Repair will add a correct chain load entry or you can add one manually (see bug report).

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Any entry that looks like this is an old BIOS entry.
'Windows ...) (on /dev/sdXY)'

How you boot installer is how it will install. If Windows boots with UEFI, you need to use 12.10 64 bit version as that has the UEFI install option.

 Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

       ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

            Asus UEFI instructions (except efi should be first partition, but must not have to be) Older install:
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Newer system:
       
 Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

---

### Post by pjnoxon on 2012-12-20
Hey, this is a really great help. I did look further into the EasyBCD and it looked
like a paid commercial product but turns out there is a free version after all so
I can follow these instructions I found online:

[http://blog.famzah.net/2011/11/12/boot-linux-using-windows-7-boot-loader/](http://blog.famzah.net/2011/11/12/boot-linux-using-windows-7-boot-loader/)

Which basically is what I gleaned from all the help I'm getting here:

1) resize with Win7 Disk Management utility so C: 120Gb D: 380Gb
2)  I will look into the quickboot in the boot menu, I don't think there is any secure boot    
    in Win7. Download [Ubuntu-Secure-Remix]("https://sourceforge.net/projects/ubuntu-secured/files/") 64bit and burn to disc, install on 
    unformatted area (dev/sda3?) so that I have /boot 40Gb, /swap 10Gb, /home 100Gb
     there is this note about grub2:
        "The issue was using GRUB2 when setting it up with EasyBCD. For some  reason it doesn’t create the ang0 file that’s required to boot. Redoing  it using Grub(Legacy) instead fixed it." but I am guessing this is something I can choose when I download and burn the ISO CD?
3) use EasyBCD to setup the dual boot

That is interesting that 12.10 has UEFI, but I am getting pointed towards 12.04 by the LinuxAudio dude FalkTX who keeps the Audio distro going. It will probably get changed like everything else Linux, in another five minutes.

I really appreciate the heads up on the possible errors you have pointed out.

thanx - PJ
[http://teachtonga.com](http://teachtonga.com)

---

### Post by oldfred on 2012-12-20
Did they finally update EasyBCD to work with UEFI? There really is no advantage and some disadvantages to EasyBCD with UEFI.

Both Windows & Ubuntu will install boot files in the efi partition. Those in the past who wanted Windows in the old MBR then needed something like EasyBCD as you can only have on system booting from MBR. But with UEFI every system is equal and can add its own boot files into the efi partition. The choice from the UEFI menu is like having many MBRs with different boot loaders in every MBR.

Grub adds chain load entries to make it easy to also boot Windows when ubuntu is set as default in UEFI menu.
But because of a bug, you still need Boot-Repair to add the correct chain load entry. Or you can manually add it.

---

### Post by pjnoxon on 2012-12-22
One worry was the question, which partition scheme came on my new laptop with Windows 7 Home Premium 64bit? Unfortunately in the Disk Manager it does not indicate the file system for the EFI (200Mb) and recovery partition (25 Gb which is empty, I wonder if I should delete it, although it has no drive letter either), (nor will it give me any info at all about this mysterious protected Q: partition which apparently has MS office on it?)!?
It could have had MBR theoretically, since it does not have a HD of more than 2.2Tb.
So I would need to change to GPT as is discussed in this forum:

[http://ubuntuforums.org/showthread.php?t=1958383&page=3](http://ubuntuforums.org/showthread.php?t=1958383&page=3) entry #27

But looking at the Microsloth Forum 
[http://support.microsoft.com/default.aspx?scid=kb;EN-US;2581408](http://support.microsoft.com/default.aspx?scid=kb;EN-US;2581408)
I find:

(HOPEFULLY YOUR CAN READ HTML, I CAN'T FIGURE OUT HOW TO PUT A TABLE IN HERE!)

Table 3: Windows support for combinations of boot firmware and partitioning schemes for the boot volume
<HTML><TABLE>
<TR><TD></TD><TD>BIOS+MBR</TD><TD>UEFI+GPT</TD><TD>BIOS+GPT</TD><TD>UEFI + MBR</TD></TR>
<TR><TD>Windows XP</TD><TD>Supported</TD><TD>Not supported</TD><TD>Boot volume not supported</TD><TD]Boot volume not supported</TD></TR>
<TR><TD>Windows Vista</TD><TD>Supported</TD><TD>Supported(64b)</TD><TD>Boot volume not supported</TD><TD>Boot volume not supported</TD></TR>
<TR><TD>Windows 7</TD><TD>Supported</TD><TD>Supported(64b)</TD><TD>Boot volume not supported</TD><TD>Boot volume not supported</TD></TR></TABLE></HTML>

Now since my laptop has UEFI as indicated by the boot screen (esc when booting) and it does work (as in it does access the boot volume) then this table indicates it must be GPT as it pretty much would have to not be UEFI in order to have MBR, I think?

Basically things get switched over as time marches on, as in there are
probably no laptops now manufactured with MBR by now, I think?

---

### Post by oldfred on 2012-12-22
Did you post BootInfo any where or did I miss it?

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

    
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

### Post by pjnoxon on 2012-12-24
OK, things starting to come into focus slowly. The problem that
I would likely run into when I do install Ubuntu 12.04 is described here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

This overview provides much but not all information that applies:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

One major confusion for me was Windows 8 has additional problems like
SecureBoot and possibly QuickBoot, that I don't have to worry about, plus I
did not realize that Ubuntu (perhaps all Linux) are essentially patching around
the UEFI capability instead of embracing it moving forward (I think?). The other
confusion is that some motherboards allow different schemes for different boot
devices (Legacy on the HD while UEFI on the CD/DVD) which does not apply to
me either. Then there is this pretty good description:

[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

But it seems to be in German but helps, and suggests my CD won't boot in UEFI
which I don't think applies. So oldfred's description of how to fix the UEFI boot
entry was really the right answer. So I am ready to try the Ubuntu 12.04 now.

Where to I get the ISO for Ubuntu 12.04 with the Boot-Repair?

One final question, I see a lot of ink re:Nvidia but I have a SandyBridge with the
HD3000 built in video. Is Ubuntu ready for that?

thanks everybody so far - prof james

---

### Post by oldfred on 2012-12-24
There is only one driver for all versions of Intel video. And it supposedly was updated and improved to work, but a few have posted some issues. I have nVidia, so I have not paid close attention.

some seem to have to force a video setting to the exact size their screen is.
This example is for 1280x1024, but you have to use yours.
       Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60

Someone posted this but I do not know:
       For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

different system needed this, or you may have to search for other boot parameters for your system.:
       Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

[http://www.phoronix.com/scan.php?page=news_item&px=MTI1Mzk](http://www.phoronix.com/scan.php?page=news_item&px=MTI1Mzk)

---

### Post by YannBuntu on 2012-12-26
> **pjnoxon said:**
> Where to I get the ISO for Ubuntu 12.04 with the Boot-Repair?

There is none (there was, but it is not supported any more).
Instead , I recommend you use Ubuntu-Secure-Remix-12.10-**64bit** : [https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
12.10 has better UEFI compatibility than 12.04.

---

