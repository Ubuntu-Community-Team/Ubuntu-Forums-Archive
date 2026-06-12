---
title: "Package Operation Failed"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by kr4zy54n on 2012-01-10
Hi,
Whenever i install new package i get the following error.. its bcoz of the failed installation of kernel?
i have deleted that kernel package (linux-image-3.0.0-14-generic-pae)  & instaed upgraded to the 3.1.5 kernel. 


installArchives() failed: Selecting previously deselected package libcurl3. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 169025 files and directories currently installed.) 
Unpacking libcurl3 (from .../libcurl3_7.21.6-3ubuntu3_i386.deb) ... 
Selecting previously deselected package dkms. 
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ... 
Selecting previously deselected package libvncserver0. 
Unpacking libvncserver0 (from .../libvncserver0_0.9.7-3ubuntu1_i386.deb) ... 
Selecting previously deselected package linux-headers-3.0.0-14. 
Unpacking linux-headers-3.0.0-14 (from .../linux-headers-3.0.0-14_3.0.0-14.23_all.deb) ... 
Selecting previously deselected package linux-headers-3.0.0-14-generic. 
Unpacking linux-headers-3.0.0-14-generic (from .../linux-headers-3.0.0-14-generic_3.0.0-14.23_i386.deb) ... 
Selecting previously deselected package linux-headers-generic. 
Unpacking linux-headers-generic (from .../linux-headers-generic_3.0.0.14.16_i386.deb) ... 
Selecting previously deselected package virtualbox. 
Unpacking virtualbox (from .../virtualbox_4.1.2-dfsg-1ubuntu1_i386.deb) ... 
Selecting previously deselected package virtualbox-dkms. 
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.2-dfsg-1ubuntu1_all.deb) ... 
Selecting previously deselected package virtualbox-qt. 
Unpacking virtualbox-qt (from .../virtualbox-qt_4.1.2-dfsg-1ubuntu1_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for ureadahead ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for shared-mime-info ... 
Unknown media type in type 'all/all' 
Unknown media type in type 'all/allfiles' 
Unknown media type in type 'uri/mms' 
Unknown media type in type 'uri/mmst' 
Unknown media type in type 'uri/mmsu' 
Unknown media type in type 'uri/pnm' 
Unknown media type in type 'uri/rtspt' 
Unknown media type in type 'uri/rtspu' 
Unknown media type in type 'interface/x-winamp-skin' 
Processing triggers for menu ... 
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ... 
Internal Error: Could not find image (/boot/vmlinuz-3.0.0-14-generic) 
dpkg: error processing linux-image-3.0.0-14-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.0.0-14-generic-pae (3.0.0-14.23) ... 
Internal Error: Could not find image (/boot/vmlinuz-3.0.0-14-generic-pae) 
dpkg: error processing linux-image-3.0.0-14-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libcurl3 (7.21.6-3ubuntu3) ... 
Setting up dkms (2.2.0.2-1ubuntu4) ... 
Setting up libvncserver0 (0.9.7-3ubuntu1) ... 
Setting up linux-headers-3.0.0-14 (3.0.0-14.23) ... 
Setting up linux-headers-3.0.0-14-generic (3.0.0-14.23) ... 
Examining /etc/kernel/header_postinst.d. 
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic 
Setting up linux-headers-generic (3.0.0.14.16) ... 
Setting up virtualbox (4.1.2-dfsg-1ubuntu1) ... 
 * Stopping VirtualBox kernel modules 
   ...done. 
 * Starting VirtualBox kernel modules 
 * No suitable module for running kernel found 
   ...fail! 
invoke-rc.d: initscript virtualbox, action "restart" failed. 
Processing triggers for python-central ... 
Setting up virtualbox-dkms (4.1.2-dfsg-1ubuntu1) ... 
Loading new virtualbox-4.1.2 DKMS files... 
First Installation: checking all kernels... 
Building only for 3.1.5 
Building initial module for 3.1.5 
Done. 
 
vboxdrv: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/3.1.5/updates/dkms/ 
 
vboxnetadp.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/3.1.5/updates/dkms/ 
 
vboxnetflt.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/3.1.5/updates/dkms/ 
 
vboxpci.ko: 
Running module version sanity check. 
 - Original module 
   - No original module exists within this kernel 
 - Installation 
   - Installing to /lib/modules/3.1.5/updates/dkms/ 
 
depmod...................... 
 
DKMS: install Completed. 
 * Stopping VirtualBox kernel modules 
   ...done. 
 * Starting VirtualBox kernel modules 
   ...done. 
Setting up virtualbox-qt (4.1.2-dfsg-1ubuntu1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for menu ... 
Errors were encountered while processing: 
 linux-image-3.0.0-14-generic 
 linux-image-3.0.0-14-generic-pae 
Setting up linux-image-3.0.0-14-generic-pae (3.0.0-14.23) ... 
Internal Error: Could not find image (/boot/vmlinuz-3.0.0-14-generic-pae) 
dpkg: error processing linux-image-3.0.0-14-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ... 
Internal Error: Could not find image (/boot/vmlinuz-3.0.0-14-generic) 
dpkg: error processing linux-image-3.0.0-14-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Errors were encountered while processing:

---

### Post by Catharsis on 2012-01-13
Yeah, it's because you removed the 3.0.0-14 kernel so its headers are trying to install but can't because there's no 3.0.0-14 kernel.

Fix it with ```
sudo apt-get install -f
```

---

### Post by kr4zy54n on 2012-01-24
hi, 
Thnaks for replying but after executing the above command i get the following out put:

[HTML]# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgmp3-dev gnat-4.4-base libgmp-dev libtinfo-dev libgnat-4.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Internal Error: Could not find image (/boot/vmlinuz-3.0.0-14-generic)
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-14-generic-pae (3.0.0-14.23) ...
No apport report written because MaxReports is reached already
                                                              Internal Error: Could not find image (/boot/vmlinuz-3.0.0-14-generic-pae)
dpkg: error processing linux-image-3.0.0-14-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-14-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

---

