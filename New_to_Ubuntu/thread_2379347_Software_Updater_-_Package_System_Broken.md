---
title: "Software Updater - Package System Broken"
date: 2017-12-04
forum: New to Ubuntu
---

### Post by Raggylad on 2017-12-04
I'm running Ubuntu 16.04 LTS (64 bit) and having problems with the software updater.

When I run the updater, I get two error messages:

- 'Failed to download repository information.  Check your internet connection' (there's nothing wrong with it).

- 'The package system is broken', following which Updater crashes.

I've then opened a terminal and tried:

> apt-get install -f

after which I get this:

>                          [FONT=Liberation Sans]Reading package lists... Done[/FONT]
 [FONT=Liberation Sans]W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)[/FONT]
 [FONT=Liberation Sans]E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)[/FONT]
 [FONT=Liberation Sans]E: Unable to lock directory /var/lib/apt/lists/[/FONT]
 [FONT=Liberation Sans]W: Problem unlinking the file /var/cache/apt/pkgcache.bin - RemoveCaches (13: Permission denied)[/FONT]
 [FONT=Liberation Sans]W: Problem unlinking the file /var/cache/apt/srcpkgcache.bin - RemoveCaches (13: Permission denied)[/FONT]
  

At which point my very limited ability with Linux reaches its limits !

Very grateful for any advice or help.

Thanks.

---

### Post by Bashing-om on 2017-12-04
Raggylad; Hello -

Apt has to have admin (sudo) privileges .
Let us see the whole story.
Post back - Between code tags - the outputs of terminal commands:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install

