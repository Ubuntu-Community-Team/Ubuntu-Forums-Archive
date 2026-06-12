---
title: "Unable to download Libre Calc--get error messages"
date: 2015-02-02
forum: New to Ubuntu
---

### Post by Haven_McClure on 2015-02-02
Hello, I've been getting error messages when attempting to download Libre Calc.  This is what I got:  

InstallArchives() failed: Selecting previously unselected package libboost-iostreams1.55.0:amd64. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 326840 files and directories currently installed.) 
Preparing to unpack .../libboost-iostreams1.55.0_1.55.0+dfsg-1ubuntu3_amd64.deb ... 
Unpacking libboost-iostreams1.55.0:amd64 (1.55.0+dfsg-1ubuntu3) ... 
Selecting previously unselected package libreoffice-calc. 
Preparing to unpack .../libreoffice-calc_1%3a4.3.3-0ubuntu1_amd64.deb ... 
Unpacking libreoffice-calc (1:4.3.3-0ubuntu1) ... 
Processing triggers for mime-support (3.55ubuntu1.1) ... 
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ... 
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ... 
Processing triggers for man-db (2.7.0.2-2) ... 
Processing triggers for menu (2.1.47ubuntu1) ... 
Setting up linux-image-extra-3.16.0-30-generic (3.16.0-30.40) ... 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic 
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic 
 
gzip: stdout: No space left on device 
E: mkinitramfs failure cpio 141 gzip 1 
update-initramfs: failed for /boot/initrd.img-3.16.0-30-generic with 1. 
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1 
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-30-generic: 
 linux-signed-image-3.16.0-30-generic depends on linux-image-extra-3.16.0-30-generic (= 3.16.0-30.40); however: 
  Package linux-image-extra-3.16.0-30-generic is not configured yet. 
 
dpkg: error processing package linux-signed-image-3.16.0-30-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-signed-image-generic: 
 linux-signed-image-generic depends on linux-signed-image-3.16.0-30-generic; however: 
  Package linux-signed-image-3.16.0-30-generic is not configured yet. 
 
dpkg: error processing package linux-signed-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-signed-generic: 
 linux-signed-generic depends on linux-signed-image-generic (= 3.16.0.30.31); however: 
  Package linux-signed-image-generic is not configured yet. 
 
dpkg: error processing package linuxNo apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
-signed-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up libboost-iostreams1.55.0:amd64 (1.55.0+dfsg-1ubuntu3) ... 
Setting up libreoffice-calc (1:4.3.3-0ubuntu1) ... 
Processing triggers for libc-bin (2.19-10ubuntu2.2) ... 
Processing triggers for menu (2.1.47ubuntu1) ... 
Errors were encountered while processing: 
 linux-image-extra-3.16.0-30-generic 
 linux-signed-image-3.16.0-30-generic 
 linux-signed-image-generic 
 linux-signed-generic 
Setting up linux-image-extra-3.16.0-30-generic (3.16.0-30.40) ... 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-30-generic /boot/vmlinuz-3.16.0-30-generic 
update-initramfs: Generating /boot/initrd.img-3.16.0-30-generic 
 
gzip: stdout: No space left on device 
cpio: write error: Broken pipe 
E: mkinitramfs failure cpio 1 gzip 1 
update-initramfs: failed for /boot/initrd.img-3.16.0-30-generic with 1. 
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1 
dpkg: error processing package linux-image-extra-3.16.0-30-generic (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-signed-image-3.16.0-30-generic: 
 linux-signed-image-3.16.0-30-generic depends on linux-image-extra-3.16.0-30-generic (= 3.16.0-30.40); however: 
  Package linux-image-extra-3.16.0-30-generic is not configured yet. 
 
dpkg: error processing package linux-signed-image-3.16.0-30-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-signed-image-generic: 
 linux-signed-image-generic depends on linux-signed-image-3.16.0-30-generic; however: 
  Package linux-signed-image-3.16.0-30-generic is not configured yet. 
 
dpkg: error processing package linux-signed-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-signed-generic: 
 linux-signed-generic depends on linux-signed-image-generic (= 3.16.0.30.31); however: 
  Package linux-signed-image-generic is not configured yet. 
 
dpkg: error processing package linux-signed-generic (--configure): 
 dependency problems - leaving unconfigured 

I don't get where the "no space left on device" comes from as this is a brand new laptop with Ubuntu Studio 14.10 installed.

---

### Post by Bucky Ball on 2015-02-02
Where are you downloading it from? Install it from Synaptic Package Manager. Search for 'libreoffice-calc'. Install. Disregard if this is what you are already attempting. Let us know of any errors you get doing it that way. 

(PS: Please use [code] tags for terminal output. See the last link in my signature for how. Thanks. ;))

