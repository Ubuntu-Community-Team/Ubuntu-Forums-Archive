---
title: "Win 8.1 secure boot"
date: 2014-12-18
forum: New to Ubuntu
---

### Post by verymadpip on 2014-12-18
Hi everybody.
If I install Ubuntu in dual boot with Win 8.1 can I re-enable secure boot without any unwanted consequences once the installation is done?
It appears that with the HP hardware I have secure boot needs to be turned off for the installation to proceed.

---

### Post by grahammechanical on 2014-12-18
I do not have Window 8, secure boot, UEFI or GPT and all that stuff but I would say that the answer is NO.

Why? I guess, because with secure boot turned off the kernel that gets installed is not the kernel that has been signed to comply with secure boot protocols. If we turn secure boot back on the booting process of the machine will detect Linux as unsigned and not allow it to load. That is my guess.

You could try what you want, then run Boot Repair. That might then install a signed kernel. I do not know if this will work.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Regards.

---

### Post by verymadpip on 2014-12-18
Thanks grahammechanical.
I think I'll just avoid the possible hassle & leave it turned off.

Anything for a quiet life ;)

---

### Post by oldfred on 2014-12-18
HP's are not dual boot friendly with UEFI.

You have to do a work around to get it to boot anything but Windows.

Several alternative work arounds. Most if dual booting copy grubx64.efi into /EFI/Boot and rename it to bootx64.efi and select the hard drive to boot from UEFI menu. I think you can also copy shimx64.efi (signed grub) instead and boot in secure boot mode. 
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Other HP

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

 Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

---

### Post by verymadpip on 2014-12-18
Thanks for the links & info oldfred.
I'll check it out before I make a decision to go ahead.

---

### Post by verymadpip on 2014-12-19
As it goes, I'm not having much luck on finding any info on *how *to back up the efi partition.
Anybody got any advice on that?
Can I do that with Boot Repair in a live environment?
Sorry for being difficult.

---

### Post by oldfred on 2014-12-19
One advantage of the efi partition over the MBR, it that it just is files. You can copy the files to any other drive and then just copy them back and it will work. File structures and having all the files is what is important.
I even copied my efi files to my flash drive and changed the grub.cfg to boot files on flash drive and it worked. You could not do that with BIOS/MBR.

---

### Post by verymadpip on 2014-12-19
Hi oldfred.
I can't find the efi partition on the Windows machine in Nautilus from a live environment.
GParted sees it no problem.
I'm clearly missing something simple.

---

### Post by fantab on 2014-12-19
Use only Windows tools from windows to work on Windows partitions.
One such tool for Windows: [macrium reflect]("http://www.macrium.com/reflectfree.aspx")

---

### Post by oldfred on 2014-12-19
I always label my partitions. 
I try to remember to label when creating partitions with gparted, but if I forget I use Disks or even command line.
If not labelled, the auto mount shows partitions by UUID or by size so it often is not as clear which is which.

---

### Post by verymadpip on 2014-12-20
Hello gents.
As luck would have it I know that the efi partition is 260mb (unlabelled), so I should be able to identify it.  It simply isn't showing up in Nautilus.  The Windows OS partition is, along with a 400mb "recovery" partition.  Oddly the HP recovery partition (18ish Gb) & the efi partition are not visible.
The efi partition doesn't appear to be accessible in any easy way from Windows either.

Gparted gives me the option to copy the partition, but not the option to paste it anywhere.

I'm familiar with Macrium so perhaps that's the way to go.  I was hoping with what oldfred had said I'd be able to copy the files from the efi partition using Nautilus - nice & simple...

I'm away from the HP for the rest of the day, but will pick this up againlater.

Thanks for the help so far guys.

---

### Post by oldfred on 2014-12-20
If you are actually booted into your system, you have already mounted the efi partition, and Nautilus only shows unmounted partitions, or partitions mounted in /home or /media.

The entry in fstab it is mounted at /boot/efi  and on efi partition it is installed to /EFI/ubuntu, so full path is /boot/efi/EFI/ubuntu.

Just go into Disks and label it. But now with gpt, there are two labels. One is gpt partition label and the other is the file system label. The one we usually see is the file system label.

