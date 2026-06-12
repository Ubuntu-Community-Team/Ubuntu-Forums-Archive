---
title: "[SOLVED] One usb memory is working, another isn't"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-20
I have two usb memory sticks/devices.

One is 256 meg. It is working. Files can be moved from the hard drive to the memory stick and vice versa.

The other is 1 gig. It shows up as:

mark@Lexington-19:~$ lsusb
Bus 004 Device 003: ID 3538:0054 Power Quotient International Co., Ltd 

but files cannot be read from nor files moved/copied to it.

From a LiveCD session, I have used GParted to partition and format the stick, time and time again.

This HH is less than 3 days old. All packages are up to date. No modifications to system files have been made. The device is listed in /media as a folder named: usb.

Please see attached screenshots.

---

### Post by django0909 on 2008-05-20
Have you tried transferring files as root?

---

### Post by Mark_in_Hollywood on 2008-05-20
I don't know how to do that as root. I'm mostly a gui user.

If you give me the terminal command structure, for example:

sudo -

cp /home/filename 

to where the usb drive is, I can try it, but I don't know whether to try to write the file into:

/dev
/media
/mnt

or all of the above.

---

### Post by Mark_in_Hollywood on 2008-05-20
I forgot this earlier

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         122      979933+  83  Linux

---

### Post by rbc on 2008-05-20
It should be
 cp */filedirectory/nameoffile* /media/disk
 
Try it as non-sudo first. If that doesn't work
sudo cp */filedirectory/nameoffile* /media/disk

---

### Post by Mark_in_Hollywood on 2008-05-20
I'm a trifle baffled. Using sudo the files copied, but don't show in the Gnome file manager browse folder or open features.

mark@Lexington-19:/media/usb$ cd /home/mark/Desktop
mark@Lexington-19:~/Desktop$ cp /home/mark/Desktop/usbmounting /media/usb
cp: cannot create regular file `/media/usb/usbmounting': Permission denied
mark@Lexington-19:~/Desktop$ sudo cp /home/mark/Desktop/usbmounting /media/usb
mark@Lexington-19:~/Desktop$ cd /media/usb
mark@Lexington-19:/media/usb$ ls
cervantes  usbmounting
mark@Lexington-19:/media/usb$

also:

May 20 10:05:17 Lexington-19 kernel: [ 9676.926324] usb 4-7: new high speed USB device using ehci_hcd and address 7
May 20 10:05:17 Lexington-19 kernel: [ 9677.060739] usb 4-7: configuration #1 chosen from 1 choice
May 20 10:05:17 Lexington-19 kernel: [ 9677.073785] scsi7 : SCSI emulation for USB Mass Storage devices
May 20 10:05:22 Lexington-19 kernel: [ 9682.062259] scsi 7:0:0:0: Direct-Access     Generic  USB Flash Disk   0.00 PQ: 0 ANSI: 2
May 20 10:05:22 Lexington-19 kernel: [ 9682.063994] sd 7:0:0:0: [sdb] 1974271 512-byte hardware sectors (1011 MB)
May 20 10:05:22 Lexington-19 kernel: [ 9682.065124] sd 7:0:0:0: [sdb] Write Protect is off
May 20 10:05:22 Lexington-19 kernel: [ 9682.068714] sd 7:0:0:0: [sdb] 1974271 512-byte hardware sectors (1011 MB)
May 20 10:05:22 Lexington-19 kernel: [ 9682.069589] sd 7:0:0:0: [sdb] Write Protect is off
May 20 10:05:22 Lexington-19 kernel: [ 9682.069608]  sdb: sdb1
May 20 10:05:22 Lexington-19 kernel: [ 9682.180925] sd 7:0:0:0: [sdb] Attached SCSI removable disk
May 20 10:05:22 Lexington-19 kernel: [ 9682.180989] sd 7:0:0:0: Attached scsi generic sg3 type 0

---

### Post by rbc on 2008-05-20
In terminal, type this please and post back: mount

According to your third screenshot, the flash drive is being mounted at /media/disk, not media/usb. is that not true?

---

### Post by Mark_in_Hollywood on 2008-05-20
Output of mount:

mark@Lexington-19:/home$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
/dev/sdc1 on /media/UDISK 28X type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
**/dev/sdb1 on /media/disk type ext2 (rw,nosuid,nodev,uhelper=hal)**

The screenshot shows as:

mount point: /media/disk

more than that I can't answer.

---

### Post by rbc on 2008-05-20
Good. So type this:
cp /home/mark/Desktop/usbmounting /media/disk

Then use terminal, or nautilus to navigate to /media/disk and see if the file transferred

---

### Post by bumanie on 2008-05-20
I don't know much about this, but I suspect the problem may be related to the 'nodev' entry. At least in fstab 'nodev' means something like - 'not to interpret the device'. I am no expert on this though, but it does seem that your usb stick is not being interpreted correctly. Sorry I don't know how to fix it other than your third screenshot does have a permissions button where you may be able to change something. You may have to wait for more expert advice.

---

### Post by Mark_in_Hollywood on 2008-05-20
> **rbc said:**
> Good. So type this:
cp /home/mark/Desktop/usbmounting /media/disk

Then use terminal, or nautilus to navigate to /media/disk and see if the file transferred

mark@Lexington-19:/home$ cp /home/mark/Desktop/usbmounting /media/disk
cp: cannot create regular file `/media/disk/usbmounting': Permission denied
mark@Lexington-19:/home$ sudo cp /home/mark/Desktop/usbmounting /media/disk
[sudo] password for mark: 
mark@Lexington-19:/home$ 

