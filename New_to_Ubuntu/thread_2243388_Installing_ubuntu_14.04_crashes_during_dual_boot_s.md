---
title: "Installing ubuntu 14.04 crashes during dual boot setup"
date: 2014-09-08
forum: New to Ubuntu
---

### Post by buzzkillington on 2014-09-08
Hi Ubuntu forums i'm new!

i've used 12.04 a bit but don't have much experience booting things ;). My goal is to install a dual boot setup of windows 7, ubuntu 14.04 and a data partion (i think FAT32 ) on my desktop,  i installed windows 7 first and am now trying to boot ubuntu 14.04 off a usb drive.

i get purple screen with white box and dude down the bottom and then just a flashing (_) no response from keyboard

my system is
SSD 256gb (windows currently here)
HDD (future data partion)
nvidia geforce gtx 780ti (forums suggest graphics card drivers might be an issue?)

i plan on putting the ubuntu os and its swap on the SSD

anythoughts?

---

### Post by fantab on 2014-09-09
Try booting with '[nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")' boot option. It disable your GPU temporarily and loads ubuntu in 'failsafe' graphics mode.
Later, after installing Ubuntu, we can install an appropriate graphics driver.

I would put the SWAP partition on the HDD. Also the 'data partition' should be NTFS if you plan on sharing the partition between Windows and Linux.

If you need help with setting up partitions then post back the output of the following, booting from Ubuntu DVD/USB and user Terminal [ctrl+alt+t] to run the commands:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by buzzkillington on 2014-09-09
Gets a bit further with "nomodeset" enabled, shows the ubuntu 14.04 and the 4 dots flashing before going to a black screen.

My boot loader is currently set to 1.usb drive 2.usb drive with UEFI above it in red 3.SSD 4.HDD

---

### Post by fantab on 2014-09-09
Is it Windows8 on the machine?
Post the output of the commands, as requested earlier.

---

### Post by buzzkillington on 2014-09-09
Windows 7 is currently on the machine
The ubuntu os isn't yet installed so i don't know how to run those commands
Looking from the working windows 7 boot my disk partions are 

SSD
System reserve 350mb NTFS 
C: 238GB NTFS 

HDD
unallocated 2000gb
unallocated 746gb


i tryed shrinking the C: drive by 90GB and then trying to boot the ubuntu image but had the same issue as early with the flashing _ and with "nomodeset" enabled a purple ubuntu screen with flashing dots then black screen.  If i hit f6 durring the purple screen it says "carn't unmount device or resource busy" for two lines then a whole bunch of things stopping (first word is stopping then stuff i don't understand) then black screen.

---

### Post by grahammechanical on 2014-09-09
You may need to try a combination of those F6 options

---

### Post by yancek on 2014-09-09
Did you verify the download of the Ubuntu iso by doing an md5 checksum?  Might be a bad download.

---

### Post by buzzkillington on 2014-09-09
downloaded iso hash is good, i've tried all the F6 options but get the same results.  Do i need to have unallocated space on my SSD?

---

### Post by oldfred on 2014-09-09
Is motherboard/system also new? And may be both UEFI and BIOS.
Some motherboards also need other boot options in addition to nVidia card needing nomodeset. What system is this?

Also do not use FAT32 for a larger data partition. Ok if small, but FAT32 cannot have any file over 4GB and has no journal so chkdsk can take forever or may not work where NTFS has journal and may allow fixes if corrupted.

---

### Post by buzzkillington on 2014-09-09
The motherboard is new, its a gigabyte z97x-gaming gt
i think i will use NTFS for the data partition

---

### Post by oldfred on 2014-09-09
What brand Z97? Different ones have minor issues.

       Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)

Asrock also has compatiblitiy issues if hard drive, SSD or DVD is plugged into a asmedia port. Only use standard SATA ports.

Older Gigabyte needed this not sure about newer ones.
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
And/or iommu boot parameters.

---

### Post by buzzkillington on 2014-09-10
its a gigabyte z97x-gaming gt g2 gaming motherboard

---

