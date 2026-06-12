---
title: "Trouble Booting USB with Full Install"
date: 2020-08-01
forum: New to Ubuntu
---

### Post by pawnslinger on 2020-08-01
I am somewhat new to Linux and Ubuntu, but I have been tinkering with it for many years.  My current computer system is a homebrew system, kind of a Frankenstein, built over the years.  My motherboard is an ASUS Crosshair VI with a Ryzen 3950X cpu, 32gb of ram and Windows 10 booting from an NVMe SSD drive.  The chipset on this board is  X370, so kind of old for the 3950X, but it works okay.  It was a treat trying to update the BIOS when I got the new CPU.  Originally I was running a Ryzen 1700X.

So that tells you a little about my system and my background.  What I'd like to do is dual boot the system with Ubuntu (or some flavor of Ubuntu).  I thought the easiest way to do that would be to give Ubuntu a full drive all to itself and just switch the boot order in the BIOS.  I've done this before on an old Dell Server, works great.  Just go into the BIOS and disable the Windows drives and then install Ubuntu on its own drive.  Easy peasy.

Not so fast with this ASUS motherboard... there is no way (that I can find) to disable the NVMe boot drive!  So I am afraid to try and do an install with a Live Linux, I have heard about the bug that might affect my Windows boot drive.  So faced with that problem, I first tried to create the bootable USB in VirtualBox.  That worked, but the USB stick  that produced won't boot.  No matter what I try, the stupid machine continues to boot into Windows... ignoring the stick.  The BIOS does see the stick and recognizes the UEFI partition, but won't boot it.  I have tried disabling Secure boot, turning CSM on and off... Legacy mode, UEFI mode... nothing.

The system will boot the Live Linux USB created by Rufus.  So I can do that, at least.  And I can use persistence with the Live Linux USB.  But I cannot load drivers onto the Live Linux USB.  And I need drivers for my wifi.  Right now I have a jury rigged ethernet cable setup so I can run the Live USB and download drivers and updates that way.  But that is just temporary... I need the wifi to work.

Can I create a full USB stick on an old Dell and boot it on my Ryzen system?  I do have several old Dells around that I can try... but I wish I knew why the USB I create in VirtualBox won't boot.  Might save me some time and effort.

Any ideas?  Suggestions?

---

### Post by sudodus on 2020-08-01
I think the easiest way would be to extract and clone from a compressed image file with Ubuntu 20.04 LTS. You can do it 

- with **Rufus** (with the help from a compressor/extractor tool, for example 7-zip) in Windows or

- with [**mkusb**](https://help.ubuntu.com/community/mkusb) in Ubuntu (can be installed temporarily in a live drive for this purpose).

This way will get an installed system, that can boot both in UEFI mode and BIOS mode. It is tested in several computers. I cannot guarantee that it works in *your* computer, but it is rather easy to try, so you will not waste too much time. See [**this link**](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203) **and links from it** to get more details.

---

### Post by oldfred on 2020-08-01
Be sure to boot in UEFI mode. You do not want to turn on legacy/BIOS/CSM nor select BIOS boot of flash drive installer which is separate choice from default boot setting of UEFI or BIOS in UEFI settings.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you also have video card?

Be sure to use 20.04 as older versions may not have drivers you need.

Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)

