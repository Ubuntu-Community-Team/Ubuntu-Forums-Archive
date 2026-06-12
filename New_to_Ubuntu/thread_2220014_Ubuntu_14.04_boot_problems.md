---
title: "Ubuntu 14.04 boot problems"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by bpashuta on 2014-04-26
Installed Ubuntu 14.04 and rebooted and the screen goes black and says:
      mounting /dev on /root/dev failed: no such file or directory
      mounting /sys on /root/sys failed: no such file or directory
      mounting /proc on /root/proc failed: no such file directory
      Target file system doesn't have requested /sbin/init.
      No init found. Try passing init=bootarg

I used a USB to install Ubuntu so I plugged the USB back in and tried an older kernel and didn't work. I have also tried to get into Ubuntu using the try ubuntu without install option and it just sticks to the purple load screen. I have also tried going into the boot parameters and changed ro to rw and quiet splash to nomodeset and then combined the two but still couldn't get into the desktop to run the terminal.

---

### Post by Bashing-om on 2014-04-26
bpashuta; Hi ! Welcome to the forum .

Looks like no operating system is found in the booting process.
So, what have you got for that initial booting medium > Are we looking at UEFI and the efi interface is not set up correctly ?

OR is this system booting with the legacy bios to Master Boot Record ?
Is ubuntu the sole operating system installed ? No ? Which system controls the booting process ?
Is there more than 1 hard disk installed ?

Can not boot the liveDVD even with the "nomodeset" boot option might indicate that you do have a UEFI system and also maybe 'secure boot' in force ?

Talk to us and advise us of what booting arrangement we are dealing with here.
[INDENT][INDENT]a world of possibilities
[INDENT][INDENT][INDENT]we are looking for that one
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bpashuta on 2014-04-26
Ubuntu is the only OS on the hard drive and there is only one hard drive installed.  I've gone into grub2 to get more information out of the HDD and these are the inputs and outputs that I get: 
grub> ls (hd0,msdos1)
            Partition hd0,msdos1: Filesystem type ext* - Last modification time 2014-04-27 02:56:00 Sunday, UUID 13b53e35-f525-4168-93ab-e27112276202 - Partition start at 1024 Kib - Total size 973882368KiB
grub> ls (hd0,msdos1)/
lost+found/ etc/ media/ var/ boot/ home/ mnt/ opt/ root/ run/ srv/ tmp/ usr/ initrd.img.old cdrom/ ubiquity-apt-clone/
grub> ls (hd0,msdos1)/boot/grub/
gfxblacklist.text i386-pc/ locale/ fonts/ unicode.pf2 gurbenv grubenv grub.cfg

---

### Post by Bashing-om on 2014-04-26
bpashuta; Welp.

The boot code has been found, and a file system identified. Are the system boot files available ?

From that grub prompt, what returns:
```

ls -la (hd0,msdos1)/boot/grub/grub.cfg
ls -la (hd0,msdos1)/vmlinuz
ls -la /initrd.img

```
Now if all the above have positive results, try and boot:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

``` 

else we are going to consider (RE-)installing grub from the liveDVD.

[INDENT]maybe yes
[INDENT][INDENT][INDENT]but I do expect no
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bpashuta on 2014-04-26
the code ls -la (hd0,msdos1)/vmlinuz came back with error :file '/vmlinuz' not found

---

### Post by bpashuta on 2014-04-26
the code ls -la /initrd.img came back with error: file '/initrd.img' not found

---

### Post by Bashing-om on 2014-04-26
bpashuta; Welp.

Like I advise, not unexpected, just to make sure was all.

OK, let's try and re-install grub from the liveDVD:

Boot up the liveDVD to terminal:
Terminal commands:
```

sudo mount /dev/sda1 /mnt ##because sda1 is where the 'root' file system is installed to
sudo grub-install --boot-directory=/mnt /dev/sda ##because we want the boot code installed to the MBR of that hard drive
sudo umount /mnt ##because we are all done

```

Reboot and reset bios to boot the hard drive.
what now results ? If all boots good. Make sure all stays good ->
```

sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```

[INDENT]when the going gets tough
[INDENT][INDENT][INDENT]the tough get going
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by bpashuta on 2014-04-26
Okay...when I boot up the laptop using my USB I go into the advanced menu and click on try ubuntu without installing this time. Now, I'm getting stuck on the purple ubuntu loading screen and when I press ESC to find out whats going on I get:
stdin: Not a typewrite
stdin: Not a typewriter
stdin: Not a typewriter
umount: can't umount /cdrom: Device or resource busy
/init: Line 7: can't open /dev/sr0: No medium found

That repeats like 4 more times then I get this.
mktemp: No space left on device
cp: write error: No space left on device
cp: write error: No space left on device

---

### Post by Bashing-om on 2014-04-26
bpashuta; Yuk !

That is beyond anything I have experienced, I have no idea what is not taking place.

Is this a viable thing you can do -> burn to a DVD ? 

Maybe that USB write is bad ? -> and thus the install was bad ?
Check the .iso :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

Burn the .iso as an image (NOT data !)  at the slowest rate:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Boot that liveDVD to the boot options menu and verify the Burn -> "check disk for defects".


Off topic: I am going to go do yard work ( mowing), I will be back in about 3 hours.

where there are solutions
[INDENT][INDENT][INDENT]there are no problems[/INDENT][/INDENT][/INDENT]

---

### Post by bpashuta on 2014-04-26
I can't burn a DVD at this moment because I just have the one laptop right now but once I get a Bootable DVD and do the above steps I will get back in touch

---

### Post by Bashing-om on 2014-04-26
bpashuta; Roger that .

I feel in a problematic situation, there is just too much room for error with a USB - not that when it is right it is not good !
Here it is one more thing to eliminate in isolating a problem. The DVD once checked and verified is rock steady and reliable.

I expect I will still be here ->
[INDENT][INDENT][INDENT]we can do this
[/INDENT][/INDENT][/INDENT]

---

### Post by Aptiva on 2014-05-02
Sadly I'm also having issues getting 14.04 to boot and it seems my issues are the same as OP.

> **bpashuta said:**
> Ubuntu is the only OS on the hard drive and there is only one hard drive installed.  I've gone into grub2 to get more information out of the HDD and these are the inputs and outputs that I get: 
grub> ls (hd0,msdos1)
            Partition hd0,msdos1: Filesystem type ext* - Last modification time 2014-04-27 02:56:00 Sunday, UUID 13b53e35-f525-4168-93ab-e27112276202 - Partition start at 1024 Kib - Total size 973882368KiB
grub> ls (hd0,msdos1)/
lost+found/ etc/ media/ var/ boot/ home/ mnt/ opt/ root/ run/ srv/ tmp/ usr/ initrd.img.old cdrom/ ubiquity-apt-clone/
grub> ls (hd0,msdos1)/boot/grub/
gfxblacklist.text i386-pc/ locale/ fonts/ unicode.pf2 gurbenv grubenv grub.cfg

I have the same output when using these commands with the exception of the partition size, so I know it can see the fs.

```
Partition hd0,msdos1: Filesystem type ext* - Last modification time 2014-05-02 14:12:38 Friday, UUID 7cbb8357-823e-43ab-9f87-aa160743d0a8 - Partition start at 1024KiB - Total size 233284608KiB
```

The drive is a Samsung 840 Pro Series 256GB SSD on a SATA3 port running in AHCI mode. 

> **Bashing-om said:**
> bpashuta; Welp.

The boot code has been found, and a file system identified. Are the system boot files available ?

From that grub prompt, what returns:
```

ls -la (hd0,msdos1)/boot/grub/grub.cfg
ls -la (hd0,msdos1)/vmlinuz
ls -la /initrd.img

```
Now if all the above have positive results, try and boot:
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

``` 


Now when I run the 3 ls commands I get no error at all so I know the files are there. I can mount the drive using the LiveUSB I created using Unetbootin and I can use nautilus to look through the file system. The files are there upon visual inspection and seem to be symlinks to the real vmlinuz and initrd.img.