### Post by buzzkillington on 2014-09-10
I couldn't find the iommu option in the bios but the VT-d option is enabled are they the same thing?.
The drives are in sata express ports

---

### Post by oldfred on 2014-09-10
This site tested a slightly different Gigabyte model.

[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

replace quiet splash with nomodeset, so you see the boot loading process. The last posted is not usually the issue but in the commands above may mention the failure or issue.

---

### Post by buzzkillington on 2014-09-10
something dosn't look right but its a bit too fast to read, is there a way to slow this down?

i tryed [http://www.linuxquestions.org/questions/linux-general-1/is-it-possible-to-slow-down-the-kernel-boot-process-838040/](http://www.linuxquestions.org/questions/linux-general-1/is-it-possible-to-slow-down-the-kernel-boot-process-838040/)
but i'm not sure i'm adding the delay to the right part of grub.cfg

Ctrl q and s work for the first part but not the second, i'm not sure what those processes are called

---

### Post by oldfred on 2014-09-10
Have you also included nomodeset?
Sometimes you can get to a point where you can get to terminal, or it has booted, but gui/desktop has not correctly loaded.

 Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7
[https://help.ubuntu.com/community/UsingTheTerminal/](https://help.ubuntu.com/community/UsingTheTerminal/)
In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal

---

### Post by buzzkillington on 2014-09-10
yes i had to manually enter the nomodeset to relpace quite splash in the boot options as the f6 nomodeset gui option didn't do anything.  With nomodeset entered i no longer see the splash screen but scrolling text.  

The diskcheck crashs same as above unless nomodeset is enabled in which case it says it passes.

i tried Ctrl-alt-t during black screen but there is no response

---

### Post by oldfred on 2014-09-10
When it stops does it still show anything that is an error. 
Often it stops on battery check, but that is not the error, it is several lines above that.

---

### Post by buzzkillington on 2014-09-11
Before the black screen during the text scrolling there are a few fails which come up on the right hand side but they are too fast for me to read there description on the left, when i tried 12.04 it had more fail messages then 14.04 but end result of a black screen was the same.  There are no hanging error messages, but just goes straight to a black screen.

I would have though that there would be some kind of tool for slowing down these messages as installation issues must be very common (for computing in general) but i car't seem to find any.  Do they exist?

---

### Post by buzzkillington on 2014-09-11
Ok i wasn't using the UDFI usb, using it with nomodeset enabled i get to the installer, at this point i set on the SSD
one partition 75gb, Primary, ext4, mount point /
one partition 34gb, logical swap area
and put the boot loader on /dev/sdb  (as sda is the 3tb drive and i left it alone) 

i hit install, everything looked good then when rebooting it showed purple outer screen black inner with no text then went to black screen

In frustration i tried just installing ubuntu using the erase disk and install ubuntu option in the installer, however this had the same issue as above
and now my drives look very messy.  This is a new machine so i don't have any data i'm worried about losing if having to re install windows is now required.

---

### Post by oldfred on 2014-09-11
If you needed nomodeset to install you then still need it for first boot or until you install proprietary video driver.

With only Ubuntu installed, you do not get grub menu. With BIOS you hold shift key from BIOS until menu, but with UEFI you hit escape key to get menu. Then you can add nomodeset.

I normally suggest a small swap for anyone with 4GB or more of RAM. Only if hibernating would you need swap equal to RAM in GiB not GB (or about 10% more).

I also suggest 20 or 25GB for / (root) if you have separate /home or data partition(s) for most of your own data.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I also like to have available an efi partition on every drive, so you could add another install and boot that drive without any other drive when you have more than one drive and drive is large like your data drive.

I use Ubuntu not Knoppix, but like this logic.

 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
     
 
    [FONT=arial][SIZE=2][COLOR=black][FONT=arial][COLOR=black][COLOR=black][FONT=&quot][EMAIL="debnap2@sbcglobal.net"][SIZE=3][/SIZE][/EMAIL][/FONT][/COLOR][/COLOR][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by buzzkillington on 2014-09-12
Ok thanks, i can now install and run ubuntu  standalone but only with nomodeset enabled, the nvidia driver options in additional drivers cause the graphics to crash as does [COLOR=#DFDFDF]sudo apt-get install nvidia-current.  [/COLOR]  

Also after re-installing windows(erasing the ubuntu dist) and re-partitioning the drive i went through the ubuntu installer and now it dosn't see any of the partions, i think this has something to do with partition table being screwed because of all my fluffing around.

---

### Post by oldfred on 2014-09-12
Ubuntu does not normally correctly see Windows that is hibernated or needs chkdsk.
But the installer does not seem to see Window 8 at all.

But it looks like that bug has just been fixed as it was an os-prober issue. But will not be in any current version installers.
       Reinstall says overwrite Ubuntu but it also erases existing Windows. 
Sept 2014 Fix being released for one drive installs, but mulitple drive installs must use Something Else.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

### Post by buzzkillington on 2014-09-13
I tried a few things
 with windows 7 on the SSD when booting into ubuntu i can't see the windows partitions (in demo or installer) and when i tried to install it erased windows 7.  Some one suggested this may be due to differnt stata modes being used by the different OS's so i tried installing both again with EDI and AHCI but same issue.  I also get a warning about GPT signatures, and left over GPT data so i ran i ran both *bootrec.exe /FixMbr and **bootrec.exe /FixBoot  but ubuntu still dosn't see the windows partitions and gives the signatures error.*

Any way now when i try to install ubuntu on the SSD i get a black screen after the first reset (still need to enter in nomodeset).

Can i revert my disks back to factory settings via the bios?

---

### Post by oldfred on 2014-09-13
If you install Windows 7 in BIOS mode over a UEFI install it converts drive to MBR(msdos), but does not correctly delete backup gpt partition table. Then you have to use fixparts to remove backup gpt data.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

With hardware that is UEFI, you do have to be consistent on how you boot install media. How you boot it is how it installs and you want all systems installed in same boot mode, either UEFI or both BIOS.

---

### Post by buzzkillington on 2014-09-14
Thanks i have been consistent with both drives having the same sata mode.
software center says the fixparts package is of bad quality and fails on install, i tried using Boot repair using this guide 
[http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)
and it ran however now when i boot i can hear the bongos from ubuntu but get a black screen i carnt get the menu where i can enter in the nomodeset either (using esc had one time when it worked but booted into a strange ubuntu dist (display option locked to built in screen?)  but am now unable to reproduce) f12 drive option i can enter nomodeset but get black screen with bongos

using the live usb the partitions are 
sdb1 ntfs boot (where the windows install should be)
sdb2 extended 
sdb5 ext4
sdb6 unknown (should be the swap

---

### Post by oldfred on 2014-09-14
If you selected encrypted /home then swap will always be unknown as it also is encrypted and cannot be parsed to know what it is.

fixparts is not in repository, so there is no way to install from Software Center. You have to follow procedure on link for downloading and running it.
If you do here sounds, you are booting, but have video issues.

Have you tried second or recovery boot entry? Even without grub menu if you press down arrow once that usually changes boot entry. Press must be after BIOS but before grub starts booting so timing can be important. Not sure now with submenus if two presses required?
Have you tried adding nomodeset?
What video card/chip do you have?

If in UEFI mode then escape key should show grub menu.
But if you have extended partition you are in BIOS Mode and then you must hold shift key from BIOS until menu appears.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1 if nomodeset does not work, often Intel video chips
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by buzzkillington on 2014-09-15
Pressing down after bios menu brings me to GRUB
i have tried the folliowing additions to the linux line 
[COLOR=#000000]nomodeset[/COLOR]
[COLOR=#000000]acpi=0[/COLOR]
[COLOR=#000000]acpi_osi=linux[/COLOR]
[COLOR=#000000]acpi_backlight=vendor[/COLOR]
[COLOR=#000000]noalpic[/COLOR]
[COLOR=#000000]i915.i915_enable_rc6=1[/COLOR]
[COLOR=#000000]video=1280x1024-24@60[/COLOR]
[COLOR=#000000]video=VGA-1:1280x1024-24@60[/COLOR]
[COLOR=#000000]nouveau.blacklist=1[/COLOR]
[COLOR=#000000]libata.force=noncq
[/COLOR] Some stop with the scrolling text displayed then bongos and others stop text scrolling and no bongos.

Recovery mode boot gives me the recovery menu, i cant seem to run failsafeX or any of the other options as i hit enter it outputs fsck from util-linux 2.20.1 /dev/sdb3: clean, XXXXXXXX files, XXXXXXX / xxxxx blocks

my graphics card is a nvidia geforce gtx 780ti on a z97x-gaming gt g1 board with a i7-479k processor

i also tried Legacy Rom option in bios, no change

---

### Post by oldfred on 2014-09-15
If you have monitor plugged into video card not motherboard Intel video you need nomodeset, but may need other parameters.

Some older Gigabyte board needed this, not sure about your new one.
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

 Gigabyte GA-Z87X-UD3H, Ubuntu 13.10, and Intermittent External USB Drive Failure 
[http://ubuntuforums.org/showthread.php?t=2194155](http://ubuntuforums.org/showthread.php?t=2194155)

Have you made sure UEFI/BIOS is updated to the current version from Vendor?

If in recovery mode you can then install the nVidia driver from command line. Then you would not need nomodeset, but still may need other parameters.

sudo apt-get update
sudo apt-get upgrade
      
 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

Install nVidia, do not install a second version without totally purging any previous versions, they will conflict:
      
 Shows versions in repository:
sudo apt-cache search nvidia-sett*

 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates
sudo apt-get install  nvidia-current-updates 
sudo apt-get install nvidia-settings-updates
sudo dpkg-reconfigure nvidia-current-updates 
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.

 shows various ways to install:
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

I prefer to install from repository, but there are ppa with precompiled newest versions or direct downloads. Again if installing from different sources you must purge first.
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
      
 Shows various install methods for nVidia. 13.04 but still the same
[http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

 Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)

---

### Post by buzzkillington on 2014-09-16
I upgrading my bios from f4 to f5, and wiped both disks and gave them new partition tables
i put two ntfs partions on the HDD and first installed windows on the SSD shrank the volume and then put ubuntu in new space (SSD).  Now weirdly when i boot into the HDD i get windows (windows is the only option on its boot loader) and ubuntu if i boot from the SSD? (ok using parted it looks like windows got installed on the HDD htfs partion its late and i'm tired may have been my error) i have the same issues as before with the graphics on the ubuntu boot, i tried to update the drivers from recovery mode command line 

first i got write priverlge and mounted things [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

but when i use apt to update or install things it carn't resolve 'au.archinve.ubuntu.com' as well as 'security.ubuntu.com' with Unable to fetch some archives shown
and carn't install the drivers

I checked ifconfig an my RX and TX are the same and everything i ping i get ping: unknown host blarblarblar
making me feel like i'm not connected to the internet but i don't know how to resolve

oh and my board has VT-d enabled (which is the same as IOMMU?)

---

### Post by oldfred on 2014-09-16
If you had BIOS set to boot hard drive when you installed Windows to SSD, Windows will put the 100MB boot partition on the hard drive. It installs boot partition and boot loader to MBR of drive set as default in BIOS. Grub just installs to whatever drive is seen as sda, which may or may not be the first drive. Some BIOS even promote flash drive to sda and really confuse things.

If it now is Internet issues, I suggest a new thread with that in the title.

Include as much info on computer and specifically what Ethernet card/chip or Wireless chip you have.
My systems have always just worked so I have not paid attention to details, but they often want all this type of info.

lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

---

### Post by buzzkillington on 2014-09-16
[http://ubuntuforums.org/showthread.php?t=2244483&p=13123225#post13123225](http://ubuntuforums.org/showthread.php?t=2244483&p=13123225#post13123225)

i'll report back if/when i get this figured out

---

### Post by oldfred on 2014-09-16
Did you check UEFI settings for IOMMU?

If you have monitor connected to motherboard not video card totally different boot parameters are also required.

       # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

 Gigabyte 970 chipset board  - GRUB_CMDLINE_LINUX="iommu=soft" and Disable iommu in bios

---

### Post by buzzkillington on 2014-09-17
Where are UDFI settings?  I carn't find any options for IOMMU in my gigabyte UEFI dualBIOS (is VT-d is the same or has the same function as IOMMU?) my VT-d is enabled.

my monitor is attached to my graphics card.

my boot mode selection (under windows 8 features in the bios/uefi ) says UEFI and BIOS.

---

### Post by Avijit_ on 2014-09-17
ubuntu 14.04 is 64 bit or 32 bit? If it is 32-bit and you are using new computers with higher RAM it may cause problems. Try with 64 bit then

---

### Post by buzzkillington on 2014-09-17
its a 64 bit image

---

### Post by oldfred on 2014-09-17
The new UEFI have so many settings it is hard to find things. And each vendor is different or puts them on different screens in UEFI menu.
Do not even know what IOMMU is but that has been an issue with Gigabyte. Not sure then what VT-d is or does.

On my much older Gigabyte I had to take photos of all the settings as I did have to change a few. But then installing new BIOS update reset everything back to defaults and I had to got back and find what settings I needed.

---

### Post by riverguy99 on 2014-09-18
I had the same problem with 14.04 crashing during boot-up, and on three machines that I had recently "upgraded" from 12.04.  Also I could never get my dual displays to work in 14.04, in spite of many suggested fixes from the Forum folks.  My cure:  Since I had been running 12.04 for two years WITHOUT A HITCH, and since 14.04 really showed me no improvements worthy of the hassle, I re-installed 12.04 again (clean install) and am once more running a flawless OS that works everything with any issues at all.

Maybe not the most high-tech solution, but it works!  No more boot-up crashes, blank screen or error messages, my wireless printers set themselves up with no help from me, and best of all, my dual displays worked and configured themselves right out of the box.

---

### Post by Michael_McKenney on 2014-09-18
root@ubuntu:/home/michael# dpkg -l | grep linux-image
rc  linux-image-2.6.38-10-server                          2.6.38-10.46                                        amd64        Linux kernel image for version 2.6.38 on x86_64
rc  linux-image-2.6.38-11-server                          2.6.38-11.50                                        amd64        Linux kernel image for version 2.6.38 on x86_64
ii  linux-image-2.6.38-12-server                          2.6.38-12.51                                        amd64        Linux kernel image for version 2.6.38 on x86_64
rc  linux-image-2.6.38-8-server                           2.6.38-8.42                                         amd64        Linux kernel image for version 2.6.38 on x86_64
rc  linux-image-3.0.0-13-server                           3.0.0-13.22                                         amd64        Linux kernel image for version 3.0.0 on x86_64
rc  linux-image-3.0.0-14-server                           3.0.0-14.23                                         amd64        Linux kernel image for version 3.0.0 on x86_64
rc  linux-image-3.0.0-15-server                           3.0.0-15.26                                         amd64        Linux kernel image for version 3.0.0 on x86_64
rc  linux-image-3.0.0-16-server                           3.0.0-16.29                                         amd64        Linux kernel image for version 3.0.0 on x86_64
rc  linux-image-3.0.0-17-server                           3.0.0-17.30                                         amd64        Linux kernel image for version 3.0.0 on x86_64
rc  linux-image-3.0.0-21-server                           3.0.0-21.35                                         amd64        Linux kernel image for version 3.0.0 on x86_64
ii  linux-image-3.0.0-26-server                           3.0.0-26.43                                         amd64        Linux kernel image for version 3.0.0 on x86_64
rc  linux-image-3.11.0-13-generic                         3.11.0-13.20                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-14-generic                         3.11.0-14.21                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-15-generic                         3.11.0-15.25                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-17-generic                         3.11.0-17.31                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-18-generic                         3.11.0-18.32                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-19-generic                         3.11.0-19.33                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                         3.11.0-20.35                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                         3.11.0-22.38                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-23-generic                         3.11.0-23.40                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-24-generic                         3.11.0-24.42                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-26-generic                         3.11.0-26.45                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-33-generic                         3.13.0-33.58                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-35-generic                          3.2.0-35.55                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-36-generic                          3.2.0-36.57                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-37-generic                          3.2.0-37.58                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-38-generic                          3.2.0-38.61                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-39-generic                          3.2.0-39.62                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-40-generic                          3.2.0-40.64                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-41-generic                          3.2.0-41.66                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-43-generic                          3.2.0-43.68                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic                          3.2.0-49.75                                         amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-36-generic                          3.5.0-36.57                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-26-generic                          3.8.0-26.38                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-27-generic                          3.8.0-27.40                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-29-generic                          3.8.0-29.42                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-30-generic                          3.8.0-30.44                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-31-generic                          3.8.0-31.46                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-3.8.0-32-generic                          3.8.0-32.47                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-3.8.0-33-generic                          3.8.0-33.48                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-13-generic                   3.11.0-13.20                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-14-generic                   3.11.0-14.21                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-15-generic                   3.11.0-15.25                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-17-generic                   3.11.0-17.31                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-18-generic                   3.11.0-18.32                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.11.0-19-generic                   3.11.0-19.33                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic                   3.11.0-20.35                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic                   3.11.0-22.38                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-23-generic                   3.11.0-23.40                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-24-generic                   3.11.0-24.42                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.11.0-26-generic                   3.11.0-26.45                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic                   3.13.0-33.58                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-36-generic                    3.5.0-36.57                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-26-generic                    3.8.0-26.38                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-27-generic                    3.8.0-27.40                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-29-generic                    3.8.0-29.42                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-30-generic                    3.8.0-30.44                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-31-generic                    3.8.0-31.46                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-32-generic                    3.8.0-32.47                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-extra-3.8.0-33-generic                    3.8.0-33.48                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.35.42                                        amd64        Generic Linux kernel image
ii  linux-image-server                                    3.13.0.35.42                                        amd64        Transitional package.
root@ubuntu:/home/michael#

---

### Post by Michael_McKenney on 2014-09-18
installed synaptic and filtered on Linux-image and picked all the 2.x kernels to remove.

---

### Post by Michael_McKenney on 2014-09-18
cleaned up more of the kernels in Synaptic.  I can still get rid of more of them.  

root@ubuntu:/boot# dpkg -l | grep linux-image
rc  linux-image-3.11.0-13-generic                         3.11.0-13.20                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-14-generic                         3.11.0-14.21                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-15-generic                         3.11.0-15.25                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-17-generic                         3.11.0-17.31                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-18-generic                         3.11.0-18.32                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-19-generic                         3.11.0-19.33                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                         3.11.0-20.35                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                         3.11.0-22.38                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-23-generic                         3.11.0-23.40                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-24-generic                         3.11.0-24.42                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.11.0-26-generic                         3.11.0-26.45                                        amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-33-generic                         3.13.0-33.58                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-13-generic                   3.11.0-13.20                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-14-generic                   3.11.0-14.21                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-15-generic                   3.11.0-15.25                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-17-generic                   3.11.0-17.31                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-18-generic                   3.11.0-18.32                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.11.0-19-generic                   3.11.0-19.33                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic                   3.11.0-20.35                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic                   3.11.0-22.38                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-23-generic                   3.11.0-23.40                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-24-generic                   3.11.0-24.42                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.11.0-26-generic                   3.11.0-26.45                                        amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic                   3.13.0-33.58                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-36-generic                    3.5.0-36.57                                         amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.8.0-33-generic                    3.8.0-33.48                                         amd64        Linux kernel image for version 3.8.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.35.42                                        amd64        Generic Linux kernel image
ii  linux-image-server                                    3.13.0.35.42                                        amd64        Transitional package.
root@ubuntu:/boot#

---