see screenshot, Nautilus now shows the file in the device.

---

### Post by Mark_in_Hollywood on 2008-05-20
From:


Reload this Page How To Fix Mounting USB Flash Drive Problem in KDE 3.5 (from: Dec. 2005)

[http://ubuntuforums.org/showthread.php?p=616396#post616396](http://ubuntuforums.org/showthread.php?p=616396#post616396)

I see these lines below added into /etc/fstab. Will this solve this without affecting other usb jumpdrives? Is what is below currently good?

sysfs /sys sysfs defaults 0 0
usbfs /proc/bus/usb usbfs defaults 0 0
none /dev/shm tmpfs defaults 0 0
none /dev/pts devpts defaults 0 0

---

### Post by bumanie on 2008-05-20
You could try that. No guarantee that it will work. But if it doesn't you should be able to remove the entries you add. I have not heard of usb devices/lines to get usb to boot being added to fstab unless they have been hard drives with grub installed. Really can't answer what it may or may not do.

---

### Post by Mark_in_Hollywood on 2008-05-20
I rebooted using GParted LiveCD to delete any data or corruption on the jumprdrive.

I told GParted to delete the entirety of the drive and re-partitioned using Primary and ext2.

On reboot, the same problem, on the Properties page the device says: ext3, but on the media properties page it says: ext2. And still no permissions.

I tried:

mark@Lexington-19:~$ sudo chmod -R 755 /media/USB/
[sudo] password for mark: 
chmod: cannot access `/media/USB/': No such file or directory

that's not it. Should it have been chown?

Is there a formatting command for this device like the old dos disksettes?

format a:/sys? or some such in Linux?

---

### Post by Mark_in_Hollywood on 2008-05-20
mark@Lexington-19:~$ ls -lh /media/
total 36K

drwx------ 4 mark root  16K 1969-12-31 16:00 UDISK 28X

**drwxr-xr-x 2 mark root 4.0K 2008-05-20 10:44 usb**

How do I change this line drwxr-xr-x to drwx?

---

### Post by Mark_in_Hollywood on 2008-05-20
So, I've made it worse?

mark@Lexington-19:~$ ls -lh /media/
total 36K

drwx------ 4 mark root  16K 1969-12-31 16:00 UDISK 28X

How can the line below be changed to look like the line above?

**drwxrwxr-x 2 mark mark 4.0K 2008-05-20 17:16 usb**

---

### Post by Mark_in_Hollywood on 2008-05-27
!!EUREKA!!

I have found a use for Microsoft operating systems.

I took my "defunct" usb memory stick/jumpdrive to a friend's house. Upon plugging the device into a usb port, Windows XP found the device, reported it as unformatted and asked me if I wanted to format it.

I said "YES".

Upon finishing the formatting, the device is now read/write.

Thanks to everyone who responded to this post.

---

### Post by wootah on 2008-05-27
USB Sticks should generally be formatted only as FAT32/FAT16. I think that is why you couldn't read off of it.

---

