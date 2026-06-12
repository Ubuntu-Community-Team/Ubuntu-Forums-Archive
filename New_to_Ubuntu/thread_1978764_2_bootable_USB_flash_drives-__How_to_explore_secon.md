---
title: "2 bootable USB flash drives-  How to explore second?"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-05-12
I have a 16 GB 11.10 that I am typing on and it is running great.

My second USB is an 8 GB that is almost bootable.

It will boot to Terminal.

I was hoping that instead of trying to solve the boot problem with the 8 GB drive in Terminal, using recovery, I could explore it on my running system.

I can see the 8 GB flash using Disk Utility but I cannot explore it.

What is needed?

---

### Post by agillator on 2012-05-12
What do you mean by 'explore' the drive. Do you mean you want to see what is on it? If so, then plug it into a usb port and if the system does not automatically mount it, manually mount it. That should make the contents available to you. There may be permission problems, but those are solvable.

---

### Post by j2bv16 on 2012-05-12
Format the 8gb drive and just explore ir t

---

### Post by agillator on 2012-05-12
CAUTION: Formatting will destroy all the data on the drive. I believe that is NOT what you are trying to do. If I am wrong then have at it. Otherwise . . . .

---

### Post by Boyntonstu on 2012-05-12
> **agillator said:**
> What do you mean by 'explore' the drive. Do you mean you want to see what is on it? If so, then plug it into a usb port and if the system does not automatically mount it, manually mount it. That should make the contents available to you. There may be permission problems, but those are solvable.

The drive is /dev/sde1

How do I mount it?

I intend to examine the boot log file and explore the errors.

---

### Post by codingman on 2012-05-12
go to terminal and type this:
```
mount /dev/sde1
```

You may have to sudo...

---

### Post by Hadaka on 2012-05-12
Explore is a windows term, if you want to view the contents of the usb drive..
right cick start..then explore..find the usb drive...windows should have assigned it a letter
as in E:,F:or some letter. then go to control panel,accessories,dos prompt   C:
once at the dos prompt enter  dir/w F: or what ever drive letter windows gave the usb drive.
you can do the same and print the contents of the workin usb drive to compare the difference 
between the two usb sticks. or if you had a REAL working linux machine, you could plug both
usb sticks in and simply enter.
```

```dif #driveA,driveB

---

### Post by Boyntonstu on 2012-05-12
> **codingman said:**
> go to terminal and type this:
```
mount /dev/sde1
```

You may have to sudo...

boyntonstu@boyntonstu-s5704y:~$ mount /dev/sde1
mount: can't find /dev/sde1 in /etc/fstab or /etc/mtab
boyntonstu@boyntonstu-s5704y:~$ sudo mount /dev/sde1
[sudo] password for boyntonstu: 
mount: can't find /dev/sde1 in /etc/fstab or /etc/mtab
boyntonstu@boyntonstu-s5704y:~$ 
boyntonstu@boyntonstu-s5704y:~$ mount /dev/sde
mount: can't find /dev/sde in /etc/fstab or /etc/mtab
boyntonstu@boyntonstu-s5704y:~$ 


/dev/sde is there.  Disk Utility shows it.

Next?

---

### Post by Boyntonstu on 2012-05-12
> **Hadaka said:**
> Explore is a windows term, if you want to view the contents of the usb drive..
right cick start..then explore..find the usb drive...windows should have assigned it a letter
as in E:,F:or some letter. then go to control panel,accessories,dos prompt   C:
once at the dos prompt enter  dir/w F: or what ever drive letter windows gave the usb drive.
you can do the same and print the contents of the workin usb drive to compare the difference 
between the two usb sticks. or if you had a REAL working linux machine, you could plug both
usb sticks in and simply enter.
```

```dif #driveA,driveB

AFAIK Windows NTFS and Ubuntu ext4 are not compatible.

---

### Post by codingman on 2012-05-12
Can you view the files in it?

---

### Post by Boyntonstu on 2012-05-12
> **codingman said:**
> Can you view the files in it?

No, that is my question.  How to view?

---

### Post by agillator on 2012-05-12
OK, you need to mount the drive manually and then you can see what is on it and open files. To mount manually, you need to know what type of file system is on it. From what you have said I would guess it is ext4. The disk utility should tell you, or at least give you a hint. You also need a place (directory) to mount it. Let's assume you have a directory /tmpmnt. With this information, you would open a terminal and enter the command 'sudo mount -t ext4 /dev/sde1 /tmpmnt' (without the ' of course). Then you can cd to /tmpmnt and do anything you need to depending on permissions, of course. If you need to know the other types, take a look and the man page for mount (man mount) and it will have a list.

---

### Post by wilee-nilee on 2012-05-12
Look in home the 2nd flash should be showing in the left panel, or mount it with the disk utility.

---