```


[INDENT][INDENT]a tale gets told
[/INDENT][/INDENT]

---

### Post by Raggylad on 2017-12-04
Bashin-om, Hi.

Here's what I get:

```
   	 	 	 	   [FONT=Liberation Sans, sans-serif]sudo apt update[/FONT]
 [FONT=Liberation Sans, sans-serif][sudo] password for nick: [/FONT] 
 [FONT=Liberation Sans, sans-serif]Hit:1 http://gb.archive.ubuntu.com/ubuntu xenial InRelease[/FONT]
 [FONT=Liberation Sans, sans-serif]Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    [/FONT] 
 [FONT=Liberation Sans, sans-serif]Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     [/FONT] 
 [FONT=Liberation Sans, sans-serif]Hit:4 http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu xenial InRelease[/FONT]
 [FONT=Liberation Sans, sans-serif]Hit:5 http://archive.canonical.com/ubuntu xenial InRelease                     [/FONT] 
 [FONT=Liberation Sans, sans-serif]Hit:6 http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial InRelease       [/FONT] 
 [FONT=Liberation Sans, sans-serif]Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  [/FONT] 
 [FONT=Liberation Sans, sans-serif]Ign:8 http://dl.google.com/linux/earth/deb stable InRelease                    [/FONT] 
 [FONT=Liberation Sans, sans-serif]Get:9 http://repository.spotify.com stable InRelease [3,302 B]                 [/FONT] 
 [FONT=Liberation Sans, sans-serif]Get:10 http://dl.google.com/linux/earth/deb stable Release [2,136 B]           [/FONT] 
 [FONT=Liberation Sans, sans-serif]Err:9 http://repository.spotify.com stable InRelease           [/FONT] 
   [FONT=Liberation Sans, sans-serif]The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFDC8610341D9410[/FONT]
 [FONT=Liberation Sans, sans-serif]Get:11 http://dl.google.com/linux/earth/deb stable Release.gpg [819 B][/FONT]
 [FONT=Liberation Sans, sans-serif]Err:11 http://dl.google.com/linux/earth/deb stable Release.gpg[/FONT]
   [FONT=Liberation Sans, sans-serif]The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551[/FONT]
 [FONT=Liberation Sans, sans-serif]Fetched 311 kB in 1s (280 kB/s)  [/FONT] 
 [FONT=Liberation Sans, sans-serif]Reading package lists... Done[/FONT]
 [FONT=Liberation Sans, sans-serif]Building dependency tree       [/FONT] 
 [FONT=Liberation Sans, sans-serif]Reading state information... Done[/FONT]
 [FONT=Liberation Sans, sans-serif]203 packages can be upgraded. Run 'apt list --upgradable' to see them.[/FONT]
 [FONT=Liberation Sans, sans-serif]W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://repository.spotify.com stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFDC8610341D9410[/FONT]
 [FONT=Liberation Sans, sans-serif]W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/earth/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551[/FONT]
 [FONT=Liberation Sans, sans-serif]W: Failed to fetch http://repository.spotify.com/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EFDC8610341D9410[/FONT]
 [FONT=Liberation Sans, sans-serif]W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551[/FONT]
 [FONT=Liberation Sans, sans-serif]W: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]
  sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libappstream3 libllvm3.8 libmircommon5 linux-headers-4.4.0-64
  linux-headers-4.4.0-64-generic linux-headers-4.4.0-66
  linux-headers-4.4.0-66-generic linux-headers-4.4.0-70
  linux-headers-4.4.0-70-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72
  linux-headers-4.4.0-72-generic linux-headers-4.4.0-75
  linux-headers-4.4.0-75-generic linux-headers-4.4.0-78
  linux-headers-4.4.0-78-generic linux-headers-4.4.0-79
  linux-headers-4.4.0-79-generic linux-headers-4.4.0-81
  linux-headers-4.4.0-81-generic linux-headers-4.4.0-83
  linux-headers-4.4.0-83-generic linux-headers-4.4.0-87
  linux-headers-4.4.0-87-generic linux-headers-4.4.0-89
  linux-headers-4.4.0-89-generic linux-headers-4.4.0-92
  linux-headers-4.4.0-92-generic linux-headers-4.4.0-96
  linux-image-4.4.0-64-generic linux-image-4.4.0-66-generic
  linux-image-4.4.0-70-generic linux-image-4.4.0-71-generic
  linux-image-4.4.0-72-generic linux-image-4.4.0-75-generic
  linux-image-4.4.0-78-generic linux-image-4.4.0-79-generic
  linux-image-4.4.0-81-generic linux-image-4.4.0-83-generic
  linux-image-4.4.0-87-generic linux-image-4.4.0-89-generic
  linux-image-4.4.0-92-generic linux-image-extra-4.4.0-64-generic
  linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-70-generic
  linux-image-extra-4.4.0-71-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-75-generic linux-image-extra-4.4.0-78-generic
  linux-image-extra-4.4.0-79-generic linux-image-extra-4.4.0-81-generic
  linux-image-extra-4.4.0-83-generic linux-image-extra-4.4.0-87-generic
  linux-image-extra-4.4.0-89-generic linux-image-extra-4.4.0-92-generic
  snap-confine
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-generic linux-headers-4.4.0-101 linux-headers-4.4.0-101-generic
  linux-headers-4.4.0-96 linux-headers-generic linux-image-4.4.0-101-generic
  linux-image-extra-4.4.0-101-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed
  linux-headers-4.4.0-101 linux-headers-4.4.0-101-generic
  linux-image-4.4.0-101-generic linux-image-extra-4.4.0-101-generic
The following packages will be upgraded:
  linux-generic linux-headers-4.4.0-96 linux-headers-generic
  linux-image-generic
