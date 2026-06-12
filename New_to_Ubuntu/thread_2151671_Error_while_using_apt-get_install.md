---
title: "Error while using apt-get install"
date: 2013-06-05
forum: New to Ubuntu
---

### Post by ultrabeat on 2013-06-05
Please Help,
While trying to install unrar im getting the following error

```
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-22-generic_3.8.0-22.33_amd64.deb
 /var/cache/apt/archives/linux-image-3.8.0-23-generic_3.8.0-23.34_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i have tried apt-get -f install to try and fix the problem but i 
have not been able to fix it, any help would be very grateful
thanks

---

### Post by oldos2er on 2013-06-05
Try ```
sudo apt-get clean

sudo apt-get update

sudo apt-get dist-upgrade

sudo apt-get install unrar
```

---

### Post by ultrabeat on 2013-06-05
thanks for the help but sadly no joy
used:
```
[COLOR=#000000][FONT=Ubuntu Mono]
sudo apt-get clean
sudo apt-get update
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
Were fine but as soon as i ran
[/FONT][/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]
sudo apt-get dist-upgrade
[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
i got
[/FONT][/COLOR]```
main@Main-Ubuntu-Server:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run âapt-get -f installâ to correct these.
The following packages have unmet dependencies.
 linux-image-extra-3.8.0-22-generic : Depends: linux-image-3.8.0-22-generic but it is not installed
 linux-image-extra-3.8.0-23-generic : Depends: linux-image-3.8.0-23-generic but it is not installed
 linux-image-generic : Depends: linux-image-3.8.0-23-generic but it is not installed
E: Unmet dependencies. Try using -f.

```[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by oldos2er on 2013-06-05
At that point does ```
sudo apt-get install -f
``` do anything helpful?

---

### Post by ultrabeat on 2013-06-05
tried your response but still getting

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-27 linux-headers-3.5.0-27-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.8.0-22-generic linux-image-3.8.0-23-generic
Suggested packages:
  fdutils linux-doc-3.8.0 linux-source-3.8.0 linux-tools
The following NEW packages will be installed
  linux-image-3.8.0-22-generic linux-image-3.8.0-23-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
34 not fully installed or removed.
Need to get 24.8 MB of archives.
After this operation, 67.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ raring-updates/main linux-image-3.8.0-22-generic amd64 3.8.0-22.33 [12.4 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ raring-updates/main linux-image-3.8.0-23-generic amd64 3.8.0-23.34 [12.4 MB]
Fetched 24.8 MB in 9s (2,659 kB/s)
(Reading database ... 198642 files and directories currently installed.)
Unpacking linux-image-3.8.0-22-generic (from .../linux-image-3.8.0-22-generic_3.8.0-22.33_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-22-generic_3.8.0-22.33_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.8.0-22-generic' to '/boot/vmlinuz-3.8.0-22-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-22-generic /boot/vmlinuz-3.8.0-22-generic
Unpacking linux-image-3.8.0-23-generic (from .../linux-image-3.8.0-23-generic_3.8.0-23.34_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-23-generic_3.8.0-23.34_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.8.0-23-generic' to '/boot/vmlinuz-3.8.0-23-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-22-generic_3.8.0-22.33_amd64.deb
 /var/cache/apt/archives/linux-image-3.8.0-23-generic_3.8.0-23.34_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by varunendra on 2013-06-05
I think you have the problem clearly stated now -
> **ultrabeat said:**
> ```

dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-22-generic_3.8.0-22.33_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-3.8.0-22-generic' to '/boot/vmlinuz-3.8.0-22-generic.dpkg-new': failed to write **[COLOR="#FF0000"](No space left on device)[/COLOR]**

```

To confirm remaining space on your root partition -
```
df -h
```
Try clearing some space by moving user data (if you have your 'Home' on the same partition) to another partition, or removing some packages that you do not use (including older linux kernel images).

---

