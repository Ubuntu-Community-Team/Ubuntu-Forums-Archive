---
title: "How to clean up temporary and obsolete files or packages?"
date: 2012-12-01
forum: New to Ubuntu
---

### Post by brodedra on 2012-12-01
I am a recent migrant to Ubuntu Linux 12.04 LTS. Recently, I have had upgraded my softwares (system update) after which, my system's performance has slowed down a bit from what I see while opening applications. 

In the past, I have had used Janitor to clean up my system but for some reason, I am not able to use it after upgrading my system (it repeatedly generated errors) and hence I had removed Janitor and installed BleachBit instead. Now, BleachBit reports me that following message upon scan:


Disk space to be recovered: 628.7MB
Files to be deleted: 898
Special operations: 31

However, it is not able to clean the system for some strange reason. I am getting error message shown below (only a portion of the entire error page):

[Errno 13] Permission denied: '/var/cache/apt/archives/libcupsimage2_1.5.3-0ubuntu4_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libasound2_1.0.25-1ubuntu10.1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/compizconfig-settings-manager_0.9.5.92-0ubuntu3_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libgnome-desktop-3-2_3.4.2-0ubuntu0.1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libgconf2.0-cil_2.24.2-1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/partial/desktop-base_6.0.7ubuntu1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/partial/gimp-data_2.6.12-1ubuntu1.1_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libgimp2.0_2.6.12-1ubuntu1.1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libvdpau1_0.4.1-3ubuntu1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/python-aptdaemon.gtk3widgets_0.43+bzr805-0ubuntu6_all.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/vim-tiny_2%3a7.3.429-2ubuntu2.1_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libecal-1.2-10_3.2.3-0ubuntu7_i386.deb'
[Errno 13] Permission denied: '/var/cache/apt/archives/libavcodec53_4%3a0.8.4-0ubuntu0.12.04.1_i386.deb'

and then, in the end I get message stating:

Disk space recovered: 2.2MB
Files deleted: 110
Special operations: 12
Errors: 763

Could someone please help me to get around with cleaning old and obsolete packages from my system so that I can reclaim free space and better performance. 

NOTE: I have had run BleachBit after restarting my system - meaning, there were no programs running and hence, no question of any open files/applications/handles which could prevent the cleaning process.

Thank you.

---

### Post by zombifier25 on 2012-12-01
If you want to clean those files (and other system files), you need to launch BleachBit as root. There's a menu entry for launching it as root, so just fire up Dash. Or else:
```
gksu bleachbit
```

---

### Post by brodedra on 2012-12-01
> **zombifier25 said:**
> If you want to clean those files (and other system files), you need to launch BleachBit as root. There's a menu entry for launching it as root, so just fire up Dash. Or else:
```
gksu bleachbit
```
You are a legend mate!

There we go...
Disk space recovered: 625MB
Files deleted: 761
Special operations: 3

Thanks a million!

---