Asrock B450 UEFI & Driver update to stop flickering.
[https://pcpartpicker.com/b/t4KBD3](https://pcpartpicker.com/b/t4KBD3)
Asrock B450M Steel Legend - turn UEFI Secure Boot off
[https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine](https://askubuntu.com/questions/1183093/ubuntu-corrupts-bios-on-ryzen-3000-machine)
Vega GPU is built into the CPU, then the M.2_2 socket cannot be used. 
[https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199](https://ubuntuforums.org/showthread.php?t=2424099&p=13877199#post13877199)
Asus B450-F Clock speeds
[https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363](https://ubuntuforums.org/showthread.php?t=2414502&p=13845363#post13845363)

Some physically disconnect other drives. Most UEFI do have setting somewhere on drive configuration to disable the drive.
Some have reported that partitioning in advance with an ESP on Ubuntu drive and from live installer removing the boot/esp flags from other ESP. After install be sure to restore boot flag before rebooting.

I have always done this. I check mounts to make sure. But I think it is because I use grub loopmount to boot ISO directly from one drive, to install to another drive. Then boot ESP is my internal drive.
Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Becuase I use loopmount, I also have to manually unmount the /isodevice as installer asks to unmount partition on drive, but never does.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1155216)

---

### Post by crip720 on 2020-08-01
Why not just install in one of the old dells.  This way Windows can't goof up Ubuntu and Ubuntu can't goof up Windows.  You don't use both systems at same time with a dual boot system anyway.

---

### Post by pawnslinger on 2020-08-01
Well, a couple of things... I forgot to say that I am trying this with 20.04 LTS (for those that suggested I use it).

As for the Dells... well I can use them, but they are not available for permanent Linux installs of any kind -- other family members are the primary users of those machines and while they would let me use them temporarily, I am sure they would lynch me if I tried to install anything more permanent (especially since they are all Windows fanboys).  And even if I could convert them to Linux, well, they are theirs, not really my personal system.  I could buy an old Dell, just for this, but then my wife would divorce me.  But after a long marriage, and a reasonably happy one, probaly not the best move.

If worse comes to worse, I could just unplug the NVMe drive, that would be easier on my marriage... hehehe.  But for some reason I want to avoid plugging and unplugging drives.

---

### Post by sudodus on 2020-08-01
With the method that I suggest in post #2 you need not unplug the internal drive, and you need not use the Dells. I think it will work.

If it does not work, I can suggest other methods that should also work without touching the internal (nvme) drive.

---

### Post by pawnslinger on 2020-08-01
Yes, I have a video card... the 3950X has no gpu... just compute cores.  My video card is an old GTX 1060 3gb variant.  Not my most astute purchase ever.  I wish I had gone for the 6gb model, but I wanted to save some money... foolish now.

I have gone around and around with ASUS, the Crosshair VI has an NVMe Disable option... but the BIOS ignores it.  As far as I can tell.  I mean it boots Windows off the NVMe with it disabled.  So what is the point of the option?  The bottom line, this motherboard is old and ASUS doesn't really want to support it anymore.  But I finally got them to admit, there is no way to disable the drive, except to physically remove it.

Going thru the BIOS settings, I do not see a way to force UEFI Boot.  ASUS lists "Legacy & UEFI", "Legacy" or some other option like "OPROM" which I don't know what it is... all of them as options under CSM Mode.  So there is no pure UEFI mode.  I assume (and you know what that means) that if I insert a UEFI device, it will boot in UEFI mode.... if I inset a Legacy device, it will boot in Legacy mode.  As far as I can tell, the Secure Boot has never been setup on my motherboard, i.e. there are no keys present... but I have it disabled anyway, just to be on he safe side.

So I have set CSM Mode to  all different settings, none work.  I tried booting with about 100 different settings yesterday, anything that seemed pertinent, nada.

The Live USB produced by Rufus boots, but the Full Install produced during a VM session won't.  That's the bottom line.  Is there a way to boot a VM in UEFI mode?  Perhaps a trick in VirtualBox that I am overlooking?  What is difference between the Rufus produced stick and the full install produced stick?

---

### Post by pawnslinger on 2020-08-01
I am going to try the "extract & clone" method that you suggest.  It sounds like it should work.  I will post a reply here and let you know how it turns out.  

I think I will use Rufus and 7zip... I have both and know how to use them.

Thanks for the idea.

---

### Post by oldfred on 2020-08-01
My Asus is an Intel based z97.
But it has the UEFI settings under the CSM mode sub menu. Seems backwards to me as CSM/BIOS is part of UEFI not the other way around.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
And the UEFI or CSM boot mode only booted in the CSM/BIOS mode. But I have a setting for UEFI only that then worked.
See if my screen shots of my z97 are similar?
Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

If you have nVidia, you either need nomodeset boot parameter or now Ubuntu has a safe graphics options that seems to automatically use nomodeset. If not in safe graphics or have not yet installed nVidia driver as part of install, you also need nomodeset on first boot of install. Selecting to install proprietary drivers should then install the nVidia driver, so nomodeset not required. But if you need that:
Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by pbear42 on 2020-08-01
> **pawnslinger said:**
> Is there a way to boot a VM in UEFI mode?
When I read the OP, where you referred to having tried to install in VBox, I had a feeling this was the problem.  Right, by default, VBox boots in BIOS mode.  But, yes, you can boot in EFI mode.  It's an option in Settings, System > Motherboard.  

So, boot the ISO same as before, then confirm boot mode, just to be sure for your own peace of mind.  Run [COLOR=#ff0000]ls /sys/firmware[/COLOR]; if [COLOR=#0000ff]efi[/COLOR] is listed, you're booted in EFI mode.  Now the world's your oyster.  You can use simple erase-and-reinstall or as complex a partitioning scheme as you want.  You even can do encryption, if you like.  I've done EFI installs to USB drive many times with VBox.  No question, it works.  Not my favorite method for installing to USB drive, but has advantages (in particular, it's safest)

By the way, one little tip.  Don't bother with a virtual hard drive. This way, the USB drive becomes sda when claimed from Devices.  Easy peasy, as you say.

---

### Post by pawnslinger on 2020-08-01
Yes.  Your BIOS screens look A LOT like mine... and yes, I was wrong, after looking at your screens, there is an option for UEFI only.  I had not seen it before.  I must be blind (actually I do have very poor eyesight).  Anyhow, strange thing... when I enabled UEFI only... my Windows wouldn't boot!!!  I had to go back to UEFI and Legacy Mode to get Windows rebooted.  Had me panicked for a bit there.  After finally getting my Windows back, the stupid mouse wouldn't work... I had to cold boot the system to get the darn mouse working again.  WOW!!  

I am driving my tech support guy (my son) crazy   <grin>  Maybe he will finally get a job and leave home... hehehe.

---

### Post by pawnslinger on 2020-08-01
> **sudodus said:**
> With the method that I suggest in post #2 you need not unplug the internal drive, and you need not use the Dells. I think it will work.

If it does not work, I can suggest other methods that should also work without touching the internal (nvme) drive.

Okay, this worked!!  I downloaded the compressed image of 20.04 and ran it thru 7zip, then burned it to my USB with Rufus... bingo!  It booted up like a champ.

Thanks for the idea.  Now I wonder how I can do this with other Ubuntu flavors, such as Mint.  I'd like to experiment with other distros too.  I am really going to drive my son nuts!  He is my tech support and a Windows fanboy.

---

### Post by pawnslinger on 2020-08-01
> **pbear42 said:**
> When I read the OP, where you referred to having tried to install in VBox, I had a feeling this was the problem.  Right, by default, VBox boots in BIOS mode.  But, yes, you can boot in EFI mode.  It's an option in Settings, System > Motherboard.  

So, boot the ISO same as before, then confirm boot mode, just to be sure for your own peace of mind.  Run [COLOR=#ff0000]ls /sys/firmware[/COLOR]; if [COLOR=#0000ff]efi[/COLOR] is listed, you're booted in EFI mode.  Now the world's your oyster.  You can use simple erase-and-reinstall or as complex a partitioning scheme as you want.  You even can do encryption, if you like.  I've done EFI installs to USB drive many times with VBox.  No question, it works.  Not my favorite method for installing to USB drive, but has advantages (in particular, it's safest)

By the way, one little tip.  Don't bother with a virtual hard drive. This way, the USB drive becomes sda when claimed from Devices.  Easy peasy, as you say.

YES!  This fixed it!!  It was on the Motherboard tab though... not the Processor tab.  No problem... I found it pretty quick.

Thank you.

Now how do I mark this thread [SOLVED]?

---

### Post by pbear42 on 2020-08-01
> **pawnslinger said:**
> Now I wonder how I can do this with other Ubuntu flavors, such as Mint.
AFAIK, no one but *sudodus* prepares compressed images of already-install systems.  OTOH, as I said, it's easy enough to install to USB drive in VBox.  Set the motherboard to EFI mode.  Boot a live ISO.  Attach a USB drive.  Install same as usual.  Only thing you don't have in this environment is access to the internal drive (you can't install guest additions to a live session).  You do have access to the internet.  There are other methods, but they require you to work around the installer bug *oldfred* mentioned.

---

### Post by sudodus on 2020-08-02
> **pawnslinger said:**
> Okay, this worked!!  I downloaded the compressed image of 20.04 and ran it thru 7zip, then burned it to my USB with Rufus... bingo!  It booted up like a champ.

Thanks for the idea.  **Now I wonder how I can do this with other Ubuntu flavors, such as Mint**.  I'd like to experiment with other distros too.  I am really going to drive my son nuts!  He is my tech support and a Windows fanboy.

There are several methods, some of them described by *pbear42*, some other methods described at the following links.

Do you intend to use it in several computers or in only one computer?

- If in only one computer, you can try according to [**this link**](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312) with a detailed description. (If you want encryption, please modify to activate LVM with LUKS encryption in the partitioning window.)

- If you want to use it in several computers, it should boot both in UEFI and BIOS mode, so try according to 
. [**How to Create a Full Install of Ubuntu 20.04 to USB Device Step by Step**](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-step/) or
. [**This link**](https://askubuntu.com/questions/1086309/how-to-make-bios-uefi-flash-drive-with-full-disk-encryption) to a similar method.

These links show different aspects of what is needed, and I think you will be able to 'do it yourself' and get the systems you want (also different linux distros, at least when they do not differ too much from Ubuntu, e.g. Mint and Debian).

[hr][/hr]
Another easy alternative for extensive testing is to create **persistent live drives** from iso files of linux distros, that do not differ too much from Ubuntu (e.g. Mint and Debian) with [**mkusb**](https://help.ubuntu.com/community/mkusb). See [this list of tested linux distros](https://help.ubuntu.com/community/mkusb/gui#Linux_distros_where_mkusb_works).

---

### Post by C.S.Cameron on 2020-08-03
> **pawnslinger said:**
> 
Now I wonder how I can do this with other Ubuntu flavors, such as Mint.  I'd like to experiment with other distros too.

If you just want to play around with other flavors, you can boot Linux ISO files stored on your HDD using GRUB from your new install:
[https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782](https://askubuntu.com/questions/1251729/20-04-booting-iso-from-grub-menu/1251782#1251782)

There are some more menuentry examples here:
 [https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