---

### Post by verymadpip on 2014-12-20
I did not know that about Nautilus.  I learn something new everyday.

I'm working in a live environment at the moment, not an installed system.  (Lack of courage there).
Using disks I've mounted the efi partition & it is now visible in Nautilus at /media/ubuntu/some-numbers-&-letters.
My plan is to copy the entire /media/ubuntu folder to a flash drive.  Hopefully that should cover everything as a backup should awful things happen when/if I attempt the install.

Okay, I had to copy the some-numbers-&-letters folder rather than the ubuntu folder, but that's good enough as a backup I think.

Thanks for the help so far oldfred.
I may be brave enough to try the install soon.

---

### Post by verymadpip on 2014-12-21
Here's the next dumb question:
During the install where do I tell Ubiquity to install grub?

---

### Post by oldfred on 2014-12-21
drive that is sda
Best answer is always the same drive you install Ubuntu onto or if only one drive the drive seen as sda usually. A few systems promote the flash drive to sda, then hard drive is sdb.

Almost never to a partition like sda1 and with UEFI it seems to correctly default to install to the efi partition when you specify the drive.
In BIOS when you specify a partition, it installs to a partition boot sector which can only be booted from another install of a boot loader that can chain load.

---

### Post by verymadpip on 2014-12-21
Thanks oldfred.
I'm going to go for it tomorrow & see what happens.

---

### Post by birkopf on 2014-12-22
One thing which I would like to add (figured out after 10x installs and 100x resets...) 

When you take the first steps before insalling linux alongside Windows 8 or 8.1, that is turn off fast boot in Windows, turn off secure boot in BIOS (you maey need to set BIOS password first)
you need to fully switch from UEFI to Legacy in boot options. The key here is to switch every single option to Lgacy, meaining Legacy needs to take priority over UEFI. 
On Lenovo, which is particularly annoyong with that it looks like that:

[IMG]http://tinyurl.com/p4y3ruc[/IMG]

When you install linux, click on first partitions and check which one is EFI partition (EFI file system) then, under partitions list you will have option to choose where to install GRUB. 
Most likely this will be sda2 so point your installer to set GRUB there. Once you install linux, you won't be able to see GRUB  unless you go to BIOS and switch back to UEFI support.

On Lenovo it looks like that: 

[IMG]http://tinyurl.com/lhaglls[/IMG]

In many cases you will not be able to have dual boot unless you do that above. Have fun! :)

---

### Post by verymadpip on 2014-12-22
Hi birkopf.
I have to say I'm sceptical abpout the legacy approach.  Simply because I've not come across that method anywhere else that I've looked as of yet.
This hasn't helped my thinking:
[http://ubuntuforums.org/showthread.php?t=2257711](http://ubuntuforums.org/showthread.php?t=2257711)
I do thank you for chipping in to help nonetheless :)
It could very well be that I have to try the install this way in the end.

My plan is this:
The space for Ubuntu is already created & Win 8.1 boots & functions as it should.
Secure boot & fast startup are disabled.  (The Live USB is being a little finicky, sometimes it decides to boot with secure boot off, & sometimes not).

-I will go through the install process as usual, allowing the bootloader to install to sda, which is the default suggested by Ubiquity.  I've already questioned this given I have an EFI partition, which is indeed sda2.
-Before rebooting into the installed system I plan to copy grubx64.efi from my Live USB: /cdrom/EFI/grubx64.efi to the efi partition: /some-numbers-&-letters/EFI & rename it to bootx64.efi.
-Then I reboot, go into the setup, & tell the machine to boot from Ubuntu in my UEFI menu doodad - providing it's listed of course.
-Save changes & boot the system.
-Cross fingers & probably pray.

A recovery medium has been created should everything go belly up & I have a copy of the EFI partition on a flash drive.

I've got a festive-come-celebratory function to attend this evening before I can begin this attempt, so if anyone has any advice before I go ahead, ***please do chip in***.
(I don't drink so I'm not going to be trying this while wide eyed & legless...)

Gentlemen, I will be back with a sit-rep later.

---

