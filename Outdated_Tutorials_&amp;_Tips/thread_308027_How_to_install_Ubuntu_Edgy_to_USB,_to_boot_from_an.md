---
title: "How to install Ubuntu Edgy to USB, to boot from any USB bootable machine"
date: 2006-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by stuporglue on 2006-11-27
Robertar and I have been trying to get Edgy installed on an external USB HD for a few weeks and had no success. Hopefully this will work for some of you, or at least help.

Normal install methods weren't working (ie. selecting the USB disk as the install target) because grub would get messed up when installed on the USB drive. Even once grub was installed 'correctly', it would only work on the original computer with the original hard disk configuration. These problems would result in grub errors 15 and 21 .
                                                                                           
The following procedure worked for us, and allowed us to boot on a variety of USB bootable machines. I'm not a grub or Linux expert, so some of my details may be slightly wrong.   Please forgive me if they are.                                      
                                             
Installing Linux to an external HD
----------------------------------------

Goal: 
To get Linux to install on an external HD and boot from it on any computer which has a 'boot from USB' BIOS option.

Resources: 
* HP Compaq dc7600 desktop computer
* Western Digital 80 Gb USB, bus powered, laptop hard drive
   -- Several other models have now been tested, all have worked, although some drives have required the use of the text based installed available on the alternative install CD. 
* Ubuntu Edgy (6.10) Desktop install CD -- this procedure won't work with 6.06!

Procedure/Explanation:

1) Remove all internal hard drives from the computer, or disable the internal hard drives in the BIOS.
	* Grub by default installs to the first hard drive detected by the BIOS. The simplest way to ensure that it installs correctly is to make sure that the only hard drive available is the install target drive.

2) Connect the USB drive and boot from the Ubuntu CD. 

3) Run the Ubuntu installer
	* Just double-click the 'Install' icon on the desktop.

3.1) When the installer is done, "Continue using the live CD"

4) Mount the root partition of the newly installed Ubuntu
	* Run the Gnome Partition Editor (System-->Administration-->GNOME Partition Editor)
	* If running the Gnome Partition Editor doesn't mount the partition open a terminal and do the following: 
```
# Create a directory: 
mkdir newinstall
# Mount your new root partition
sudo mount /dev/sda1 newinstall
```

5) On the new root partition, modify the GRUB config file to allow computer-independent booting. 
	* It is named boot/GRUB/menu.lst
	* To edit it, open a terminal and type "gksudo gedit " then drag the file to the terminal, then hit return.  This edits the file as the super user.
	* Find the line that says "kopt=root=UUID=(Long HEX number here) -- copy the portion from 'root' through the end of the HEX number
	* Find all instances of 'root=/dev/sda1' (where sda1 is the partition you installed to) and replace it with the 'root=....' string you just copied
	* Save and close the file

5) On the new root partition, modify the GDM startup script to re-detect the graphics card at each login. 
	* Edit the GDM (Gnome Desktop Manager) script. It is named etc/init.d/gdm
	* To edit it, open a terminal and type "gksudo gedit " then drag the file to the terminal, then hit return.  This edits the file as the super user.
	* Add a blank line after the line that says "start)"
	* On this blank line, enter the text "dpkg-reconfigure -fnoninteractive --no-reload -phigh xserver-xorg" (with no quotes).
	* Save and close the file

6) Shut down, and you should be set! 


Issues: 

All BIOSs aren't created equal. In the current configuration, GRUB needs to be on hd0. On some computers, selection USB from the BIOS boot menu, USB is made hd0, on others it is not.
Solution: Set the boot order in the BIOS to be CDROM, USB, First HD

---

### Post by mickbw on 2006-12-03
I do not have the option to use the USB as a boot option, BUT the external drive does show up as a Hard Drive.  Should I leave it as hd0?  

Thank you for this guide.  

Michael

---

### Post by stuporglue on 2006-12-03
> I do not have the option to use the USB as a boot option
If you don't have an option to do a USB boot, I suspect it's not going to work no matter what. No number of changes on your USB disk is going to allow you to boot from it if your BIOS doesn't support it. If your BIOS does support it, there should be a 'boot from USB' option somewhere. 

OTOH, if you're using Smart Boot Manager or some such to start the boot process, I don't know what you'd have to do. I suspect that you'd still want grub on hd0, but I haven't tried it.

---

### Post by mickbw on 2006-12-03
I installed successfully and chose to continue using live desktop.  This is being done on an external Seagate 160 gb hard drive.  I unplugged the power supply for the main hard drive to ensure it was only being installed to the external.  

I went to gparted as instructed.  The ext3 partition (usbdisk) and the fat32 partitions opened up as you said they probably would.  The display for the ext3 partition looked like the following:  

/media/usbdisk/ 
/media/usbdisk/.¬&#9580;&#9556;
/media/usbdisk/.ƒC
/media/usbdisk/.
/media/usbdisk/any key.to
/media/usbdisk/éèí&#8992;)
/media/usbdisk/RRaA
/media/usbdisk/"&#9492;tv&#9508;&#9559;.
/media/usbdisk/&#948;XÉ.fs
/media/usbdisk/&#948;XÉmkdos.fs

