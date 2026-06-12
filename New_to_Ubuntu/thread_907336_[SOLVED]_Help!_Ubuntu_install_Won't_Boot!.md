---
title: "[SOLVED] Help! Ubuntu install Won't Boot!"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-09-01
I've been using this installation of ubuntu since christmas and it's been fine but maybe 15 min ago I downloaded a video to the desktop and then double clicked it to play and the desktop froze (although the cursor still moved...) so I pressed ctrl + alt + backspace and i got alot of errors saying that "soft system reboot failed" or something to that effect and then nothing so i pressed the reboot button on my pc and now I cant boot ubuntu! i dont even get to grub:( im currently using the live cd but it hasnt mounted my ubuntu partition!

Thanks in advance!

---

### Post by xeth_delta on 2008-09-01
> **kamitsukai said:**
> I've been using this installation of ubuntu since christmas and it's been fine but maybe 15 min ago I downloaded a video to the desktop and then double clicked it to play and the desktop froze (although the cursor still moved...) so I pressed ctrl + alt + backspace and i got alot of errors saying that "soft system reboot failed" or something to that effect and then nothing so i pressed the reboot button on my pc and now I cant boot ubuntu! i dont even get to grub:( im currently using the live cd but it hasnt mounted my ubuntu partition!

Thanks in advance!

Ok, let's verify the partition table and mount points. Assuming your HDD is on sda, type:
```
sudo mount
```
```
sudo parted /dev/sda print
```
```
sudo fdisk -l
```

---

### Post by cwsnyder on 2008-09-01
Can you get into Grub by pressing the Escape key after the system goes from your manufacturer's logo screen and tries to boot?  If you can, enter **grub** and press the Enter key.

This should take you to the Grub prompt.  Type **find /boot/grub/stage1** and press the Enter key.  This should return something like **(hd0,0)**.  This response is Grub's syntax for the location of your hard drive which contains the bootable portion of Grub.

Now type **root (hd0,0)**, or whatever the previous response was, followed by the Enter key.  Type **setup (hd0)**, again should match the previous, followed by the Enter key.  This should re-install the boot loader in the MBR (Master Boot Record), and you can reboot, coming back up into Grub normally, at least according to Linux Format Magazine September 2008, page 47.

---

### Post by kamitsukai on 2008-09-01
This is what i get from the commands...
```

ubuntu@ubuntu:~$ sudo mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
```

```

ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Could not stat device /dev/sda - No such file or directory.        
Retry/Cancel?
```

Tried again but get the same result as above...and the last command as far as i can tell didnt do anything...

---

### Post by kamitsukai on 2008-09-01
> **cwsnyder said:**
> Can you get into Grub by pressing the Escape key after the system goes from your manufacturer's logo screen and tries to boot?  If you can, enter **grub** and press the Enter key.

This should take you to the Grub prompt.  Type **find /boot/grub/stage1** and press the Enter key.  This should return something like **(hd0,0)**.  This response is Grub's syntax for the location of your hard drive which contains the bootable portion of Grub.

Now type **root (hd0,0)**, or whatever the previous response was, followed by the Enter key.  Type **setup (hd0)**, again should match the previous, followed by the Enter key.  This should re-install the boot loader in the MBR (Master Boot Record), and you can reboot, coming back up into Grub normally, at least according to Linux Format Magazine September 2008, page 47.

Nope i dont even get to grub i get as far as my systems bios when it tells me that it failed to boot and asks me to boot from cd...

---

### Post by philinux on 2008-09-01
Very Odd.

Sounds like the mbr vanished. Could be a sign of a failing hard drive.

I'd try re-installing grub from the live cd.

[How to install Grub from a live Ubuntu cd. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by kamitsukai on 2008-09-01
> **philinux said:**
> Very Odd.

Sounds like the mbr vanished. Could be a sign of a failing hard drive.

I'd try re-installing grub from the live cd.

[How to install Grub from a live Ubuntu cd. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=224351")

just tried the command:

```

find /boot/grub/stage1
```

```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> 


```

...thats bad isn't it?

---

### Post by xeth_delta on 2008-09-01
> **kamitsukai said:**
> just tried the command:

```

find /boot/grub/stage1
```

```

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1

Error 15: File not found

grub> 


```

...thats bad isn't it?

I don't think you tried
```
sudo fdisk -l
```
Try it, it should list any HDD.

---

### Post by kamitsukai on 2008-09-01
That command doesent do anything :( does this mean my hardrive's broken?

---

### Post by django0909 on 2008-09-01
Does 'sudo fdisk -l' not even give an error message? And am I correct in assuming you're running it from terminal in the live CD?

---

### Post by xeth_delta on 2008-09-01
> **kamitsukai said:**
> That command doesent do anything :( does this mean my hardrive's broken?

Not even an error message? That's odd. Several things to check.

Is the HDD visible under the BIOS? Check the cable between the drive and the mainboard (if it is not a laptop). Make sure the drive is actually running.

Also run
```
dmesg | grep -i ata
```
or
```
dmesg | grep -i sd
```
or
```
dmesg | grep -i scsi
```

There is a possibility, that the drive is not running due to some reason, in the worst case, it is a hardware problem. But, please don't be alarmes, we can still try to decipher what's wrong.

---

### Post by kamitsukai on 2008-09-01
```
sudo fdisk -l
```

yep running from live cd and i dont get any error messages...

Ive included what i get from the command "dmesg | grep -i ata"
in two atachments as there was so much... also id prefer to try and find out whats wrong without opening up my case (as it will more than likley void my warranty...:()

---

### Post by kansasnoob on 2008-09-01
You're not confusing the lower case L for a one at the end of sudo fdisk -l are you?

---

### Post by kamitsukai on 2008-09-01
> **kansasnoob said:**
> You're not confusing the lower case L for a one at the end of sudo fdisk -l are you?

Im copy and pasting the commands :P

---

### Post by kansasnoob on 2008-09-01
And you're running the live CD right now? If so go to System > Administration > Partition Editor (that's gparted) which will open up a gui and see if you can post a screenshot.

---

### Post by kamitsukai on 2008-09-01
**OK I'm really confused now:confused:**

I just shutdown my PC to open up the case and see if any of the cables had fallen out but on the off chance I switched it back on and it booted up straightaway into grub and ubuntu:KS but why did I have this problem??? I'm a bit frightened to turn my PC off again now, just in case it wont boot again:mad:

---

### Post by kansasnoob on 2008-09-01
I'm glad you got it back. What I was suspicious of was if you might be getting pinched for free space on your boot partition.

I had a similar problem when editing some home movies because I simply was trying to use space that wasn't there.

Edit: Another possibility is that something, like the cpu, was overheated. I have computertemp installed in system panel to monitor the cputemp.

---

### Post by xeth_delta on 2008-09-01
> **kamitsukai said:**
> **OK I'm really confused now:confused:**

I just shutdown my PC to open up the case and see if any of the cables had fallen out but on the off chance I switched it back on and it booted up straightaway into grub and ubuntu:KS but why did I have this problem??? I'm a bit frightened to turn my PC off again now, just in case it wont boot again:mad:

That is a bit strange, I am not sure what to tell you. I wonder if it's a bug in the BIOS. Could it be that last time you booted it did not recognize the drive, perhaps after an unclean shut-down? I believe I've seen something like this before, but was a rare event, and I believe independent of the OS.

In any case, glad it's working. You maybe can go to the BIOS setup and fix the HDD config to the current.

Let us know if it happens again.

---

### Post by kansasnoob on 2008-09-01
Computertemp:

[ATTACH]83664[/ATTACH]

See it installed to the left of the right grouping of applets in my panel? I use Fahrenheit because my brain's lazy:)

---

### Post by kamitsukai on 2008-09-01
> **xeth_delta said:**
> That is a bit strange, I am not sure what to tell you. I wonder if it's a bug in the BIOS. Could it be that last time you booted it did not recognize the drive, perhaps after an unclean shut-down? I believe I've seen something like this before, but was a rare event, and I believe independent of the OS.

In any case, glad it's working. You maybe can go to the BIOS setup and fix the HDD config to the current.

Let us know if it happens again.

This is probably more likely as I mentioned in my first post the computer froze and refused to shutdown properly at which point I hit the reset button:)

Thanks for everybody's help

---

### Post by xeth_delta on 2008-09-01
> **kamitsukai said:**
> This is probably more likely as I mentioned in my fist post the computer froze and refused to shutdown properly at which point I hit the reset button:)

Thanks for everybody's help

You're welcome! Do not hesitate to ask if you need any further help.

---

