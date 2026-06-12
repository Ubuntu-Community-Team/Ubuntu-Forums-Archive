---
title: "genisoimage: Uh oh, I cant find the boot image 'isolinux.bin' !"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by 01100001 on 2008-05-18
Well, hi. I am trying to customize the main boot screen of Ubuntu 8.04, to change the splash.pcx with another one. So, I copy all the files to my HDD from the ubuntu CD and change the picture and then when I try to make it a bootable ISO I get the folowinr error :

```

[aleks@darkstar isolinux]$ mkisofs -o /tmp/test.iso -c boot.cat  -b isolinux.bin -f /home/aleks/Desktop/ISO/ubuntu/
Warning: -follow-links does not always work correctly; be careful.
I: -input-charset not specified, using utf-8 (detected in locale settings)
Already cached directory seen (/home/aleks/Desktop/ISO/ubuntu/ubuntu)
Already cached directory seen (/home/aleks/Desktop/ISO/ubuntu/dists/stable)
Using RED_U000.PNG;1 for  /home/aleks/Desktop/ISO/ubuntu/pics/red-upperleft.png (red-upperright.png)
Using BLUE_000.PNG;1 for  /home/aleks/Desktop/ISO/ubuntu/pics/blue-upperright.png (blue-upperleft.png)
Using RED_L000.PNG;1 for  /home/aleks/Desktop/ISO/ubuntu/pics/red-lowerleft.png (red-lowerright.png)
Using BLUE_001.PNG;1 for  /home/aleks/Desktop/ISO/ubuntu/pics/blue-lowerright.png (blue-lowerleft.png)
Using FILES000.MAN;1 for  /home/aleks/Desktop/ISO/ubuntu/casper/filesystem.manifest-desktop (filesystem.manifest)
Using OEM_C000.DEB;1 for  /home/aleks/Desktop/ISO/ubuntu/pool/main/o/oem-config/oem-config-gtk_1.37_i386.deb (oem-config_1.37_i386.deb)
Using NDISW000.DEB;1 for  /home/aleks/Desktop/ISO/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb (ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb)
Using LIBCA000.DEB;1 for  /home/aleks/Desktop/ISO/ubuntu/pool/main/i/isdnutils/libcapi20-3_3.12.20071127-0ubuntu1_i386.deb (libcapi20-dev_3.12.20071127-0ubuntu1_i386.deb)
Using ISDNU000.DEB;1 for  /home/aleks/Desktop/ISO/ubuntu/pool/main/i/isdnutils/isdnutils-xtools_3.12.20071127-0ubuntu1_i386.deb (isdnutils-base_3.12.20071127-0ubuntu1_i386.deb)
genisoimage: Uh oh, I cant find the boot image 'isolinux.bin' !
[aleks@darkstar isolinux]$ 


```

Now, I know for shure that isolinux.bin is in that directory:

```

[aleks@darkstar isolinux]$ pwd
/home/aleks/Desktop/ISO/ubuntu/isolinux
[aleks@darkstar isolinux]$ ls isolinux*
isolinux.bin  isolinux.cfg  isolinux.txt
[aleks@darkstar isolinux]$ 



```

What can be wrong ?
Thanks in advance.

---