---

### Post by Haven_McClure on 2015-02-02
Thanks for your very quick reply and your guidance regarding code tags is duly noted.  

I downloaded from Ubuntu Software Center.  I did discover that I was able to open Libre Office Calc despite being told that the download failed.  Should I uninstall and reinstall from Synaptic Package Manager just to play it safe?

I've been getting error messages since updating some  packages related to xscreensaver in an attempt to update that app.  So far it seems to not have affected functionality, though I"m not entirely sure if that is indeed the case..  I wish I could remember which packages I updated, but I did okay the other updates that it told me it needed to update.  I have been reporting the error messages whenever the system has given me the opportunity to. 

Not sure if this is very helpful? ;- /

---

### Post by Bucky Ball on 2015-02-02
All good. SCentre/Synaptics installs from the same place so stick with what you have (wasn't sure if UStudio had Software Centre).

Perhaps try these commands, one after another one at a time, and report any and all errors.
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by Haven_McClure on 2015-02-02
after sudo-apt-get update
```

W: Failed to fetch http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/utopic/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mixxx/mixxx/ubuntu/dists/utopic/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Those were the only error messages I got--if they were even error messages in the first place.

One noteworthy note:  the Mixxx program was something I added after instaling 14.10.  As usual they had me install from terminal mode.  I followed their instructions but it gave me version 1.10.1 instead of their current version 1.11.1.

---

### Post by Bucky Ball on 2015-02-02
You have added that PPA manually during the instructions. Remove it (go to Sorftware & Updates and untick or completely remove) and install mixxx from the Software Centre or Synaptics. Best to look there first before dragging in third-party PPAs. ;)

This probably has nothing to do with your original issue, but best to get it out of the way. 

The version in the repos is 1.10.1, at least in 14.04 LTS. Might be different for 14.10. Have a look. 

PS: Just a note: You are aware that 14.10 has only nine months support? That means there's about six months left before you need to upgrade/reinstall. The LTS releases (12.04 LTS, 14.04 LTS) have five years (may be three for UStudio as it uses xfce4, not sure).

---

### Post by ptn107 on 2015-02-02
> gzip: stdout: No space left on device 
What's the output of
```
df -h
```

** You should try installing the LibreOffice deb from the actual website.

---

### Post by Bucky Ball on 2015-02-02
Better from the repos where it is fully supported, but your choice. 

Just a point: Do you have Openoffice installed? This causes conflicts. You can't have both. 

Please give the output of ptn107's command and we'll try figure out what's going on with the out of space error before anything else.

---

### Post by monkeybrain20122 on 2015-02-02
This has nothing to do with your original problem. But going to MIXXX's website I found this link [https://launchpad.net/~mixxx/+archive/ubuntu/mixxx](https://launchpad.net/~mixxx/+archive/ubuntu/mixxx)
It offers 1.11.0 for Trusty, maybe you can download the .deb and install it on Utopic (choose Trusty in filter then click View package details) The ppa you added apparently has been removed.[https://bugs.launchpad.net/mixxx/+bug/1398844](https://bugs.launchpad.net/mixxx/+bug/1398844)

P.S. I don't use Mixxx, just googling around.

---

