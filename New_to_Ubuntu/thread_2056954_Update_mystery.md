---
title: "Update mystery"
date: 2012-09-12
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-09-12
The machine I have running Ubuntu is headless - no keyboard, mouse nor monitor. I ssh into it from either my PowerBook or iMac to keep an eye on temperatures.

I keep getting this upon first connecting:

```
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

6 packages can be updated.
0 updates are security updates.

```

Updating doesn't seem to work. I always get 6 updates mentioned upon reconnecting.

Any ideas why?

---

### Post by Ubunterrific on 2012-09-12
> **Penfold1971 said:**
> The machine I have running Ubuntu is headless - no keyboard, mouse nor monitor. I ssh into it from either my PowerBook or iMac to keep an eye on temperatures.

I keep getting this upon first connecting:

```
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-29-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

6 packages can be updated.
0 updates are security updates.

```Updating doesn't seem to work. I always get 6 updates mentioned upon reconnecting.

Any ideas why?


Kernel (and kernel related) updates, perhaps? Latest is 3.2.0.31.34 in the -proposed repository for precise?
Run 'sudo apt-get upgrade' and have a look what's new.
EDIT: What happens when you try to update, specifically?

---

### Post by snowpine on 2012-09-12
Please post the output of:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Penfold1971 on 2012-09-12
Thanks. (I don't do the 'sudo apt-get dist-upgrade' daily, just 'sudo apt-get upgrade.)

The outputs are, respectively, :

```
Ign http://security.ubuntu.com precise-security InRelease
Ign http://gb.archive.ubuntu.com precise InRelease
Ign http://gb.archive.ubuntu.com precise-updates InRelease           
Ign http://gb.archive.ubuntu.com precise-backports InRelease         
Ign http://extras.ubuntu.com precise InRelease 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://gb.archive.ubuntu.com precise Release.gpg
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]            
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]  
Get:4 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]       
Hit http://extras.ubuntu.com precise Release                                   
Hit http://gb.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://extras.ubuntu.com precise/main Sources        
Hit http://gb.archive.ubuntu.com precise Release         
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Get:5 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:6 http://security.ubuntu.com precise-security/main Sources [42.8 kB]
Hit http://gb.archive.ubuntu.com precise-backports Release                     
Get:7 http://security.ubuntu.com precise-security/restricted Sources [1,950 B] 
Get:8 http://security.ubuntu.com precise-security/universe Sources [13.5 kB]   
Get:9 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B] 
Get:10 http://security.ubuntu.com precise-security/main amd64 Packages [161 kB]
Hit http://gb.archive.ubuntu.com precise/main Sources                          
Hit http://gb.archive.ubuntu.com precise/restricted Sources                    
Hit http://gb.archive.ubuntu.com precise/universe Sources 
Hit http://gb.archive.ubuntu.com precise/multiverse Sources
Hit http://gb.archive.ubuntu.com precise/main amd64 Packages
Hit http://gb.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise/universe amd64 Packages
Hit http://gb.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com precise/main i386 Packages                    
Hit http://gb.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://gb.archive.ubuntu.com precise/universe i386 Packages                
Hit http://gb.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:11 http://gb.archive.ubuntu.com precise-updates/main Sources [163 kB]      
Get:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:13 http://security.ubuntu.com precise-security/universe amd64 Packages [43.8 kB]
Get:14 http://gb.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:15 http://gb.archive.ubuntu.com precise-updates/universe Sources [50.8 kB] 
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Get:16 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,180 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [165 kB] 
Get:18 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [4,241 B]
Get:19 http://gb.archive.ubuntu.com precise-updates/main amd64 Packages [382 kB]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [44.0 kB]
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Get:23 http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages [6,755 B]
Get:24 http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages [129 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en      
Get:25 http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:26 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [387 kB]
Get:27 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:28 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [129 kB]
Get:29 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [9,672 B]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/main Sources
Hit http://gb.archive.ubuntu.com precise-backports/restricted Sources
Hit http://gb.archive.ubuntu.com precise-backports/universe Sources
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://gb.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 1,865 kB in 3s (578 kB/s)
Reading package lists... Done
```

and

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed
  linux-headers-3.2.0-30 linux-headers-3.2.0-30-generic
  linux-image-3.2.0-30-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 51.2 MB of archives.
After this operation, 217 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-30-generic amd64 3.2.0-30.48 [38.5 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic amd64 3.2.0.30.32 [1,714 B]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic amd64 3.2.0.30.32 [2,594 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-30 all 3.2.0-30.48 [11.7 MB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-30-generic amd64 3.2.0-30.48 [990 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic amd64 3.2.0.30.32 [2,596 B]
Fetched 51.2 MB in 1min 2s (823 kB/s)                                          
Selecting previously unselected package linux-image-3.2.0-30-generic.
(Reading database ... 224151 files and directories currently installed.)
Unpacking linux-image-3.2.0-30-generic (from .../linux-image-3.2.0-30-generic_3.2.0-30.48_amd64.deb) ...
Done.
Preparing to replace linux-generic 3.2.0.29.31 (using .../linux-generic_3.2.0.30.32_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 3.2.0.29.31 (using .../linux-image-generic_3.2.0.30.32_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously unselected package linux-headers-3.2.0-30.
Unpacking linux-headers-3.2.0-30 (from .../linux-headers-3.2.0-30_3.2.0-30.48_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-30-generic.
Unpacking linux-headers-3.2.0-30-generic (from .../linux-headers-3.2.0-30-generic_3.2.0-30.48_amd64.deb) ...
Preparing to replace linux-headers-generic 3.2.0.29.31 (using .../linux-headers-generic_3.2.0.30.32_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Setting up linux-image-3.2.0-30-generic (3.2.0-30.48) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (3.2.0.30.32) ...
Setting up linux-generic (3.2.0.30.32) ...
Setting up linux-headers-3.2.0-30 (3.2.0-30.48) ...
Setting up linux-headers-3.2.0-30-generic (3.2.0-30.48) ...
Setting up linux-headers-generic (3.2.0.30.32) ...
```

---

### Post by Penfold1971 on 2012-09-12
Actually, that seems to have done it. I was prompted to restart, so I did 'sudo reboot'.

When I ssh-ed back into it, the output was:

```
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-30-generic x86_64)

 * Documentation:  https://help.ubuntu.com/
```

Can you explain what that was all about, please?

---

### Post by snowpine on 2012-09-12
In a nutshell, "dist-upgrade" is more thorough than plain "upgrade" which will never install new packages (such as new kernels, which are new packages rather than upgrades to the existing kernel package).

---

### Post by Penfold1971 on 2012-09-12
OK! :D

So would you recommend that I use 'sudo apt-get dist-upgrade' instead of 'sudo apt-get upgrade' from now on?

---

### Post by snowpine on 2012-09-12
"dist-upgrade" is my own personal practice, yes. If there is an argument for using "upgrade" instead, it is not known to me.

---

### Post by Penfold1971 on 2012-09-12
Then I'll use the dist-upgrade version from now on.

One final question: What is your recommendation for using/not using 'sudo apt-get autoremove' ? 
As I understand it, that cleans away any old packages that are made redundant. Am I right?

---

### Post by snowpine on 2012-09-12
I do not use "autoremove" personally because I have plenty of GB's free space on my hard drive.

---

### Post by Penfold1971 on 2012-09-12
OK.

Thanks for all your help here. Problem solved, plus something new learned. :D

---

