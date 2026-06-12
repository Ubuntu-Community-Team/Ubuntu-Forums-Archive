---
title: "A clean ubuntu installation without access to the windows partition"
date: 2013-01-18
forum: New to Ubuntu
---

### Post by Turtlesarequitenice on 2013-01-18
Hi,
im completly new to ubuntu and generally at installing several Operating Systems on the same HDD, please explain it simple.
Also, english isn't my native language.

I recently installed Ubuntu on the same HDD where i have my windows 7 installation. I thought it's a completly indepentent installation but my ubuntu and windows 7 installations seem to share the same file system. I don't want that. My brother wants to use ubuntu to get used to it but i want absolutely no connection to my windows partition or that he is able to read, change and delete my files.

I currently have on the boot-up screen(i think thats Grub2?):
- Ubuntu
- some memory tests
- Windows 7 (loader) on dev/sda1

How can i change all that to get 2 completly independent operating systems? Keep in mind that i dont want to lose all my files on my windows 7 installation.

Help would be appreciated. :)

---

### Post by mastablasta on 2013-01-18
the only way that no one can access your files on another partition is to encrypt them partition or files on it. 

Ubuntu is an operating system. it can even run in live session with desktop. an operating system is what is made to communicate with hardware and what is found on hardware. so to not be able to access the files on hardware the only way is to encrypt them or prevent phisycal access to computer. 

grub is a bootloader that replaces windows boot loader. it is there because it can boot multiple operating systems (while windows boot loader can only boot microsoft based operating systems)

---

### Post by cypa on 2013-01-18
Perhaps you may wish to consider installing yourself as a separate user of the Linux system then bro cannot enter your account without your password.
It means of course you must be the established root since root can also get to any file.
Encryption is the only way to keep as private as possible since anyone with physical access to the computer can obtain access to the files with a CD disk
good luck:popcorn:

---

### Post by Mark Phelps on 2013-01-19
> **Turtlesarequitenice said:**
> I currently have on the boot-up screen(i think thats Grub2?):
- Ubuntu
- some memory tests
- Windows 7 (loader) on dev/sda1

How can i change all that to get 2 completly independent operating systems? Keep in mind that i dont want to lose all my files on my windows 7 installation.

First of all, they do NOT share the same filesystem.  Windows uses NTFS; Ubuntu uses Ext4.  Windows can't even READ Ext4.

Second, they are completely independent operating systems.  You boot into one or the other, not both.

What Ubuntu DOES do is allow you to "mount" the windows filesystem in read/write mode by default; meaning, that any changes can then be made to it.

As folks have mentioned, the only way to keep someone in Ubuntu from accessing the Windows filesystem is to encrypt the partition -- but be aware, if the boot loader files are on that partition, encrypting it will prevent Windows from booting.  You would have to move the Windows boot loader files to their OWN partition, one that you would NOT encrypt.

---

### Post by grahammechanical on 2013-01-19
Can we be clear about something? How did you install Ubuntu? Did you install it using Wubi.exe? Using the windows installer? If you did then you installed Ubuntu inside of Windows.

[http://www.ubuntu.com/download/help/install-ubuntu-with-windows]("http://www.ubuntu.com/download/help/install-ubuntu-with-windows")

Or did you run a live session and then selected to install Ubuntu using the Install alongside windows option?

[http://www.ubuntu.com/download/help/install-desktop-latest]("http://www.ubuntu.com/download/help/install-desktop-latest")

If this is what you did (and from the menu list I think that you did do it), then Ubuntu is already a completely separate operating system.

Regards.

---

### Post by Turtlesarequitenice on 2013-01-19
I did not use wubi.exe, i installed it as an independant OS.

The problem is that i can access all the files from both OS.
Thanks for the possible solutions so far. :)

Solution 1.
What would be the easiest way to encrypt the partition (I would have to encrypt the windows partition?) while still being able to boot from both Operating Systems. As far as i understand the problem is that i would encrypt the windows loader as well, correct?
That still looks like the best solution so far or are there any downsides like slow hdd access or anything?
How would i do that?

Solution 2.
Is it possible to simply unmount all the windows files?

Solution 3.
Can i just create a new user on Ubuntu with restricted access? The user should still be able to do have as much rights as possible, just not accessing the windows files.

Solution 4.
How about reinstalling Ubuntu with wubi.exe? I would install it as part of my windows but isn't it easier to restrict access to the rest of the files that way?
How could i remove the current installation if i did this?

In any case thanks for your time. :)

---

### Post by Impavidus on 2013-01-19
You can make sure in your /etc/fstab so that you (and your brother) need root privileges to mount the windows partition, but with root privileges or a live dvd (or a recovery console) he can always access your windows file: physical access is root access. If you've encrypted your windows documents he cannot read or modify them, but still delete. Just format the windows partition.

But hey, were are we going with this world if one can't even trust one's own brother (I've one too)? I mean, a practical joke is one thing, but do you really expect he will do you harm?

---

