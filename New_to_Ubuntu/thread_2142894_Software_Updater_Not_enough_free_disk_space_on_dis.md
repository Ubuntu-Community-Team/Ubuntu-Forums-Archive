---
title: "Software Updater: Not enough free disk space on disk '/boot'"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by TooFreppaT on 2013-05-07
I am trying to update, not upgrade
I click on Software Updater
it check for Updates
I click Install Now
I get the following~

[IMG]http://s21.postimg.org/552mrp4jb/Screenshot_from_2013_05_07_16_38_06.png[/IMG]

my Rubbish Bin is empty and I have tried```
sudo apt-get clean
```but it didn't fix anything and I'm still getting this same messages
I have also tried Restart... but I'm not sure if Restart... is different to Shut Down... so maybe I will try Shut Down... instead

---

### Post by monkeybrain2012 on 2013-05-07
Seems like your root directory is full. 

Open the terminal and type 

```
df -h
```

and let's see the output.

Also what was the terminal output when you ran 

```
sudo apt-get clean
```

P.S. Is this a WUBI install by any chance?

---

### Post by TenPlus1 on 2013-05-07
You could try and install Bleachbit and run the admin version to remove unecessary temp files and such from your root and home...

---

### Post by monkeybrain2012 on 2013-05-07
> **TenPlus1 said:**
> You could try and install Bleachbit and run the admin version to remove unecessary temp files and such from your root and home...

He has probably run out of room to install bleachbit, :)

---

### Post by TooFreppaT on 2013-05-07
> **monkeybrain2012 said:**
> Seems like your root directory is full. 

Open the terminal and type 

```
df -h
```

and let's see the output.

Also what was the terminal output when you ran 

```
sudo apt-get clean
```

P.S. Is this a WUBI install by any chance?
```
TooFreppaT@TooFreppaT:~$ df -h
Filesystem                     Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root        2.7T  493G  2.1T  19% /
udev                           7.7G  4.0K  7.7G   1% /dev
tmpfs                          3.1G  892K  3.1G   1% /run
none                           5.0M  8.0K  5.0M   1% /run/lock
none                           7.8G  164K  7.8G   1% /run/shm
none                           100M   28K  100M   1% /run/user
/dev/sda2                      229M  189M   29M  88% /boot
/home/TooFreppaT/.Private      2.7T  493G  2.1T  19% /home/TooFreppaT
/dev/sdb1                      7.2G  763M  6.5G  11% /media/TooFreppaT/6748-2BC8
TooFreppaT@TooFreppaT:~$ sudo apt-get clean
[sudo] password for TooFreppaT: 
TooFreppaT@TooFreppaT:~$ 
```
what is WUBI? I clean-installed this one from one of the previous three  versions of Ubuntu, I cannot remember which one but it didn't have Unity so it was the one just before Unity was implemented, here this is a  snapshot of my current system.

[IMG]http://s9.postimg.org/5vfqyp5b3/Screenshot_from_2013_05_07_18_32_47.png[/IMG]
> **TenPlus1 said:**
> You could try and install Bleachbit and run the  admin version to remove unecessary temp files and such from your root  and home...
is Bleachbit easy to use?

---

### Post by monkeybrain2012 on 2013-05-07
See if this helps

