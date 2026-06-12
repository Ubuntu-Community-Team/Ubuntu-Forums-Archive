---
title: "Stuck in Reboot Cycle"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by pwn2king on 2013-05-17
I'm running a Dell Inspiron with windows 8, I turned off the legacy and uefi boot in order to install 13.04. It worked and then I was upgrading(?) to Gnome 3.8 for better visuals or so I thought, while it was installing I stepped away from the computer, it went into suspense and corrupted itself, so I've been told. 

I installed ubuntu only once I was able to load it, so there is no windows OS on it. 

What it won't do:  boot ubuntu, load cd/rom, what i download through the internet is installed via command line, but cannot use it as will not boot to the OS. 

What it will do: Boot to recovery mode, allow me to enter tty command line. command line in recovery mode. connect to the internet. It will boot an external floppy, and this is my last resort. I will try and load a windows program via floppy, boot cd and install OS then wipe the entire thing again. 

I do not know enough line commands to repair grub, move files or change them. 

in the few times it recognizes the cd/rom, it will spin down, boot to the blu Gnome screen, give me a message about the cd "not ready or out to lunch", so its not useable. 

out of the 12,000 ubuntu wizards out there in this forum, somebody has the answer, please help. I have a nice 1tb, 6gig paper weight that can make a nice drum roll. ](*,)

---

### Post by cub on 2013-05-17
Can you use another pc to get a ubuntu bootable usb stick? And does the pc support to boot from an usb? If so, that might be a way to start up a live ubuntu or do a reinstallation.

---

### Post by grahammechanical on 2013-05-17
If it boots to recovery mode, then you get a Grub menu. Yes? Are you not able to enter the boot system (BIOS/EFI - whatever)? You need to check if the DVD drive still has boot priority over the hard disk. 

Have you tried recovery mode>resume? You say it won't boot Ubuntu but what happens? What you see on the screen may be a clue to what is going wrong. What version of Ubuntu are you using that has a blue Gnome screen? Ubuntu Gnome?

Regards

---

### Post by pwn2king on 2013-05-20
thanks for replying: Yes i have another computer that im using to try and repair the first. the pc does support boot from usb, floppy and cd/rom, the problem is that there is a disconnect between the boot process and the ubuntu system already onboard. In the command line i have two partitions, /sda1 and /udev, sda1 seems to be the main one. the computer will absolutely not read the cdrom or usb, only floppy disk.

---

### Post by pwn2king on 2013-05-20
Thanks for reply: Yes have command line, the grub menu is limited and for the most part useless, whatever it does, i cannot "see" the results. I do not have graphical mode access to run gedit or anything else. I can download, but cannot access, the most maddening thing I have ever seen. no cannot get into bios/uefi, i turned those off to install ubuntu. I am running 13.04, i was adding Gnome 3.8, stepped away, it froze, crashed and burned, and is stuck in this groundhog loop of login. 
The blue screen will, when i boot in f12, for advanced ubuntu recovery screen, will say that the device UUID etc is not present or can't mount it, press S or M, but that does not work either. 
I tried a network install, but again have no graphical ability...
I tried ubuntu rescue disks, from floppy called all in one, it can load, but it won't load the cd/rom. 
If I can only get it to read the cd/rom..i can just do a clean re-install. 
i have access to command line in recovery mode and in tty mode. 
"whew", thanks at least for looking into this..I'm combing the forums and internet, lots of similiar cases, but they have the luxury of a working cd rom, all i have is the hope of the floppy.

---

### Post by pwn2king on 2013-05-20
Im in the recovery menu: 
 resume.
clean.
dpkg
 failsafex
 fsck
grub
ntework
root
system-summary

---

### Post by pwn2king on 2013-05-20
system summary: 

system mode: read-only mode
CPU information 4x2501MHZ
Network connectivity: none

Detailed Disk Usage:
File System: /dev/sda1    Size: 912G   Used: 266G   Avail: 840G   Use% 3%   Mounted on /

File System: udev           Size: 2.9G    Used: 0         Avail:  2.9G   Use%   0% Mounted on /dev

File System: tmpfs         Size: 583M  Used: 876k     Avail:  582M  Use%   1% Mounted on /run

File System: none           Size: 583M  Used: 876k     Avail:  582M  Use%   1% Mounted on /run/lock

File System: none           Size: 583M  Used: 876k     Avail:  582M  Use%   1% Mounted on /run/shm

Sofware RAID State: No Software RAID detected (mstat)

LVM State: No LVM detected (vgscan)

Detailed Memory Use: 

Mem:  TOTAL: 5827    Used: 125    Free: 5701   Shared: 0    Bufferes: 9   Cached: 35

-/+ buffers/cache: 

Swap:    total: 0    Used: 0     Free:   0 

Detailed Network Configuration: 

System Database (APT)

Database is consistent:L unkown (read-only filessystem)

When i enter to update grub, it goes to screen "continuing wil remount your / filesystem in read/write mode and mount an other filesystem defined in /etc/fstab. 
Do you wish to continue"...I choose yes, and it shows underneath in a command line: 

fsck from util-linux 2.20.1
/dev/sda1: clean, 345812/60669952 files, 10470998/242653952 blocks 

and from there i get nothing more. 

I have tried enter fstab, and cannot.
I have tried to mount the cd/rom...but get error message that it's not there..

hope the information gives some clues.

---

### Post by pwn2king on 2013-05-20
Here is some more info from TTY1 command line:

Build Operating System: Linux 3.2.0-37 -generic x86_64 ubuntu
Current Operating System: Linux (machine name) 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:3f5:2f3 UTC 2013 x86_64
Kernel Command Line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=505b 451f-cc59-432e-8f85-c75081ad0f520 ro quiet splash vt.handoff=7

---

### Post by pwn2king on 2013-05-20
And this from Gnu Grub version 2.00-13Ubuntu3 

setparams "Memeory test (memtest86+, serial console 115200)'

insmod part_msdos
insmod ext2
set root= 'hd0,msdos1
if [ x$feature_platform_search_hint = xy ]; then 
search --no-floppy --fs-uuid -set=root --hint-bios=hd0,msdos1 --hint-efi-hd0,msdos1 --hint-baremetal=ahci0,msdos1 505b451f-cc59-432e-8f85-c75801ad0f52
else
search --no-floppy --fs-uuid --set=root 505b451f-cc59-432-d-8f-85-c75081ad0f52
fi
linux16     /boot/memtest86+.bin console=ttyS0,115200n8


at the bottom of the screen it says: 
Minimum Emacs-like screen editing is supported. TAB lists completeions. Press Ctrl-x or F10 to boot, Ctrl-c or F2 to for a command line or ESC to discard edits and return to the GRUB menu. 

Is it possible to edit in this screen and change the UUID settings so that the CD/ROM can be recognized...ohh man...I need some coffee.

---

