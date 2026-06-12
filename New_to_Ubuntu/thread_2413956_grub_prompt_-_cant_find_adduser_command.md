---
title: "grub prompt - cant find adduser command"
date: 2019-03-04
forum: New to Ubuntu
---

### Post by autocoder2 on 2019-03-04
I have booted into the GRUB prompt by pressing ESCAPE during the boot.

Now I want to run adduser command to add my user account as a super user account.

```
grub> adduser steve sudo
error: can't find command "adduser"
```

what to do? 

This is GNU GRUB version 2.02.   

Running on a standalone PC. My user account is the only account on the system.

Doing this because I cannot run sudo. sudoers.so only writable by owner:

```
steve@steve-All-Series:~$ sudo apt install curl
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
steve@steve-All-Series:~$ 
```

also, pressing ESCAPE is the only way I have been able to get to GRUB.  Pressing left shift or F1 during boot has not worked.

-thanks,

---

### Post by yancek on 2019-03-04
You can't add a user to the operating system from the Grub prompt as Grub is just a bootloader.  The link below shows a list of available commands in Grub which does not include adduser or useradd.

[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)

Looks like you have a problem with your /etc/sudo.conf file.  You might post it and someone would be able to help.

---

### Post by ajgreeny on 2019-03-04
Have you manually edited your /etc/sudoers file using a standard text editor instead of the advised visudo?

Using visudo will check the syntax of the file before saving to ensure there are no problems.

Or have you made changes to files in the filesystem at some point in the past without realising that they should not be edited unless you know exactly what you're doing and why.

---

### Post by autocoder2 on 2019-03-04
> **yancek said:**
> You can't add a user to the operating system from the Grub prompt as Grub is just a bootloader.  The link below shows a list of available commands in Grub which does not include adduser or useradd.

[https://www.gnu.org/software/grub/manual/grub/grub.html](https://www.gnu.org/software/grub/manual/grub/grub.html)

Looks like you have a problem with your /etc/sudo.conf file.  You might post it and someone would be able to help.

there is no /etc/sudo.conf file.

---

### Post by autocoder2 on 2019-03-04
> **ajgreeny said:**
> Have you manually edited your /etc/sudoers file using a standard text editor instead of the advised visudo?

Using visudo will check the syntax of the file before saving to ensure there are no problems.

Or have you made changes to files in the filesystem at some point in the past without realising that they should not be edited unless you know exactly what you're doing and why.

made no changes.  Downloaded Ubuntu from the official web site over the weekend. Burned it to a USB and then installed from that USB.

I run this:
```
steve@steve-All-Series:/etc$ visudo sudoers
usage: visudo [-chqsV] [-f sudoers] [-x output_file]
steve@steve-All-Series:/etc$ sudo visudo
sudo: error in /etc/sudo.conf, line 0 while loading plugin "sudoers_policy"
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
```

here is a list of the su* files in /etc:
```
steve@steve-All-Series:/etc$ ls -a su*
subgid  subgid-  subuid  subuid-  sudoers


sudoers.d:
```

Can I just create the sudo.conf file?

---

### Post by ajgreeny on 2019-03-05
I also have no /etc/sudo.conf file so I do not believe that is worrying.
However, it looks as if the /usr/lib/sudo/sudoers.so file has incorrect permissions so please show us what output you get from command ```
ls -l /usr/lib/sudo/sudoers.so
```
It should be very similar to
```
-rw-r--r-- 1 root root 354592 Jan 18  2018 /usr/lib/sudo/sudoers.so
``` with ownership as **root** and permissions **-rw-r--r--**
If it is wrongly owned or has the incorrect permissions you will probably have to boot into recovery mode from grub and make changes from that.

One step at a time, but we can hopefully figure this out!

---

### Post by autocoder2 on 2019-03-05
> **ajgreeny said:**
> I also have no /etc/sudo.conf file so I do not believe that is worrying.
However, it looks as if the /usr/lib/sudo/sudoers.so file has incorrect permissions so please show us what output you get from command ```
ls -l /usr/lib/sudo/sudoers.so
```
It should be very similar to
```
-rw-r--r-- 1 root root 354592 Jan 18  2018 /usr/lib/sudo/sudoers.so
``` with ownership as **root** and permissions **-rw-r--r--**
If it is wrongly owned or has the incorrect permissions you will probably have to boot into recovery mode from grub and make changes from that.

One step at a time, but we can hopefully figure this out!

here is the sudoers.so file.  thanks for the help!

steve@steve-All-Series:~$ ls -l /usr/lib/sudo/sudoers.so
-rw-rw-rw- 1 root root 354592 Jan 17  2018 /usr/lib/sudo/sudoers.so
steve@steve-All-Series:~$

---

### Post by SeijiSensei on 2019-03-06
Have you not tried booting into recovery mode then choosing "root shell" from the menu? 

To make changes to any files, you'll need to first run the command

```
mount -o remount,rw /
```

since the filesystem is mounted read-only by default in rescue mode.  Now you should be able to edit any file or run any command on the system with root privileges. (No GUI, of course.)

---

### Post by ajgreeny on 2019-03-06
It looks as if the permissions of that sudoers.so file are the cause your problem; your **-rw-rw-rw-** should be **-rw-r--r--** so you will need to boot into a root shell from grub ->Recovery mode, then run command ```
mount -o remount,rw /
``` to make the filesystem read/write (it is mounted read only in recovery mode for safety) then run command ```
[COLOR="#FF0000"]chmod 644 /usr/lib/sudo/sudoers.so[/COLOR]
``` and finally reboot.

Now see if **sudo apt update** in terminal works; if you made permission changes to that file alone all ought to proceed as it should but if you made changes to any other system files it is impossible to know what will or will not work as expected.

Good luck.

[COLOR="#FF0000"]EDIT:[/COLOR]
Please note my edit to the command ```
[COLOR="#FF0000"]chmod 644 /usr/lib/sudo/sudoers.so[/COLOR]
``` where I inadvertently used a chown command in its place.

If you ran that **chown** command check the files ownership again from recovery mode with the ```
ls -l /usr/lib/sudo/sudoers.so
``` and if it now belongs to 664 run command ```
chown root:root /usr/lib/sudo/sudoers.so
```
My sincere apologies for my goof !!!

---

### Post by autocoder2 on 2019-03-06
working now.   thanks for staying with me.

---

### Post by ajgreeny on 2019-03-07
Brilliant!!

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