[http://ubuntuforums.org/showthread.php?t=1435818](http://ubuntuforums.org/showthread.php?t=1435818)

---

### Post by TooFreppaT on 2013-05-07
> **monkeybrain2012 said:**
> See if this helps

[http://ubuntuforums.org/showthread.php?t=1435818](http://ubuntuforums.org/showthread.php?t=1435818)
apart from *linux-image-3.5.0-27-generic* and *linux-image-extra-3.5.0-27-generic*, are there any that I should not remove? like *linux-image* and *linux-image-3.0* and *linux-image-generic*
```
TooFreppaT@TooFreppaT:~$ uname -r
3.5.0-27-generic
TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
ii  linux-image-3.5.0-17-generic                  3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-23-generic                  3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-24-generic                  3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-25-generic                  3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-26-generic                  3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-17-generic            3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-23-generic            3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-24-generic            3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-25-generic            3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-26-generic            3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.5.0.27.43                 amd64                       Generic Linux kernel image
TooFreppaT@TooFreppaT:~$ sudo apt-get remove linux-image-3.5.0-17-generic linux-image-3.5.0-23-generic linux-image-3.5.0-24-generic linux-image-3.5.0-25-generic linux-image-3.5.0-26-generic linux-image-extra-3.5.0-17-generic linux-image-extra-3.5.0-23-generic linux-image-extra-3.5.0-24-generic linux-image-extra-3.5.0-25-generic linux-image-extra-3.5.0-26-generic
[sudo] password for TooFreppaT: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.5.0-17-generic linux-image-3.5.0-23-generic linux-image-3.5.0-24-generic linux-image-3.5.0-25-generic linux-image-3.5.0-26-generic linux-image-extra-3.5.0-17-generic
  linux-image-extra-3.5.0-23-generic linux-image-extra-3.5.0-24-generic linux-image-extra-3.5.0-25-generic linux-image-extra-3.5.0-26-generic
0 upgraded, 0 newly installed, 10 to remove and 5 not upgraded.
After this operation, 765 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 157148 files and directories currently installed.)
Removing linux-image-extra-3.5.0-17-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.5.0-17-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-17-generic /boot/vmlinuz-3.5.0-17-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-extra-3.5.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.5.0-23-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-23-generic /boot/vmlinuz-3.5.0-23-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found initrd image: /boot/initrd.img-3.5.0-24-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-extra-3.5.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-24-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.5.0-24-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-24-generic /boot/vmlinuz-3.5.0-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-extra-3.5.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.5.0-25-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-25-generic /boot/vmlinuz-3.5.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found initrd image: /boot/initrd.img-3.5.0-26-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-extra-3.5.0-26-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found linux image: /boot/vmlinuz-3.5.0-26-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.5.0-26-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-26-generic /boot/vmlinuz-3.5.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found initrd image: /boot/initrd.img-3.5.0-27-generic
Found memtest86+ image: /memtest86+.bin
done
TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
rc  linux-image-3.5.0-17-generic                  3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-23-generic                  3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-24-generic                  3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-25-generic                  3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-26-generic                  3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-17-generic            3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-23-generic            3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-24-generic            3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-25-generic            3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-26-generic            3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.5.0.27.43                 amd64                       Generic Linux kernel image
TooFreppaT@TooFreppaT:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
rc  linux-image-3.5.0-17-generic                  3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-23-generic                  3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-24-generic                  3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-25-generic                  3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-26-generic                  3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-17-generic            3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-23-generic            3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-24-generic            3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-25-generic            3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-26-generic            3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.5.0.27.43                 amd64                       Generic Linux kernel image
TooFreppaT@TooFreppaT:~$ 

```
nothing happened, they are all still there anyway :( I will try Restart...

---

### Post by TooFreppaT on 2013-05-07
okay, so upon Restart... I get Software Updater popup and I try to install and it installs so it works :) but I Restart... anyway
```
TooFreppaT@TooFreppaT:~$ df -h
Filesystem                     Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu-root        2.7T  492G  2.1T  19% /
udev                           7.7G  4.0K  7.7G   1% /dev
tmpfs                          3.1G  888K  3.1G   1% /run
none                           5.0M  8.0K  5.0M   1% /run/lock
none                           7.8G  160K  7.8G   1% /run/shm
none                           100M   28K  100M   1% /run/user
/dev/sda2                      229M   67M  151M  31% /boot
/home/TooFreppaT/.Private      2.7T  492G  2.1T  19% /home/TooFreppaT
/dev/sdb1                      7.2G  763M  6.5G  11% /media/TooFreppaT/6748-2BC8
TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
rc  linux-image-3.5.0-17-generic                  3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-23-generic                  3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-24-generic                  3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-25-generic                  3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-26-generic                  3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-17-generic            3.5.0-17.28                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-23-generic            3.5.0-23.35                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-24-generic            3.5.0-24.37                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-25-generic            3.5.0-25.39                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-26-generic            3.5.0-26.42                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.5.0.28.44                 amd64                       Generic Linux kernel image
TooFreppaT@TooFreppaT:~$ 

```
now after Restart... they are all still there even though I remove them?

---

### Post by Impavidus on 2013-05-07
rc means remaining configuration. You can savely purge them:
```

sudo apt-get purge linux-image-3.5.0-17-generic
```etc.

---

### Post by TooFreppaT on 2013-05-07
is it safe to remove _linux-image_ and _linux-image-3.0_ and _linux-image-generic_?

---

### Post by Impavidus on 2013-05-07
linux-image and linux-image-generic are metapackages pointing at the latest linux-image-something, ensuring you get the updates. Keep them.
linux-image-3.0 sounds like something old, as everything else is at 3.5. Not sure what it is.

---

### Post by grahammechanical on 2013-05-07
Compare the two listings to df -h that you have provided.

> 
1)   /dev/sda2
Size     Used    Avail  Used%   Mounted on
                           229M   189M   29M   88%       /boot

2)  /dev/sda
Size Used Avail Used% Mounted on
229M    67M   151M   31%     /boot

= job done. You have gone from 29M Available to 151M Available.

Do not remove anything with Linux 3.5.0-27 or Linux 3.5.0-28. Those are your two latest kernels. We always keep at least one previous kernel to boot into if the present kernel fails to load for some reason. Have you noticed that since you were able to run Update Manager you have got Linux kernel 3.5.0-28 in all its parts.