Any ideas what to do now.  

One thing I did was before the installation I deleted all existing partitions from the USB drive.  This was done successfully but I forgot and left the gparted window open during the install.  I will try and re-do the install ensuring the gparted window is closed, but would appreciate any further insights you could give. 

Michael

---

### Post by mickbw on 2006-12-03
BTW, I did choose English as the language for the install.

---

### Post by stuporglue on 2006-12-03
> The display for the ext3 partition looked like the following:

/media/usbdisk/ 
/media/usbdisk/.¬&#9580;&#9556;
/media/usbdisk/.ƒC
/media/usbdisk/.
/media/usbdisk/any key.to
/media/usbdisk/éèí&#8992;)
/media/usbdisk/RRaA
/media/usbdisk/"&#9492;tv&#9508;&#9559;.
/media/usbdisk/&#948;XÉ.fs
/media/usbdisk/&#948;XÉmkdos.fs

...
but I forgot and left the gparted window open during the install. 

That looks like something didn't work out right. :-/ If you haven't already done a reinstall with gparted closed, you could run "sudo fdisk -l /dev/sda" where sda is your USB disk. This command will tell you what the partition table is saying. 

The installer opens its own gparted instance and closes it when you move on to the next step. If you had a gparted open the whole time, maybe there was some corruption from having two instances operating on the same disk at the same time?

---

### Post by mickbw on 2006-12-03
Thanks for the reply.

Okay, i have a completed install now.  I gave up doing the manual partitioning and accepted the default wipe of the drive, so I now have a huge ext3 partition and the 2 gig swap partition.  I disconnected my internal drive and before booting into the live CD and left the grub to the default location. 

If I do sudo fdisk -1, I get the following information:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19086   153308263+  83  Linux
/dev/sda2           19087       19457     2980057+   5  Extended
/dev/sda5           19087       19457     2980026   82  Linux swap / Solaris

```
Now the bad news.  Even after I make the changes to the menu.lst file I still get Error 18.  

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=53b01304-0084-4685-a06d-023732484307 ro
# kopt_2_6=root=UUID=53b01304-0084-4685-a06d-023732484307 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root UUID=53b01304-0084-4685-a06d-023732484307 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root UUID=53b01304-0084-4685-a06d-023732484307 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

I would appreciate any assistance in discovering what I did incorrectly.  I also made a backup copy of the original menu.lst file which follows:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=53b01304-0084-4685-a06d-023732484307 ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

Thanks,

Michael

---

### Post by stuporglue on 2006-12-03
> Now the bad news. Even after I make the changes to the menu.lst file I still get Error 18. 

Well, I do see an error in your grub.lst, but Error 18 is: 

> 18 : Selected cylinder exceeds maximum supported by BIOS
    This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general). (From [http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors))

The error I see is in the kernel lines of your two boot menu options. You have:
```
kernel		/boot/vmlinuz-2.6.17-10-generic root UUID=53b01304-0084-4685-a06d-023732484307 ro single
```
You need:```

kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=53b01304-0084-4685-a06d-023732484307 ro single
```

The line should be root=UUID=HEXNUMBERHERE

---

### Post by mickbw on 2006-12-04
I made that change to the menu file and rebooted but it didn't make a difference.  

What is weird is that I had Edgy installed on this computer and it worked fine BUT I wanted to reinstall XP AND I wanted the Edgy install not to be dependent on the internal Hard Drive SO I made the fateful decision to try and reinstall Edgy two days ago.  

Does that seem like it may be more of a Grub error?  

Thanks for all the help,

Michael

---

### Post by stuporglue on 2006-12-04
> Does that seem like it may be more of a Grub error? 

Yeah, I'd have to guess it's a GRUB/BIOS error. Since GRUB is saying you're asking to boot from beyond what the BIOS can handle, I think you're in for some more work if you want it to all work out properly. 

This may be getting beyond this thread, but I think if you put /boot as a smaller partition at the start of your hard drive, it might work. 

BIOS would only have to work with the smaller /boot partition, and Linux would mount the other partition as root and maybe work fine. 

I've never had to do that, but I think that's how it was always done in the old timey Linux days. :-)

---

### Post by mickbw on 2006-12-04
I deleted the partitions, ran the install using a manual partition and it installed.  I am now at the point where I can start making the menu.lst changes.

Wish me luck.  Thanks for the help.

Michael

---

### Post by mickbw on 2006-12-04
Hi,

I am working from my own Ubuntu install rather than the live desktop.  

I did a very small partition (3 GB) for the / partition as you suggested and it worked.  

Do you think I can change the size or add another larger partition and make it the home directory now leaving root with the small partition?  

Thanks for all your help.  I felt like I was going to go insane.  

Michael

---

### Post by bodhi.zazen on 2006-12-06
Nice How-to

This thread has been added to the UDSF wiki.

[Edgy_USB_Install](http://doc.gwos.org/index.php/Edgy_USB_Install)

---

### Post by MistaED on 2006-12-11
Hey would it be at all possible to install/run ubuntu from a signle image on a USB drive? I have a 250gb USB drive which has 128mb for fat32 (contains various misc stuff and the ext2 fs driver for windows) and the rest of the drive is ext3 with a lot stored on it that I don't really want to backup and restore. 

I just wanted to put a /boot onto the ext3 partition, a 10gb image file formatted with ext3 or reiserfs and a 1 or 2 gb swap image. Do you think maybe root=UUID='hexnumber'/'rootimagefile' would work in grub? I'll have fstab set up to mount the huge ext3 partition, and then mount the root image off of that, and the MBR can contain grub no problems.

Cheers for the advice
-MistaED

---

### Post by stuporglue on 2006-12-12
> I just wanted to put a /boot onto the ext3 partition, a 10gb image file formatted with ext3 or reiserfs and a 1 or 2 gb swap image. Do you think maybe root=UUID='hexnumber'/'rootimagefile' would work in grub?

Maybe but that's so different from what's being done in this tutorial that you should probably start a new thread. Check out puppylinux though. They essentially do that on their USB bootable version. Depending on your skills you should be able to adapt their methods to Ubuntu

---

### Post by xtra2000 on 2006-12-20
ok. It works. Thanks stuporglue.

---

### Post by Biomorph on 2006-12-21
Hey just a basic question...how do you unplug the hard drive and still have linux to load from the live CD? I tried to disconnect my laptop hard drive... First it says hard disk read error and asks me to press F1 to move on...then It begins to boot from my cd rom and gets stuck without starting up ubuntu

---

### Post by stuporglue on 2006-12-23
> how do you unplug the hard drive and still have linux to load from the live CD? I tried to disconnect my laptop hard drive

It's worked just fine on the desktop computers I've tried this on. Booting from laptops has worked as well, once Ubuntu was on the external drives. 

Laptop hardware often behaves differently than desktop hardware. It may not be possible to install Ubuntu on an external drive with your laptop. Try: 1) Disabling the HD in the BIOS, but leaving it attached or 2) Changing the boot order to CDROM, USB, HD.

Hope that helps.

---

### Post by DigitalDingo on 2007-01-05
I just tried to install Edgy on my 250 GB usb hard drive so I can use that as a crash test dummy before touching the version on my laptop. 
Well, as install method I chose "Erase entire disk" and GRUB automatically chose hd0.
But during the installation (15% done saying: "Creating ext3 file system for / in partition #1 of SCSI1(0,0,0)(sda)") there is a failure: the progress bar jumps back to 5% and a dialog appears: "The ext3 file system creation in partition #1 of SCSI1(0,0,0)(sda) failed."

Any idea on how to fix this?

---

### Post by jacoby on 2007-01-06
I had the same problem as above.

I wiped my drive (had nothing anyways) and used GParted to make the partitions before starting install.  Then unmount them, start install, and choose to manually partition, leave em as is, and click next.  double check that they are unmounted, and choose mount points (root, swap, fat32 partition).  its all straight from there.

---

### Post by flamarro on 2007-01-11
> **DigitalDingo said:**
> I just tried to install Edgy on my 250 GB usb hard drive so I can use that as a crash test dummy before touching the version on my laptop. 
Well, as install method I chose "Erase entire disk" and GRUB automatically chose hd0.
But during the installation (15% done saying: "Creating ext3 file system for / in partition #1 of SCSI1(0,0,0)(sda)") there is a failure: the progress bar jumps back to 5% and a dialog appears: "The ext3 file system creation in partition #1 of SCSI1(0,0,0)(sda) failed."

Any idea on how to fix this?

i did have this exact problem. All you have to do is before you start installing, 
System > Preferences > Removable Drives and Media and deselect the following options
    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted
then when you are on the partitioning step of the installation unmount all disk and proceed...
i think this problem happens because after this step the live cd auto mount the usb disk again. When i did this that problem was solved.


Now me.... :-)
I  have an Acer computer, my moterboard dosent have a boot sequence like cdrom usbdisk and hdd, but has, when booting, doing F12, a boot option to select a hard drive to boot. ok, i complet my installation of ubuntu in my usb disk, and manage to see grub screen, so it can see my usb disk, but when i select the option to boot, gives me error 17, cant mount drive.
Why???? i have changed to hd0,0 hd1.0 but cant manage to mount the drive anyway. since i can see grub why cant it mount the drive......

PS: sorry for my english :-)

---

### Post by stuporglue on 2007-01-11
> **flamarro said:**
> 
manage to see grub screen, so it can see my usb disk, but when i select the option to boot, gives me error 17, cant mount drive.
Why???? i have changed to hd0,0 hd1.0 but cant manage to mount the drive anyway. since i can see grub why cant it mount the drive......


Flamarro, 

1) Are you absolutely *POSITIVE* that you didn't install GRUB to your main HD's MBR? When the USB disk isn't attached, and you boot normally, GRUB doesn't show up, right? 

(Just checking the simple mistakes first. :-) 

2) When you installed, did you disable or remove all internal hard drives? Your error is very similar (same?) to what I was getting when I'd do an install with an internal SATA drive. GRUB would get confused about how to install, and install to the correct place, but with the wrong parameters. Error 17 indicates this, as it means "This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB." So, I'm guessing it's looking at your other HD, possibly a windows partition and saying "this isn't linux". Faz sentido? :-) 


Thanks, 

Michael

---

### Post by Shin_Gouki2501 on 2007-01-11
Hello there , i just discoverd this tutorial!
I just tried to install Edgy on a USB Drive! I tried the "normal" install with Live CD but as depicted above the internal mbr always put an error. 

After That i looked up the forums and found this:
[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

But its far more difficult than ur tutorial!

Its a rather simple yet brilliant idea to remove the PCs internal HD ^^° ( why i didnt think of that :O )

since i am on a Notebook i cannot remove THAT easily my HD but i simply will turn it off in the BIOS :D

maybe this weekend i check out ur install method :)

Nice Work!!

wbr Shin Gouki

---

### Post by flamarro on 2007-01-11
> **stuporglue said:**
> Flamarro, 

1) Are you absolutely *POSITIVE* that you didn't install GRUB to your main HD's MBR? When the USB disk isn't attached, and you boot normally, GRUB doesn't show up, right? 

(Just checking the simple mistakes first. :-) 

2) When you installed, did you disable or remove all internal hard drives? Your error is very similar (same?) to what I was getting when I'd do an install with an internal SATA drive. GRUB would get confused about how to install, and install to the correct place, but with the wrong parameters. Error 17 indicates this, as it means "This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB." So, I'm guessing it's looking at your other HD, possibly a windows partition and saying "this isn't linux". Faz sentido? :-) 


Thanks, 

Michael

:D  Faz todo o sentido  :-D 
Yes, without usb disk attached i boot normally to windows. Yes, i have a Sata disk internally.
 I dont want to open my machine because i bought it a few months ago and i dont want to remove the acer's tape and lose my guarantie. I installed with grub option /dev/sdb and was a clean install.
Said that, i understand what you mean, so when on boot i select my usbdisk, grub is read, but selecting the option to boot it messes apart and cant be mount... Is there other option besides root  (hd0,0)? As i said i tryed (hd1,0) also but no sucess. I havent tryed yet to turn off my internally disk in Bios to see what happens.... will later...

thanks for your quick reply.... this indeed is a great forum...:-D

---

### Post by stuporglue on 2007-01-11
> **Shin_Gouki2501 said:**
> Hello there , i just discoverd this tutorial!
Its a rather simple yet brilliant idea to remove the PCs internal HD ^^° ( why i didnt think of that :O )

since i am on a Notebook i cannot remove THAT easily my HD but i simply will turn it off in the BIOS :D


Yes, disabling the HD in BIOS works as well. I discovered that a few days after making my orriginal post. Hope it works out for you.

To Flammaro: 

Yes, try disabling the drive from the BIOS. If you're not able to do that, you may have to use a different computer to get Ubuntu installed on the drive.

---

### Post by flamarro on 2007-01-11
Ok, didn't work.
I turned off my internal disk on Bios, and now, i dont even need to select presing F12, as i turn the pc the usb disk is detected, grub runs, but keep telling me the same, error 17 cant mount the desired disk.... changed (hd0,0) (hd1,0) (sd0, 0), this come up with error 23, but was a last resort chance :D 
Well, dont know what to do now....  ](*,) 
I think now i have ubuntu on a disk, ready to go, the only problem is mounting that disk with grub, isn't it???

---

### Post by garak on 2007-01-13
> **stuporglue said:**
> Create a large (at least 20 Gb) root partition

Is there any chance to get this howto working for much much less space?
I would like to use it for a 2gb usb pendrive.

---

### Post by stuporglue on 2007-01-13
> Is there any chance to get this howto working for much much less space?
I would like to use it for a 2gb usb pendrive.

I would consider 10 GB the minimal for a comfortable Linux install. I believe a fresh nothing-added Ubuntu install is about 2GB, not counting swap space, so I don't think there's a way using this method to fit it on a pen drive.

You may want to look at what Puppy Linux does with their USB booting. They use an file image or two and SYSLINUX to get it booting. You could probably use the Ubuntu live CD ISO, SYSLINUX, and a data file (to save you stuff in) to get it working on your drive. That's a whole different approach then what's happening here though. :-) 

Good luck

---

### Post by stuporglue on 2007-01-13
> **flamarro said:**
> Ok, didn't work.
I turned off my internal disk on Bios, and now, i dont even need to select presing F12, as i turn the pc the usb disk is detected, grub runs, but keep telling me the same, error 17 cant mount the desired disk.... changed (hd0,0) (hd1,0) (sd0, 0), this come up with error 23, but was a last resort chance :D 
Well, dont know what to do now....  ](*,) 
I think now i have ubuntu on a disk, ready to go, the only problem is mounting that disk with grub, isn't it???

Did you do a full install again with the disk disabled? That was the key to success here. Disable/remove disks from the computer during the install, then afterwards it didn't matter if they were in/on or not. 

With the disk disabled, you may be able to use the live CD, chroot into your current install and re-install grub. Since the internal HD is disabled, hopefully you can use the default install options.

---

### Post by soldonz on 2007-01-13
I have worked on this for sometime now and here are some notes worth sharing. So if you have problem, please check these. 

1. During the installation of Edgy, you will be asked where to install grub. PLEASE open the /boot/grub/device.map, and check if hd0 or hd1 or hd2 is your usb device. (e.g. for pc with one internal HDD, hd0 may point to /dev/hda and hd1 may point to /dev/sda, which is your usb hdd)

To avoid confusion, I strongly recommend that you disable all internal HDD from bios or disconnect them manually so you won't install grub on the wrong place.

2. make sure that you know which partition did you install ubuntu to and make sure you know there device name. e.g. /dev/sda1. You should know this if you edit partition manually during installation. 

3. Note this very important thing. For a portable ubuntu on HDD. "**DO NOT USE UUID**"  "by-id" is better.
I choosed the default EXT3 as my primary partition for ubuntu and later found out that UUID is not a fixed value. It somehow changes when you plug it onto another PC. it happened to me. took me a while to find this out. so.. no uuid.

Another reason to your by-id link is that your device.map file needs to be able to specify where hd0 points to and .. I could only find the uuid for all my parttions, but none for the device itself. only by-id link is available to point to the device itself. This pretty much forced us to useby-id link as a mean to have a fixed device/partition referral on any pc. 

for example: this is what use in my device.map for my transcent StoreJet USB HDD
(hd0) /dev/disk/by-id/usb-StoreJet_StoreJet

use the command
ls /dev/disk/by-id -lh 
to display the by-id link and their real device point. e.g. /dev/disk/by-id/usb-StoreJet_StoreJet ..-> /dev/sda

4. now, modify /boot/grub/menu.lst and make the following changes assuming that your device is /dev/sda and your simple id as shown in /dev/disk/by-id is usb-StoreJet_StoreJet

Here is an example

before:

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=**[COLOR="Red"]/dev/sda1[/COLOR]** ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

after

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=**[COLOR="Red"]/dev/disk/by-id/usb-StoreJet_StoreJet-part1[/COLOR]** ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

Also in /etc/fstab

before

[COLOR="Red"]**/dev/sda1**[/COLOR]      /               ext3    defaults,errors=remount-ro 0       1

after

[COLOR="Red"]**/dev/disk/by-id/usb-StoreJet_StoreJet-part1**[/COLOR]       /               ext3    defaults,errors=remount-ro 0       1

note that the "-part1" refers to partition number. e.g. sda4 = "usb-StoreJet_StoreJet-part4"

If you are unable to boot after kernal update, edit the commands in grub and do the above changes on menu.

Anyway. the key here is to refer to your partition using the by-id link instead of the actual device link. 

My usbhdd now boots on all the PCs that I have tested so far. from work and at home. with different setups. (internal IDE HDD or internal SATA HDD and with and without other USB/fireware HDDs).

The next problem is to do with the hardware detection, video card detection to be exact, I still haven't figure out how to make ubuntu re-probe the video hardware at each boot, like the way it does on live CD. If you know, could you please share the know how? (dpkg-reconfigure does not detect changes in video card PCI bus correctly. e.g. on-board intel video, APG video and PCI-Express video cards.)

---

### Post by stuporglue on 2007-01-13
Hi soldonz, glad to hear more people are doing this too. :-) I have a couple of comments on your notes, based on the experience I've been having. I've been working as a teacher's assistant in a class where each student was required to do this, so I have experience with probably 8 different USB drive models and maybe 15 different computer and laptop models. 

> **soldonz said:**
> 3. Note this very important thing. For a portable ubuntu on HDD. "**DO NOT USE UUID**"  "by-id" is better.
I choosed the default EXT3 as my primary partition for ubuntu and later found out that UUID is not a fixed value. It somehow changes when you plug it onto another PC. it happened to me. took me a while to find this out. so.. no uuid.

I'll have to partially disagree with you. by-id my also work, but UUID has been working wonderfully for myself and many others. The UUID doesn't change from machine to machine. It is assigned to a partition at formatting time (ie. by mkfs.ext3), and can be assigned to an ext3 drive by using tune2fs. It *will* change each time you format your partition however. 

> **soldonz said:**
> Another reason to your by-id link is that your device.map file needs to be able to specify where hd0 points to...
If you remove all hard drives, then there will only be the USB drive. That drive will be /dev/sda, and hd0 will point to it. There is no need to mess with the map file, unless you're trying to put Windows and Linux on the same USB drive. On all computers tested here, when you choose to boot from USB, the BIOS assigns the USB drive to hd0, so no problems. I suppose it's possible that not all BIOSes do that though, so you may be right. 

> **soldonz said:**
> The next problem is to do with the hardware detection, video card detection to be exact, I still haven't figure out how to make ubuntu re-probe the video hardware at each boot, like the way it does on live CD.

This was our biggest issue too. I eventually just decompressed the initrd from the live CD. We're putting the command
```
dpkg-reconfigure -fnoninteractive --no-reload -phigh xserver-xorg
```into the /etc/init.d/gdm startup script on it's own line, right after the line that says "start)". This means it's getting reconfigured each time GDM gets restarted. It works fine on everything we've tested it on. I'm excited for Fiesty Fawn's "Bullet Proof X" though. :-)

---

### Post by soldonz on 2007-01-14
Hi stuporglue, 

Many thanks for the comment and solution to the video card detection.

I don't know what has happened back there.. I had it all configured using UUID.. and even booted at home once, but it crashed at video detection.. then I had to reset the computer. after that, it wouldn't boot anymore.. and I found out that the UUID was changed. (I ran the recovery mode couple times I think).

Do you think it could be the hard reset or data corruption that affect the uuid? or maybe fsck? 

many thanks,

Peter

---

### Post by Shin_Gouki2501 on 2007-01-14
Hello stuporglue!
I just did like u wrote on page 1, i replaced thre entry in the menu.lst. everything worked well until the reboot...
now it simply displays on boot up:
GRUB_
with blinking _
but nothing else.... any ideas?

wbr Shin Gouki

---

### Post by stuporglue on 2007-01-15
> **soldonz said:**
> I don't know what has happened back there.. I had it all configured using UUID.. and even booted at home once, but it crashed at video detection.. then I had to reset the computer. after that, it wouldn't boot anymore.. and I found out that the UUID was changed. (I ran the recovery mode couple times I think).

Do you think it could be the hard reset or data corruption that affect the uuid? or maybe fsck? 

Interesting. The hard reset is probably the most likely candidate, of those you listed. A hard reset can mess up other features of ext3, I suppose it could mess up the UUID.

I might take a closer look at by-id.  It seems that the id of a disk doesn't ever change? This would make disk imaging harder (since the install is tied to a specific disk), but might make a normal install more robust.

---

### Post by stuporglue on 2007-01-15
> **Shin_Gouki2501 said:**
> Hello stuporglue!
I just did like u wrote on page 1, i replaced thre entry in the menu.lst. everything worked well until the reboot...
now it simply displays on boot up:
GRUB_
with blinking _
but nothing else.... any ideas?


I don't know for sure, but here are some things I would try: 

1) Change the boot order in the BIOS so that USB is before the internal HD

2) I might let the disk spin up before selecting to boot from USB

3) Double check the grub.lst file, and make sure you didn't break it. :-) A friend forgot to leave a space between the UUID number and the "ro" flag, and had a similar issue.

---

### Post by flamarro on 2007-01-16
Hi guys,
just to say that i finnaly did it yeeeeee:-D 
In my usb disk i have a logical partition with ntfs (windows) and when partitioning i have sdb2 where i put / sdb3 sdb4 sdb5 and sdb6, didnt have sdb1, dont now why. when installing i put grub in /dev/sdb, went good. The change i had to do was root  (hd0,1), i suppose sdb1 was (hd0,1) wasnt it?
Pretty good. Now i am following that changes that you refer, so that i can go to any computer  and have my own system..... i tryed at work but the bloddy machine cant boot by usb devices..... :(

---

### Post by random guy on 2007-01-21
hey i just got a drive yesterday, here is a question though:

in the description for the alternative install cd it says that you can use it to install grub onto a different partition that the main one.

quote + link

> installing GRUB to a location other than the Master Boot Record;

[http://ftp-mirror.internap.com/pub/ubuntu-releases/kubuntu/6.10/](http://ftp-mirror.internap.com/pub/ubuntu-releases/kubuntu/6.10/)

will that work instead? i mean could you just go through the regular isntaller there and select that you want to install onto the external hd drive?

EDIT: can you jsut umount /dev/hda instead of unpluging the hard drive?

---

### Post by stuporglue on 2007-01-21
> **random guy said:**
> here is a question though:

in the description for the alternative install cd it says that you can use it to install grub onto a different partition that the main one.

We tested that, and found that it _does_ install to a different partition, but with the wrong parameters. Someone smarter than I may be able to make it work though, or may have success with their particular machine. If there's a way to make it work w/out disabling/removing the drives, I'd love to know! :-)

> **random guy said:**
> EDIT: can you jsut umount /dev/hda instead of unpluging the hard drive?

Mounting/Mounting doesn't make a difference for grub. It typically installs to the MBR of a drive which isn't mounted anyways. It *may* be possible to remove the references to the disk in /dev entirely, but disabling/removing is a sure thing. 

Note: You can disable the drive in the BIOS instead of physically removing it from the computer.

---

### Post by random guy on 2007-01-21
> Note: You can disable the drive in the BIOS instead of physically removing it from the computer.

well i dont know how to do this, can you give me a general crash course in it, if it is a little different for my bios than yours i will still be able to figure it out so long as i know generally what i am looking for.

thanks.

---

### Post by stuporglue on 2007-01-21
> 
```
You can disable the drive in the BIOS instead of physically removing it from the computer.
```
well i dont know how to do this, can you give me a general crash course in it, if it is a little different for my bios than yours i will still be able to figure it out so long as i know generally what i am looking for.
thanks.

It really depends on the BIOS. Some BIOSes may not even have it as an option. On the BIOS  on the machines at school, there is an option for the SATA controllers that says "ENABLED", then I toggle it, and it says "DISABLED". :-) 

You can probably find a PDF of your BIOS manual online, usually on the manufacturer's site (of the BIOS, not the computer itself).

hope that helps

---

### Post by random guy on 2007-01-24
ok thanks so far.  i have had some success and some failure.  

i disabled internal hd, i booted and isntalled ubuntu and edited the files as you posted but when i boot from the external hd i can see the ubuntu loading screen but after that the screen is blank.  i hear the login drums and such but no visual.  

i can switch to another runlevel and there i can see the terminal.

any idea why this is?

dell 4600
p4 2.4
256 ram
nvidia x5200
160gb maxor usb hd

---

### Post by stuporglue on 2007-01-24
> **random guy said:**
> when i boot from the external hd i can see the ubuntu loading screen but after that the screen is blank.  i hear the login drums and such but no visual.  


I'm afraid I don't know. The link "dpkg-reconfigure -fnoninteractive --no-reload -phigh xserver-xorg" is the best I've been able to figure out for auto-detecting the video setup, and it works on most computers. 

Unfortunately, yours is the second case I know of where there are no graphics. In another case there is a little bit of garbage at the edges of the screen, but it's otherwise fine. 

I've been trying to understand everything that happens on the Live CD so I can use exactly what it uses, but I've been unsuccessful in figuring it out. :-( 

You could of course remove the dpkg-reconfigure line from the /etc/init.d/gdm script, then run "sudo dpkg-reconfigure xserver-xorg" and semi-manually configure your video card, but then it wouldn't attempt to auto-redetect the video on each boot. Each time you changed computers you'd have to reconfigure X. 

Sorry it's not working correctly.

---

### Post by random guy on 2007-01-25
thanks for the help, i will play around with it some over the weekend, maybe clear it and try again and see if it was a problem with that one time.  i will also try booting it from another computer and seeing if after i install nvidia drivers it will boot correctly on that first system.  

thanks for the help, will let you know if i figure out something.

---

### Post by sv3t on 2007-02-02
I have a laptop under a warranty, so I couldn't remove the hdd. However, I installed the vmware server, and created a system without a hdd (actually you cannot do that directly - you first create it with a virtual hdd, and then delete the hdd). Then I followed your instructions and it worked. Note: the vmware bios couldn't boot from the usb drive, so once you install ubuntu on the usb drive, do not forget to follow steps **3.1** through 6. After that, stop the virtual machine and restart the host. Then boot your laptop from the usb drive. It worked for me.

---

### Post by mooter on 2007-02-03
Awesome.  I got it working!  After many attempts of the install stopping at 15% and giving me a partition error (which I think I gave up on when I first tried to install Ubuntu so ended up putting it on internal hd) I did something right with gpart and it installed.

One thing worth mentioning though,  since there wasn't any mention of marking the sda root as a boot part the bios won't load it.  So I marked it and is fine.

Big problem though.  Now that I plugged in my internal hd Ubuntu won't recognise it!  It's still listed in the bios, so I would figure it would still show up.
I have 4 different partition of useful stuff on there that I would frequently reference to, usually media files.  My other USB drive is recognised but that doesn't surprise me. 

Is this the catch?

Anyway thanks Stupor:)

---

### Post by stuporglue on 2007-02-03
> Big problem though. Now that I plugged in my internal hd Ubuntu won't recognise it! It's still listed in the bios, so I would figure it would still show up.
I have 4 different partition of useful stuff on there that I would frequently reference to, usually media files. My other USB drive is recognised but that doesn't surprise me.


Mooter, 

I bet it's seeing it, it's just not auto-mounting it (slight, but important, difference).  Run "sudo fdisk -l /dev/hda" if the drive is an IDE drive, or "sudo fdisk -l /dev/sda" or possibly "sudo fdisk -l /dev/sdb" if the disk is a SATA or SCSI drive. If it prints out your intermal drive's partition table, it's seeing it. 

If it's seeing it, search the forums for a tutorial on how to mount partitions. It's not too hard, but probably a bit off topic for this thread.  

HTH

---

### Post by mooter on 2007-02-04
Cool.  It's seeing them.  Thanks again!

---

### Post by Xx_qwerty_xX on 2007-02-16
I just followed your steps and it all ended in an error 18 on booting the USB HDD..

Whats an error 18?

---

### Post by jagrav on 2007-02-21
Hi stuporglue,
     Followed your instructions. It works most of the time. Once in a while I get the boot does not complete and i get this message:
"/bin/sh: can't access tty; job control turned off "

If I then give 'poweroff' and restart the computer it sometimes works. Is this a hardware problem  
 or does it have anything to do with the fact that my internal drives are plugged back in?

---

### Post by stuporglue on 2007-02-21
> **jagrav said:**
> Hi stuporglue,
     Followed your instructions. It works most of the time. Once in a while I get the boot does not complete and i get this message:
"/bin/sh: can't access tty; job control turned off "

If I then give 'poweroff' and restart the computer it sometimes works. Is this a hardware problem  
 or does it have anything to do with the fact that my internal drives are plugged back in?

Once the install is done, it doesn't matter if the internal HDs are present or not. I have seen that error mesgae before, but not in context of USB drives, so I would guess it's hardware. Are you able to pinpoint it to any certain occasions (fresh boot vs. reboot, choose boot immediately or after some time (time for drive to spin down or not) )? 

I haven't personally had that problem on the computers or USB drives I've worked with, so I haven't had to solve it before. Sorry!

---

### Post by stuporglue on 2007-02-21
> **Xx_qwerty_xX said:**
> I just followed your steps and it all ended in an error 18 on booting the USB HDD..

Whats an error 18?

Here's the list of GNU Grub error codes. 
[http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html)

Looks like error 18 means your root partition is too big for your BIOS. You can solve this when you re-install by creating a small (40Mb?) boot partition. It should be formatted ext2 and mounted on /boot. 

hth, 

Stuporglue

---

### Post by scott_b on 2007-03-10
Thanks for the how-to. 

Everything worked fine, but it hangs on boot.  It says "Device not accepting address 5, error -71". It goes on to test a whole bunch of other addresses, but no luck.  I saw something about irqpoll on another thread, but I don't know what it is, nor do I know how to add it as a boot option.

Any help is greatly appreciated.

---

### Post by scott_b on 2007-03-14
Ok, I figured out my last problem. I just have to unplug the thing when it freezes, then plug it back in. strange.  apparently, its a kernel issue.  over my head.

new problem - 

I can't get xorg to work on any machine but my laptop.  It'll but on others, but gdm wont come up.  I have the dpkg-reconfigure line in my /etc/init.d/gdm file.  I also installed every xserver-xorg-video thing I could find.  What is the problem?

---

### Post by stuporglue on 2007-03-14
```
I can't get xorg to work on any machine but my laptop. It'll but on others, but gdm wont come up. I have the dpkg-reconfigure line in my /etc/init.d/gdm file. I also installed every xserver-xorg-video thing I could find. What is the problem?
```

Hard to say without more information. If I were you, I'd stop gdm, and run startx manually (on a machine it doesn't work on). Then I'd take the errors it spits out, and ask in a new thread. 

I've found machines that have distorted graphics with the instructions I posted, but all of them have had something appear.

---

### Post by random guy on 2007-03-14
you know reading this guide it sounds like it would work in any recent ubuntu release, aka maybe it will work better for me with feisty.

i am using fesity herd 5 right now and it is working fine.  i have even installed a few edgy debs and such despite a possible risk in doing so without any real side effects.

feisty just seems like an upgraded edgy, usful thing in this case is bulletproofx which is a great idea...

---

### Post by victorbrca on 2007-05-15
I just installed this using Feisty Fawn 7.04 and a WD Passport with 120G.

I set it like this:

Primary -   2g  - /
Primary -   1g  - swap
Logical - 117g  - /media/fat32


  **Tested on 2 PCs and it worked.** Could not configure wireless (did not have a chance to try too much).

  I also did not have to edit grub, it apparently did automatic.



Vic.

---

### Post by victorbrca on 2007-05-16
Hi all,


  I have a question in regards to this setup. How well does this work when you are booting from different machines with different hardware, different processor (even different architecture)?

  I'm a new Ubuntu user, and a long Windows user. In Windows we'd avoid using same image on different hardware as it does not adapt so well. I'm not sure how Linux/Ubuntu would adapt to it...

  I know we are running the script to reconfigure X at boot, but how about the reaming hardware.


Thanks!!


Vic.

---

### Post by neelesh_jn on 2009-03-06
hi,,i tried with 'unetbootin' to install live ubuntu on my pendrive,
but since it is a live environment so whatever i install in it in a session remains for the session only...
isn't there a method such that i install a permanent version on my usb-drive so that i can install stuff too...
i also tried the version from 'pendrivelinux.com' but my ubuntu was not able to boot that time..
so i thought to ask u before trying yours..
thankyou

---

### Post by Ken_C on 2009-03-12
Will this tutorial work with ubuntu 8.10? I have it installed and booting a usb HD. I run it on a IBM thinkpad R-51. if you have one of these you know the internal HD comes out quite easily. so I removed mine and installed. works fine. just wondering if the rest of the config to make it re-detect video hardware is the same. also should I boot the cd to do it?

---