### Post by oldfred on 2014-12-22
To birkopf suggestion of turning on legacy support.
That could very well be required. I have seen that suggestion with Dell and the Dell post indicated it was an Intel thing, so may apply to more than just Dell. 
I always thought Legacy & UEFI were totally separate, and mostly they are.

But you need to still install in UEFI mode and how you boot installer UEFI or BIOS is how it installs.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

A few systems will not install in UEFI mode no matter what or users are not able to find combination of UEFI/BIOS settings that works. Boot-Repair can convert BIOS to UEFI, if needed. But if in BIOS be sure to install grub to sda, not sda2. 

On my motherboard, I only had Windows and "other" which I think really meant secure boot on or off. And then all the UEFI settings could only be seen in a sub-menu under CSM which seemed strange. And then even though it had UEFI and BIOS, UEFI first and UEFI only, the only setting that would let me boot installer in UEFI mode was UEFI only.
Or Vendors have many different ways they have implemented UEFI.

---

### Post by verymadpip on 2014-12-22
Up to now it matters not what I do the only OS that will boot is Win 8.1
There is no mention of Ubuntu in the UEFI at all.
Gonna have a rethink & maybe try again tomorrow.

---

### Post by verymadpip on 2014-12-23
I have some level of success.
If I press F9 as the machine starts I can to choose to boot Ubuntu, which then presents me with the grub menu.
So far I have to select advanced options & then boot one of the kernels. I've only tried the 3.13.0-43-generic kernel so far.
I believe this is progress, albeit with an interesting new twist - Ubuntu will neither shut down nor restart correctly.  It hangs on the screen with the dots & has to be powered off with a long button press.  I can't even get any info by pressing escape.

---

### Post by oldfred on 2014-12-23
Sounds like a typical video issue.
What video chip/card do you have. With nVidia or AMD you need nomodeset until you install proprietary video drivers, or with newer Intel chips you often need boot parameter to get it into correct mode.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
    
Do not force power off, remember the elephants:
       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by verymadpip on 2014-12-23
Hi oldfred.
Intel ValleyView Gen7 (?).
Nomodeset seemed to cause the machine to freeze on boot.  REISUB (always liked the utterly broken thing myself) didn't help unfortunately.
No additional drivers are available either.

---

### Post by oldfred on 2014-12-23
If its Intel, nomodeset does not usually work, you have to use one of the other parameters as shown in link and ubfan1's post. Some that usually work depending on version of Intel chip. Try each.
       i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

---

### Post by verymadpip on 2014-12-24
Ah, okay.  My mistake.
I'll give it a go a little later - more festive functions today...
Come to think of it, a properly functioning Ubuntu install on this laptop would be a great Christmas gift :)

---

### Post by verymadpip on 2014-12-24
Removing quiet splash causes machine to freeze during boot
i915.modeset=0 machine freezes during boot
i915.i915_enable_rc6=1 machine freezes on restart at "will now restart"
acpi=off no wireless or battery monitor available, graphics corruption during reboot?  Don't actually know what is happening because of the graphics corruption...
acpi_osi=linux machine freezes on restart at "will now restart"
acpi_backlight=vendor machine freezes on shutdown at "will now halt"  (Tried a shutdown instead of a restart).
noalpic machine freezes on shutdown at "will now halt"  (Tried a shutdown instead of a restart).
sudo shutdown -P now machine freezes during shutdown
sudo shutdown -h now machine freezes during shutdown
Checked USB for defects - no errors found.

Looks like there's no way to successfully run Ubuntu on this machine.  I don't know how many more time I can force the power off before something breaks.  For the record it's a Pavilion 11 x360 - not recommended :(
Guess it's time to give up.

Well gents, thanks for trying & Merry Christmas.

---

### Post by fantab on 2014-12-25
Post your **bootinfo summary** which Boot-Repair creates. Just post the link here.

---

### Post by verymadpip on 2014-12-25
Too late - already wiped the install & now the machine won't even boot into the live environment.
It just freezes on the splash screen.
Ooh - I spoke too soon, the live USB is running, but I can't mount the efi partition from disks anymore, which I was hoping to do to clear out the stuff left over from the last install.