You might want to think about increasing the size of sda2. Or using Synaptic Package Manager to trim out excessive previous kernels.

Regards.

---

### Post by bcbc on 2013-05-07
I wrote a script to remove all but the two most recent kernels. You can just run it periodically, usually after rebooting following a kernel update. That will keep the /boot directory clean.

```
wget https://raw.github.com/bcbc/utilities/master/clean_kernel.sh
bash clean_kernel.sh
```

The actual script is a two liner that was originally posted in the ubuntu-devel mailing list (by Kees Cook I believe):
```
[COLOR=#008080][FONT=Consolas]OLD[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**=**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**$(**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]ls -tr /boot/vmlinuz-* | head -n -2 | cut -d- -f2- | awk [/FONT][/COLOR][COLOR=#DD1144][FONT=Consolas]'{print "linux-image-" $0}'[/FONT][/COLOR][COLOR=#333333][FONT=Consolas][B])
[/B][/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**if **[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**[**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] -n [/FONT][/COLOR][COLOR=#DD1144][FONT=Consolas]"$OLD" [/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**]**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]; [/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**then **[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]sudo apt-get -q remove --purge [/FONT][/COLOR][COLOR=#008080][FONT=Consolas]$OLD[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]; [/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**fi**[/FONT][/COLOR]
```

---

### Post by TooFreppaT on 2013-05-07
I accidentally deleted **linux-image-extra-3.5.0-28-generic** and **linux-image-generic** (it automatically went after I deleted 28, miss-type 27)
I have already deleted **linux-image-3.5.0-27-generic** and **linux-image-extra-3.5.0-27-generic**
```
TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
TooFreppaT@TooFreppaT:~$ 

```

how can I get them all back? or have I now broken my operating system? I rarely turn off my computer.

---

### Post by TooFreppaT on 2013-05-07
here is everything I did
```
**TooFreppaT@TooFreppaT:~$ uname -r**
3.5.0-28-generic
**TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
ii  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.5.0.28.44                 amd64                       Generic Linux kernel image
**TooFreppaT@TooFreppaT:~$ sudo apt-get remove linux-image-3.5.0-27-generic linux-image-extra-3.5.0-28-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.5.0-27-generic linux-image-extra-3.5.0-27-generic linux-image-extra-3.5.0-28-generic linux-image-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 275 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140305 files and directories currently installed.)
Removing linux-image-extra-3.5.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found linux image: /boot/vmlinuz-3.5.0-27-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-3.5.0-27-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-generic ...
Removing linux-image-extra-3.5.0-28-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
update-initramfs: Deleting /boot/initrd.img-3.5.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-28-generic /boot/vmlinuz-3.5.0-28-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found memtest86+ image: /memtest86+.bin
done
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
**TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
rc  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
**TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
rc  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
**TooFreppaT@TooFreppaT:~$ sudo apt-get purge linux-image-3.5.0-27-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.5.0-27-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132633 files and directories currently installed.)
Removing linux-image-3.5.0-27-generic ...
Purging configuration files for linux-image-3.5.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
**TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
un  linux-image-3.5.0-27-generic                  <none>                                                  (no description available)
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
**TooFreppaT@TooFreppaT:~$ sudo apt-get purge linux-image-extra-3.5.0-27-generic**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.5.0-27-generic*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 132633 files and directories currently installed.)
Removing linux-image-extra-3.5.0-27-generic ...
Purging configuration files for linux-image-extra-3.5.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.5.0-27-generic /boot/vmlinuz-3.5.0-27-generic
**TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'**
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
**TooFreppaT@TooFreppaT:~$ **

```

---

### Post by Impavidus on 2013-05-08
Just reinstall them
```

sudo apt-get install package-you-accidentally-removed

```
You're not running them right now, so your computer should still boot. I advise you to keep one old kernel at all times, just in case you break your current one.

---

### Post by TooFreppaT on 2013-05-08
okay, I have reinstalled them all again, this is what I have now```
TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
ii  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic            3.5.0-28.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.5.0.28.44                 amd64                       Generic Linux kernel image
TooFreppaT@TooFreppaT:~$ 

```
but after when linux-image-generic and linux-image-extra-3.5.0-28-generic both got deleted together it did this```

The link /initrd.img is a damaged link
Removing symbolic link initrd.img
  you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
  you may need to re-run your boot loader[grub]
```
so when I reinstalled them did it fix that aswell? I don't know how to re-run my boot loader[grub]

---

