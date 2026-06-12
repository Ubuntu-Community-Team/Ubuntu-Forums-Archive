---
title: "Security update Failed &quot;Lunix kernel image for version 3.8.0&quot;"
date: 2013-06-01
forum: New to Ubuntu
---

### Post by bcarney on 2013-06-01
[INDENT]I just tried to install the recent (today) security update named "Lunix  kernel image for version 3.8.0 on 64 bit x86 SMP" part way through the  install it failed saying it was corrupt. I ended up removing the package  with synaptic package manager. After reboot I no longer have USB or  Network support. On the Grub menu I boot to an older version (On now)  and everything works fine. I ran software updater as a test and it is  still telling me I need this security update. How do I repair the boot process so everything works again? 

I forgot I am running ver 13.04 with KDE 4.0 (13.04 unity does not work with VMWorkstation 9)

I just discoverd the packages seem to be corrupt still. I ran apt-get -f install this is the out put.

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-extra-3.8.0-23-generic
The following NEW packages will be installed:
  linux-image-extra-3.8.0-23-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/30.8 MB of archives.
After this operation, 129 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 294809 files and directories currently installed.)
Unpacking linux-image-extra-3.8.0-23-generic (from .../linux-image-extra-3.8.0-23-generic_3.8.0-23.34_amd64.deb) ...
dpkg-deb (subprocess): decompressing archive member: internal bzip2 read error: 'DATA_ERROR'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/linux-image-extra-3.8.0-23-generic_3.8.0-23.34_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-23-generic /boot/vmlinuz-3.8.0-23-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-extra-3.8.0-23-generic_3.8.0-23.34_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Thanks in advance 
Brian                 
[/INDENT]

---

### Post by jonnyboysmithy on 2013-06-01
So it appears the package has been downloaded but the package is corrupt.
We can remove the corrupt package like this :```

sudo apt-get clean

```
Then we can install it again (since we removed it from cache it will be redownloaded):```

sudo apt-get install linux-image-extra-3.8.0-23-generic
```
Let us know how it goes :)

---

### Post by bcarney on 2013-06-01
THANKS! ):P

That fixed it! things boot up, although it seems to take much longer to boot, also longer to connect to WIFI. An for some reason the home drive GUI browser automaticly open everytime I sign in and get to the desktop (irratating is all). I am bootting from an SSD drive. Do you happen to know if there is any way to clean up\defrag the drive? I hear the comercial product does not work well or on SSD drives. 

Thanks for the help!

Brian

---

### Post by jonnyboysmithy on 2013-06-01
Ubuntu uses ext as the default filesystem. Its a journaling filesystem  meaning its smarter so that it places file in larger pieces of free  space on the harddrive to prevent fragmentation.
In other words it  doesn't just dump files to the first freely avaliable sector. This is  why it normally would never need defragmenting. Fragmentation can and  does still happen only that it is always kept to a minimum provided you  have enough free space. If you're disk is fuller than say 80-90% you'll  get much more fragmentation simply because there is nowhere else to put  the files.

Ok so the chances are you don't need to defragment your drive because you use a journaling filesystem unless your disk is full.
You  use a solid state drive. The whole point of defragmenting is to keep  files in one place so that the read/write head doesn't have to look in a  million places to read the file.
A SSD doesn't have a read write head, it can read anywhere on the drive instantaneously. Thus there is no need for defragmenting.

If you still want to see what your fragmentation level is run: 
 ```
sudo e4defrag -c /
``` It took ages on my computer for that to finish..

Here's a guide that shows you how to enable TRIM. TRIM basically lets your disk completely zero blocks that you delete making write operations much faster.
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)
The guide assumes you are using ext4 filesystem. Be sure thats actually what you are using.

---