4 to upgrade, 4 to newly install, 0 to remove and 199 not to upgrade.
2 not fully installed or removed.
Need to get 78.7 MB of archives.
After this operation, 369 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-101-generic amd64 4.4.0-101.124 [21.9 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-101-generic amd64 4.4.0-101.124 [36.1 MB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-generic amd64 4.4.0.101.106 [1,782 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-generic amd64 4.4.0.101.106 [2,298 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-101 all 4.4.0-101.124 [9,916 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-101-generic amd64 4.4.0-101.124 [789 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-generic amd64 4.4.0.101.106 [2,270 B]
Get:8 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-96 all 4.4.0-96.119 [10.0 MB]
Fetched 78.7 MB in 39s (2,014 kB/s)                                            
Selecting previously unselected package linux-image-4.4.0-101-generic.
(Reading database ... 635937 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-101-generic_4.4.0-101.124_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
Done.
Unpacking linux-image-4.4.0-101-generic (4.4.0-101.124) ...
Selecting previously unselected package linux-image-extra-4.4.0-101-generic.
Preparing to unpack .../linux-image-extra-4.4.0-101-generic_4.4.0-101.124_amd64.deb ...
Unpacking linux-image-extra-4.4.0-101-generic (4.4.0-101.124) ...
Preparing to unpack .../linux-generic_4.4.0.101.106_amd64.deb ...
Unpacking linux-generic (4.4.0.101.106) over (4.4.0.96.101) ...
Preparing to unpack .../linux-image-generic_4.4.0.101.106_amd64.deb ...
Unpacking linux-image-generic (4.4.0.101.106) over (4.4.0.96.101) ...
Selecting previously unselected package linux-headers-4.4.0-101.
Preparing to unpack .../linux-headers-4.4.0-101_4.4.0-101.124_all.deb ...
Unpacking linux-headers-4.4.0-101 (4.4.0-101.124) ...
Selecting previously unselected package linux-headers-4.4.0-101-generic.
Preparing to unpack .../linux-headers-4.4.0-101-generic_4.4.0-101.124_amd64.deb ...
Unpacking linux-headers-4.4.0-101-generic (4.4.0-101.124) ...
Preparing to unpack .../linux-headers-generic_4.4.0.101.106_amd64.deb ...
Unpacking linux-headers-generic (4.4.0.101.106) over (4.4.0.93.98) ...
Preparing to unpack .../linux-headers-4.4.0-96_4.4.0-96.119_all.deb ...
Unpacking linux-headers-4.4.0-96 (4.4.0-96.119) over (4.4.0-96.119) ...
Setting up linux-image-4.4.0-101-generic (4.4.0-101.124) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-101-generic
Found initrd image: /boot/initrd.img-4.4.0-101-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-92-generic
Found initrd image: /boot/initrd.img-4.4.0-92-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-extra-4.4.0-101-generic (4.4.0-101.124) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-101-generic /boot/vmlinuz-4.4.0-101-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-101-generic
Found initrd image: /boot/initrd.img-4.4.0-101-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Found linux image: /boot/vmlinuz-4.4.0-93-generic
Found initrd image: /boot/initrd.img-4.4.0-93-generic
Found linux image: /boot/vmlinuz-4.4.0-92-generic
Found initrd image: /boot/initrd.img-4.4.0-92-generic
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-image-generic (4.4.0.101.106) ...
Setting up linux-headers-4.4.0-101 (4.4.0-101.124) ...
Setting up linux-headers-4.4.0-101-generic (4.4.0-101.124) ...
Setting up linux-headers-generic (4.4.0.101.106) ...
Setting up linux-generic (4.4.0.101.106) ...
Setting up linux-headers-4.4.0-96 (4.4.0-96.119) ...
nick@nick-Latitude-E5400:~$ 

```

Many thanks for the help - what does all this mean ?

---

### Post by Bashing-om on 2017-12-04
Raggylad; Well -


Looks fairly descent :)
> 
what does all this mean ?

1) There "was" an issue with the signing keys for google-earth and spotify .. that may or may not still exist after the updates completed.
2) You need to do some maintenance/cleanup as the package manager advises ( autoremove) .


Reboot the machine - 
Next in terminal run
```

sudo apt autoremove

```

then show us a new output of:
```

sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]see where then we stand
[/INDENT][/INDENT]

---

### Post by Raggylad on 2017-12-04
Bashing-om,

Here's the output of those two commands:

[https://paste.ubuntu.com/26114708/](https://paste.ubuntu.com/26114708/)

(Too much code for the forum to digest directly !)

---

### Post by Bashing-om on 2017-12-04
Raggylad; Well ..

Looks sane :)

Now what results:
```

sudo apt autoremove

```

Before we return to the signing key issues .

[INDENT][INDENT]one thing now at a time
[/INDENT][/INDENT]

---

### Post by Raggylad on 2017-12-04
That was easier !

```
sudo apt autoremove
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

```

---

### Post by Bashing-om on 2017-12-04
Raggylad; Hey hey ...

Looking great ..

Now what about those singing keys ?? Are they now fixed ? ( likely not) 
Do you want spotify and google-earth to remain on the system ? 
show a new:
```

sudo apt update
sudo apt upgrade

```

and we tell the system to get the new keys .

[INDENT][INDENT][INDENT]we can do that
[/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2017-12-04
Bashing-om,

Here's what we get:

```
sudo apt update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu xenial InRelease
Ign:3 http://dl.google.com/linux/earth/deb stable InRelease                    
Hit:4 http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial InRelease       
Hit:5 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Get:6 http://dl.google.com/linux/earth/deb stable Release [2,136 B]            
Get:7 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:8 http://repository.spotify.com stable InRelease [3,302 B]                 
Get:9 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:10 http://dl.google.com/linux/earth/deb stable Release.gpg [819 B]         
Get:11 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB] 
Err:10 http://dl.google.com/linux/earth/deb stable Release.gpg 
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551
Get:12 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [62.4 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [218 kB]
Get:15 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [62.2 kB]
Get:16 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [51.3 kB]
Get:17 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [85.1 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [185 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [262 kB]
Get:20 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:21 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:22 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [4,676 B]
Fetched 1,557 kB in 1s (806 kB/s)                                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/earth/deb stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551
W: Failed to fetch http://dl.google.com/linux/earth/deb/dists/stable/Release.gpg  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1397BC53640DB551
W: Some index files failed to download. They have been ignored, or old ones used instead.
nick@nick-Latitude-E5400:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
nick@nick-Latitude-E5400:~$ 

```

If possible, I would like to keep Spotify and Google-earth to remain on the system.  That being said, they aren't vital to my existence and I'd rather have a system in good order and live without them (if that is the only way to achieve nirvana) than have a ragged system and well geo-located music !

Many thanks for all your ongoing help.

---

### Post by Bashing-om on 2017-12-04
Raggylad; Ho Kay ..
Raggylad; Uh Huh .

Try:
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551

```

To deal with google-earth's signing key .

Now run again:
```

sudo apt update

```

[INDENT][INDENT]I expect
[INDENT][INDENT][INDENT]clean as a whistle
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Raggylad on 2017-12-04
Bashing-om,

Here's the output of those:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1397BC53640DB551
[sudo] password for nick: 
Executing: /tmp/tmp.75xBorrmec/gpg.1.sh --keyserver
keyserver.ubuntu.com
--recv-keys
1397BC53640DB551
gpg: requesting key 640DB551 from hkp server keyserver.ubuntu.com
gpg: key D38B4796: public key "Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
nick@nick-Latitude-E5400:~$ sudo apt update
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                     
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:4 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:5 http://security.ubuntu.com/ubuntu xenial-security InRelease              
Hit:6 http://ppa.launchpad.net/freecad-maintainers/freecad-stable/ubuntu xenial InRelease
Ign:7 http://dl.google.com/linux/earth/deb stable InRelease                    
Hit:8 http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu xenial InRelease       
Get:9 http://dl.google.com/linux/earth/deb stable Release [2,136 B]            
Hit:10 http://repository.spotify.com stable InRelease                   
Get:11 http://dl.google.com/linux/earth/deb stable Release.gpg [819 B]
Get:12 http://dl.google.com/linux/earth/deb stable/main amd64 Packages [805 B]
Get:13 http://dl.google.com/linux/earth/deb stable/main i386 Packages [800 B]
Fetched 2,424 B in 1s (1,973 B/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
nick@nick-Latitude-E5400:~$ 

```

---

### Post by Bashing-om on 2017-12-04
Raggylad; Mighty fine :)

Looks like we are all done here. 

[INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT]

---

### Post by Raggylad on 2017-12-04
Bashing-om,

Many thanks for all your help.
:p

---

### Post by Bashing-om on 2017-12-04
Raggylad; Welp;

Help is what we do .. pass it on along .

If this matter is now concluded to your satisfaction -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

and it is
[INDENT][INDENT][INDENT]up up and away
[/INDENT][/INDENT][/INDENT]

---