### Post by TooFreppaT on 2013-05-11
I have found [this]("http://askubuntu.com/questions/18804/what-do-the-various-dpkg-flags-like-ii-rc-mean")
```
TooFreppaT@TooFreppaT:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                                                  (no description available)
un  linux-image-3.0                               <none>                                                  (no description available)
ii  linux-image-3.5.0-27-generic                  3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-3.5.0-28-generic                  3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-27-generic            3.5.0-27.46                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-28-generic            3.5.0-28.48                 amd64                       Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.5.0.28.44                 amd64                       Generic Linux kernel image
TooFreppaT@TooFreppaT:~$

```
since [COLOR=#696969]*linux-image*[/COLOR] and [COLOR=#696969]*linux-image-3.0*[/COLOR] are both unknown and not-installed, is it safe and should I remove/purge them?

---

### Post by TooFreppaT on 2013-05-14
> **grahammechanical said:**
> You might want to think about increasing the size of sda2. Or using Synaptic Package Manager to trim out excessive previous kernels.
how can I do these things? and does it have anything to do with [this]("https://en.wikipedia.org/wiki/Configuration_file")?

---

### Post by temporos on 2013-09-06
I know I'm kinda resurrecting an old thread, but my question is the same as the OP's, and I want to verify something.

Which of these packages can I safely remove using *apt-get remove*? Also, does it matter that the dpkg flags on many of them are still "ii" instead of "rc"?

```
$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-=============================================================================
un  linux-image                          <none>                                          (no description available)
un  linux-image-3.0                      <none>                                          (no description available)
rc  linux-image-3.8.0-19-generic         3.8.0-19.30             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-21-generic         3.8.0-21.32             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-23-generic         3.8.0-23.34             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-25-generic         3.8.0-25.37             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-26-generic         3.8.0-26.38             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-29-generic         3.8.0-29.42             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-19-generic   3.8.0-19.30             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-21-generic   3.8.0-21.32             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-23-generic   3.8.0-23.34             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-25-generic   3.8.0-25.37             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-26-generic   3.8.0-26.38             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-29-generic   3.8.0-29.42             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                  3.8.0.29.47             i386                    Generic Linux kernel image

```

---

### Post by Impavidus on 2013-09-06
rc=removed, but configuration remaining.
ii=installed, not marked for change. If you mark them for removal, they can be removed automatically.

You can safely remove the packages with version numbers 3.8.0-19, 3.8.0-21, 3.8.0-23 and 3.8.0-25, just keeping the current one and one older kernel. There may also be some linux-header-* packages with these version numbers, you can uninstall those too. You can also remove the configuration using **sudo apt-get --purge remove <package name>**

---

### Post by heir4c on 2013-09-06
....

Oops, I don't see the post above, so I deleted my answer.

---

### Post by temporos on 2014-02-11
First, thanks to everyone who's participated in this thread! :D It's been very helpful at several times since it was "new." New question along the same vein.

Can I remove all these headers, too? As you can see, I have only the *34-generic* and *35-generic* images. How much space would removing those headers free up?

```

jonathan@Mizuki:~$ dpkg -l 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-=============================================================================
un  linux-image                          <none>                                          (no description available)
un  linux-image-3.0                      <none>                                          (no description available)
ii  linux-image-3.8.0-34-generic         3.8.0-34.49             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-35-generic         3.8.0-35.50             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-34-generic   3.8.0-34.49             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-35-generic   3.8.0-35.50             i386                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                  3.8.0.35.53             i386                    Generic Linux kernel image
jonathan@Mizuki:~$ dpkg -l 'linux-headers*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-=============================================================================
un  linux-headers                        <none>                                          (no description available)
un  linux-headers-3.0                    <none>                                          (no description available)
ii  linux-headers-3.8.0-21               3.8.0-21.32             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-21-generic       3.8.0-21.32             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-23               3.8.0-23.34             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-23-generic       3.8.0-23.34             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-25               3.8.0-25.37             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-25-generic       3.8.0-25.37             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-26               3.8.0-26.38             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-26-generic       3.8.0-26.38             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-29               3.8.0-29.42             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-29-generic       3.8.0-29.42             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31               3.8.0-31.46             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic       3.8.0-31.46             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32               3.8.0-32.47             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic       3.8.0-32.47             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-33               3.8.0-33.48             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-33-generic       3.8.0-33.48             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-34               3.8.0-34.49             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-34-generic       3.8.0-34.49             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-35               3.8.0-35.50             all                     Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-35-generic       3.8.0-35.50             i386                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic                3.8.0.35.53             i386                    Generic Linux kernel headers

```

---

### Post by Impavidus on 2014-02-12
Yes, headers belonging to kernel versions you have uninstalled can be uninstalled too. I always do so, to keep my system neat and tidy. I your case that would be the header packages version 21–33. It should save you about 60MB per version, in addition to several thousand inodes. The files in these packages are not located on the /boot partition, so it won't give you extra space there

---