---

### Post by verymadpip on 2014-12-25
Boot info summary from the reinstall
[http://paste.ubuntu.com/9619915/](http://paste.ubuntu.com/9619915/)

---

### Post by oldfred on 2014-12-25
Do you have rEFInd installed or is that left over?
Do not know rEFIND, but some with HP have found that to be one solution that lets then boot Ubuntu. The other is renaming /EFI/Boot/bootx64.efi and copy grub or shim as boot x64.efi.

Did you try these options? With newer Intel systems they seem to be better.
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

Some vendors create a separate partition for the vendor efi files and somehow use that when they want the vendor files. HP seems to put them all into the standard efi partition, but then os-prober finds many new entries. I would try turning off os-prober and manually copy only a few entries into 40_custom.

 From live installer mount the efi partition on hard drive:
mount /dev/sda1 /mnt
mkdir /mnt/EFI/Boot
cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi


Copy the  entries from this:
 sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

 #Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu after any change
sudo update-grub

---

### Post by verymadpip on 2014-12-26
Hi oldfred.
rEFInd is leftover I think, although I can choose it to boot from when pressing F9 at boot.  It doesn't actually boot anything anymore.  It worked with the last install.  So yes...that's leftover & of no use.

At this point I can boot into Win 8.1 & Ubuntu, using F9 to change the boot order.  Not ideal, but I think that could be dealt with after sorting out the shutdown/restart issue.  Or is the thinking that something in that "faulty" boot process is contributing to the shutdown/restart problem?

What I *can't do* is restart or shutdown Ubuntu.  The machine hangs after it tells me it's either going to restart or halt depending on what I've asked it to do. I then have to force it to shutdown by pressing the power button.
This behaviour was also exhibited when trying to restart or shutdown from a Live USB.

---

### Post by verymadpip on 2014-12-26
video=1366x768-24@60 - machine doesn't boot.  Hard shutdown required.
video=VGA-1:1366x768-24@60  - machine doesn't boot.  Hard shutdown required.

I'll pick this up again later gents.
I know I'm being a pain & I do really appreciate all the effort you guys are going to helping me here, so thanks again :)

---

### Post by oldfred on 2014-12-26
What does happen on screen. Are you also removing quiet splash so you can see boot process?

Please do not do hard shutdown, remember the elephants. See post #22.

Hard shutdown, may corrupt system and then it will not work until fixed with a fsck.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by verymadpip on 2014-12-26
Hi oldfred.
When the machine locks it locks completely.  REISUB has no effect whatsoever.  No response from any keystrokes, just nothing.  Maybe I need to wait longer?
Tried REISUB on frozen boot & frozen shutdown on more than one occasion with no response from the machine at all.  I really have no option but to hard shutdown.
As I say I can boot the OS, it won't shutdown or restart.  It just hangs & stays there. 
This is pretty much why I'm about ready to throw the towel in.  All this hard shutdown business can't be helping matters.

With the "video=" settings I'd selected the kernel to boot from advanced options, edited the parameters then crtl+x.  The machine locked after "loading initial ramdisk" if I recall correctly with both of those settings.
I'll have to try with quiet splash disabled again to give the point at which that particular boot failed.

On shutdown/restart the machine freezes when the cursor drops to the line after "will now restart" or "will now halt".  It just never does either of those things.
I don't know what to say....

---

### Post by oldfred on 2014-12-26
Do not know about shutdown issues, but seems related.
So when you boot is video ok?
Or is that just with Live installer?

What model HP? 
Some have posted they need additional boot parameters also, not just the Intel ones.

If you can boot, then reviewing log files may show certain hardware that is causing issues and narrows down the problem. Log file is the same as what you see without quiet splash, but then it is re-viewable.

---

### Post by verymadpip on 2014-12-26
Hi oldfred.
I'm able to boot into a perfectly functioning Ubuntu.  (I have to press F9 to choose the boot device, which then gives me the grub menu, other than that everything functions as it should).
 I'm unable to shut down or restart from Ubuntu without the machine locking up & basically becoming a paperweight.
Windows 8.1 functions as it should.  Shuts down okay & restarts okay.
Any suggestions on which log files I should be looking at?

---

### Post by oldfred on 2014-12-26
You should have a log file viewer. Or just called system log.
But you want dmesg to see the boot process. If not offered in left panel the gear/star icon in upper right lets you open more logs.
or:
 gksudo gedit /var/log/dmesg

It is long, but you want to look for warnings, errors, repeated entries with failure or even sucess after multiple tries. And anything with long time to next timestamp. The numbers in the [0000.0] are the time stamps. It will start with a lot of entries at zero. Last entry is the total time from grub to boot. There are lots of other log files, you may want to review, but I do not think there is a separate one for shutdown. 

Still seems to me to be some UEFI setting. Is secure boot on/off?, Both Windows fast boot is hibernation and UEFI may have a fast boot entry also, so UEFI does not rescan hardware on every reboot. Best of all fast boot settings are off. Not sure about other UEFI settings. 
I have a Asus motherboard and had to make many UEFI settings changes, but once I found a good working configuration it works well. And every vendor has different settings. Even different models. What model is yours?

---

### Post by verymadpip on 2014-12-26
Hi again.
The machine is an HP Pavilion 11 x360PC 11-n083sa for the UK market.
Fast boot turned off in Windows - no fast boot options in UEFI settings.
I disabled Windows hibernation with powercfg -h off
I've got secure boot off at the moment.  Even though secure boot is disabled I have an option to clear all secure boot keys, which disables secure boot..?
Unfortunately the UEFI adjustments available are pretty woeful.
I've just noticed cd rom boot is enabled - don't have an optical drive..... let's disable that.
Think I'm going to disable smart connect too...

---

### Post by oldfred on 2014-12-26
That CD boot could be an issue.
One user had a floppy drive enabled without floppy drive and it always took awhile to error out.
Another user did have DVD in drive and system for some odd reason wanted to run fsck on DVD every reboot.

So odd settings can cause issues.

I would not clear all keys. That is a bit advanced and Ubuntu is using the Microsoft key. There are ways to create your own key or install other keys but have no idea of details.

---

### Post by verymadpip on 2014-12-26
Okay.  dmesg shows a bunch of acpi errors & a few other nasty looking lines.

```
[    0.126942] ACPI Error: [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.126952] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.IPCL] (Node ffff880179ac8938), AE_NOT_FOUND (20131115/psparse-536)
[    0.126964] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.PCLK] (Node ffff880179ac88e8), AE_NOT_FOUND (20131115/psparse-536)
[    0.126972] ACPI Error: Method parse/execution failed [\_SB_.TBSW] (Node ffff880179ac8f00), AE_NOT_FOUND (20131115/psparse-536)
[    0.126980] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q1D] (Node ffff880179ac9028), AE_NOT_FOUND (20131115/psparse-536)
[    0.126988] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node ffff880179ac2c08), AE_NOT_FOUND (20131115/psparse-536)
[    0.127249] ACPI Error: [\_PR_.CPU0._PPC] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[    0.127257] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.IPCL] (Node ffff880179ac8938), AE_NOT_FOUND (20131115/psparse-536)
[    0.127266] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.PCLK] (Node ffff880179ac88e8), AE_NOT_FOUND (20131115/psparse-536)
[    0.127274] ACPI Error: Method parse/execution failed [\_SB_.TBSW] (Node ffff880179ac8f00), AE_NOT_FOUND (20131115/psparse-536)
[    0.127282] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._Q1D] (Node ffff880179ac9028), AE_NOT_FOUND (20131115/psparse-536)
[    0.127290] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_._REG] (Node ffff880179ac2c08), AE_NOT_FOUND (20131115/psparse-536)

[    0.787896] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
[    0.787905] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)

[    0.970199] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM

[    1.049058] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.049178] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.049295] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.049412] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.049528] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.049651] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.049768] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.049885] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.

[    5.626369] init: plymouth-upstart-bridge main process (159) terminated with status 1
[    5.626391] init: plymouth-upstart-bridge main process ended, respawning
[    5.630679] init: plymouth-upstart-bridge main process (172) terminated with status 1
[    5.630700] init: plymouth-upstart-bridge main process ended, respawning
[    5.634326] init: plymouth-upstart-bridge main process (174) terminated with status 1
[    5.634348] init: plymouth-upstart-bridge main process ended, respawning
[    5.639512] init: plymouth-upstart-bridge main process (176) terminated with status 1
[    5.639543] init: plymouth-upstart-bridge main process ended, respawning
[    5.642887] init: plymouth-upstart-bridge main process (178) terminated with status 1
[    5.642912] init: plymouth-upstart-bridge main process ended, respawning
[    5.645600] init: plymouth-upstart-bridge main process (180) terminated with status 1
[    5.645622] init: plymouth-upstart-bridge main process ended, respawning
[    5.649804] init: plymouth-upstart-bridge main process (181) terminated with status 1
[    5.649827] init: plymouth-upstart-bridge main process ended, respawning
[    5.754416] init: plymouth-upstart-bridge main process (183) terminated with status 1
[    5.754437] init: plymouth-upstart-bridge main process ended, respawning

[   14.955305] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
```

I'm guessing the problem's there somewhere.

---

### Post by oldfred on 2014-12-26
I do not know if this causes other issues.

Try adding it to the Linux line in place of quiet splash. If you are using a video parameter include that also.
worked for HP2000
acpi=off  

Not sure what all the acpi=off does.

Are there any settings for acpi in UEFI?
You are booting in UEFI mode? But did you leave legacy mode on? I might also try changing that separately if you did.

Some more info:
[http://askubuntu.com/questions/139157/booting-ubuntu-12-04-with-acpi-off-grub-parameter](http://askubuntu.com/questions/139157/booting-ubuntu-12-04-with-acpi-off-grub-parameter)

Some of the issues you may then have:
[https://wiki.archlinux.org/index.php/ACPI_modules](https://wiki.archlinux.org/index.php/ACPI_modules)

I do not know if this applies or not since Arch
**[Boot Problem with HP Pavilion 11 x360 PC]("https://bbs.archlinux.org/viewtopic.php?id=184117")**
[https://bbs.archlinux.org/viewtopic.php?id=184117](https://bbs.archlinux.org/viewtopic.php?id=184117)

---

### Post by verymadpip on 2014-12-26
Already tried acpi=off.
It disables the wireless adapter in the machine & also the battery monitor & causes graphical corruption when trying to shut down, so I can't tell what's actually happening.
No settings for acpi in UEFI settings.  Woeful, as I say.
Legacy mode is off.

I've just tried running the Live USB in legacy mode & the shutdown issue is still there.
I think it's pretty much game over.

---

### Post by oldfred on 2014-12-26
The thread with the Arch user also mentions that you must have the newest UEFI from HP.
And it said Lubuntu worked where Arch did not?

---

### Post by verymadpip on 2014-12-26
The bios on my machine is F14, the one on HP's website is F12?
Surely the one already installed is newer?  System info states it's from July whereas the HP download file is from June.
I'm confused to heck.

---

### Post by oldfred on 2014-12-26
I would think f14 is newer than f12.

---

### Post by verymadpip on 2014-12-27
Hi oldfred.
Thanks for putting so much time into this with me.
It's a shame about the shutdown/restart nonsense, as that's the fly in the ointment here.
I think I'm going to call it a day trying to dual boot on this hardware, before I do some real damage with hard shutdowns.

Thanks again.

---

### Post by oldfred on 2014-12-27
Good luck and have a Happy New Year.

I know others also have given up. Vendors & Microsoft are just making it too difficult to use PC as we have always used a PC and they want it to be just a Windows machine. :(

---

### Post by verymadpip on 2014-12-27
Yeah.  The paranoid conspiracy theorist in me is telling me it's a deliberate thing HP & Microsoft have concocted to prevent me from running anything but Windows 8.1 on the machine.
(Even though that's probably not the case).
I feel a little irked that I can't do what I want to do with something I have purchased.
I'm sure there'll be something in some small print somewhere that says I don't really own the machine for some outlandish reason...

Thanks again oldfred.
You have a good New Year too :)

---