When I try the last 3 commands to boot the computer, I get the same error on boot:

```
Kernel panic - not syncing: No init found. Try passing init= option to kernel. See Linux Documentation/init.txt for guidance.
```

Now instead of using the vmlinuz and initrd.img I attempted to call the 2 directly like so:

```
linux (hd0,msdos1)/boot/vmlinuz-3.13.0-24-generic root=/dev/sda1 ro
initrd (hd0,msdos1)/boot/initrd.img-3.13.0-24-generic
boot
```

After this I still ended up with the same kernel panic.

I have reinstalled Ubuntu and Grub many times from the LiveUSB and the MD5 was correct. Unfortunately I'm in the same boat as far as not being able to burn a DVD, but I have used the same exact method to install Ubuntu on numerous machines successfully (including this one I'm working on now) using the same USB Flash Drive.  13.10, 13.04, and 12.04 have graced this machine and thumb drive at one point or another, but I have made sure I clean the thumb drive and the hard drive before I do any fresh install(never dirty installs or upgrades.... force of habit because of the problems that usually arise), so I'm at a loss.

Detailed rundown of my machine which is 100% stock speeds and voltages:

AMD Phenom II x6 1090t Black Edition @ 3.2GHz
Gigabyte GA-870A-UD3 Rev 2.1 mobo (non EFI/UEFI as this revision didn't have the proper bios chips to support the size of the EFI bios from gigabyte until revision 3.1)
16GB Kingston HyperX DDR3 @ 1600MHz in Dual Channel Mode
Samsung 840 Pro Series 256GB SSD (partitioned 2 ways 232GB as ext4 and 1GB as swap) on SATA3 6.0GB/s port 0
Asus Nvidia ENGT240 1GB PCI-e x16
LG BD Rom/DVD-RW
Thermaltake 750w PSU


I have another HD which will go into the machine after I work out the Linux problems. I'm installing Linux first, then removing the drive and installing Windows 7 Pro 64 bit on a seperate WD 1.5TB SATA3 HD which will end up on SATA3 6.0GB/s port 1, but only after I get my main OS installed first ;)


Edit: Upon closer inspection, 2 lines above the panic error, it tells me "Failed to execute /init"

---

### Post by Aptiva on 2014-05-02
So I kept searching for an answer while I waited for a reply and I found something that worked to fix this. The problem seems to be creating the USB via Unetbootin. To try my solution you will either need a working 14.04 install (which you said you only have the 1 laptop so you'll need to use the Unetbootin created LiveUSB and another seperate thumb drive/SD Card)

The LiveUSB works fine, but the install doesn't work. Here's how I managed to fix it:

I used the LiveUSB I created in Unetbootin to create a NEW USB (on a seperate disk) using usb creator from command line.

1. Open a terminal by pressing Ctrl + Alt + T
2. Type "usb-creator-gtk" and press enter
3. Select the ISO in the top box. If you do not see it, click "Other..." and navigate to the ISO
4. (WARNING: DRAGONS AHEAD) Select the USB Thumb Drive / SD Card (which ever you use) in the bottom box. I recommend you erase it so there are no files that may cause conflict. If there is something you want on the drive, move it off the flash drive.
5. Optional Step: If you want to be able to use the flash drive to save files, select an amount of space for user files.
6. Click "Make Startup Disk" and wait.
7. Reboot the machine and remove the Unetbootin created flash drive and boot from the new one you created.
8. Install as normal and reboot
9. Enjoy!

I found this thread here:
[http://ubuntuforums.org/showthread.php?t=2219493](http://ubuntuforums.org/showthread.php?t=2219493)

They said to use a working install, however like the OP I didn't have a working install and went out on a limb and tried it this way and it worked perfectly the first time. I have a fully functional install as the sole OS (at present) and the problem I had was solved.  To be honest you don't have anything to lose by trying this except a few minutes of time, so it may be worth a shot!

---

### Post by Bashing-om on 2014-05-02
@ Aptiva; Wow,

Wonderful, thanks for the sharing.

[INDENT][INDENT]as I live and learn
[/INDENT][/INDENT]

---

