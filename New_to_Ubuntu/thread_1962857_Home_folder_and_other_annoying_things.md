---
title: "Home folder and other annoying things"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by marrs101 on 2012-04-21
Hi guys!

 I'm using the 10.04 for a couple of years now with wi-fi, without problem, but we got a new wireless router, and since than I can not connect to the internet. I upgraded to 12.04, wi-fi worked, but it's really slow on my eeePC, and I did not like it generally, so went back to 10.04.
 I found treads with the problem dating back 2010, but I couldn't fix it.

[http://ubuntuforums.org/showthread.php?t=1476007&highlight=wifi](http://ubuntuforums.org/showthread.php?t=1476007&highlight=wifi)

 I have problem with Step 2, I don't have the right to extract or copy anything to Home folder... 
 I know it sounds stupid, it feels like it, but I'm about to give up. Please help!

 Thanks!

---

### Post by papibe on 2012-04-21
Hi marrs101.

Could you post the result of this command?
```
ls -ld ~
```
Regards.

---

### Post by marrs101 on 2012-04-21
marrs@marrs101:~$ ls -ld ~
drwxr-xr-x 36 marrs marrs 4096 2012-04-21 22:07 /home/marrs
marrs@marrs101:~$

---

### Post by papibe on 2012-04-21
That looks OK. You have both write and read permissions to your home directory.

Could you tell us more detail about the file you downloaded and the error you are getting?

Regards.

---

### Post by marrs101 on 2012-04-21
To me it looks like the upgraded driver, this is the name of the file:

2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2

I have changed the name to .tar, by deleting the .bz2 as it was in the instructions, than I got this:

Extraction not performed

You don't have the right permissions to extract archives in the folder "file:///home"

---

### Post by papibe on 2012-04-21
Try putting back the name as it was and run this:
```
tar xvjf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
```
Tell us how it goes.
Regards.

---

### Post by marrs101 on 2012-04-21
marrs@marrs101:~$ tar xvjf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
tar: 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
marrs@marrs101:~$ 

To which folder I should copy the file?

---

### Post by papibe on 2012-04-21
> **marrs101 said:**
>  Cannot open: No such file or directory
Probably a typo, or is in the Download directory.

Try to use tab completion. after the command and options start writing the name of the file, and press tab so the shell complete the name.

Regards.

---

### Post by marrs101 on 2012-04-21
Well, it is in the Download...

---

### Post by papibe on 2012-04-21
Then, go to that directory:
```
cd Downloads
```
Make sure it is there by listing your files:
```
ls
```
And then unpack it there. Where is says <tab> press your 'tab' key.
```
tar xvjf 2010<tab>
```
Tell us how it goes.
Regards.

---

### Post by uRock on 2012-04-21
> **marrs101 said:**
> Well, it is in the Download...

Before running the tar command, you need to use ```
cd ~/Downloads
```to get you into the directory containing the file.

---

### Post by marrs101 on 2012-04-21
marrs@marrs101:~$ cd Downloads
marrs@marrs101:~/Downloads$ ls
2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
cnet2_comm_driver_gigabyte_mimobility_v_1_3_1_0_15_zip.exe
comm_driver_gigabyte_mimobility_v.1.3.1.0.15.zip
linux-image-2.6.32-21-generic_2.6.32-21.32rsalveti1_i386.deb
marrs@marrs101:~/Downloads$ ^C
marrs@marrs101:~/Downloads$ tar xvjf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2 
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
marrs@marrs101:~/Downloads$

---

### Post by jerome1232 on 2012-04-21
what does this return?

```
file 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
```

---

### Post by marrs101 on 2012-04-21
marrs@marrs101:~/Downloads$ file 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2: gzip compressed data, from Unix, last modified: Thu Jul 15 12:09:16 2010
marrs@marrs101:~/Downloads$

---

### Post by papibe on 2012-04-21
That's interesting. Did you rename the file?

Maybe they didn't name it properly.

Try this:
```
tar xvzf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
```
Note that I replaced the 'j' for a 'z' (z = gzip-ped; j = bzip2-zipped).

Regards.

---

### Post by marrs101 on 2012-04-21
hm...  


```
marrs@marrs101:~/Downloads$ tar xvzf 2010_07_16_RT2860_Linux_STA_v2.4.0.0.tar.bz2
2010_07_16_RT2860_Linux_STA_v2.4.0.0/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/mlme.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/wpa_cmm.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/dfs.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_cmd.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/os/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/os/rt_linux.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/iface/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/iface/rtmp_pci.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rt_config.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/br_ftph.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/client_wds_cmm.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/spectrum_def.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/vr_ikans.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_type.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/cfg80211extr.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/crypt_arc4.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_chip.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/crypt_sha2.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/chlist.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/spectrum.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_mcu.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/link_list.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_def.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/wpa.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/sta_cfg.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/dot11i_wpa.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/crypt_aes.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_dot11.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/ap.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/client_wds.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rt_ate.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/eeprom.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/crypt_hmac.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/chip/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/chip/rtmp_mac.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/chip/rt2860.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/chip/rtmp_phy.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/chip/mac_pci.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_os.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/action.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/wsc.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/oid.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_iface.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/cfg80211.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/crypt_md5.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/rtmp_timer.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/netif_block.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/include/firmware.h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/sync.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/rtmp_ckipmic.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/rtmp_data.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/connect.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/sta_cfg.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/dls.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/auth_rsp.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/auth.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/assoc.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/sanity.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta/wpa.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/crypt_sha2.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/rtmp_mcu.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/rt_ate.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_asic.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/rtmp_init.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/eeprom.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_cmd.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/mlme.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/ee_prom.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/crypt_md5.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_sync.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/client_wds.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_aes.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_sanity.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/crypt_arc4.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/rtmp_timer.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_mac_pci.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/netif_block.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_data.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_tkip.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/spectrum.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/crypt_aes.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/dfs.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/rt_channel.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/action.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_data_pci.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/ba_action.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_wep.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_profile.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/rt2860.bin
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_cfg.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/rtmp_init_inf.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_wpa.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/crypt_hmac.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/common/cmm_info.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/LICENSE ralink-firmware.txt
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt_pci_rbus.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/vr_ikans.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/br_ftph.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt_rbus_pci_util.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/vr_bdlt.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt_profile.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/config.mk
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/cfg80211.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile.6
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/sta_ioctl.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile.4
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt_linux.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/rt_main_dev.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/pci_main_dev.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/Makefile
2010_07_16_RT2860_Linux_STA_v2.4.0.0/README_STA
2010_07_16_RT2860_Linux_STA_v2.4.0.0/RT2860STACard.dat
2010_07_16_RT2860_Linux_STA_v2.4.0.0/sta_ate_iwpriv_usage.txt
2010_07_16_RT2860_Linux_STA_v2.4.0.0/iwpriv_usage.txt
2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/
2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/Makefile
2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h.c
2010_07_16_RT2860_Linux_STA_v2.4.0.0/RT2860STA.dat
marrs@marrs101:~/Downloads$
```

---

### Post by papibe on 2012-04-21
:)  There you go.

Regards.

---

### Post by marrs101 on 2012-04-21
So far so good... Now how do I extract it to the Home folder...

---

### Post by papibe on 2012-04-21
You already extract it on your Download directory. If you open nautilus (file manager), it should be a directory named '2010_07_16_RT2860_Linux_STA_v2.4.0.0' under Downloads.

If you really need to move it one level up to your home directory, you can do it very easily there on nautilus (using the GUI).

Hope that helps, and tell us how it goes.
Regards.

---

### Post by marrs101 on 2012-04-21
According to the instructions here under Step 2, I have to move it to Home

[http://ubuntuforums.org/showthread.php?t=1476007&highlight=wifi](http://ubuntuforums.org/showthread.php?t=1476007&highlight=wifi)

 Unless You have any other idea to fix this problem, I have to stick to this one... So I figure it out how to get Nautilus, and let's move forward. Thanks for all Your help, You guys did a great job!
 Let's call it a day, and I'm back to it tomorrow.
 Thanks again, and good night!

---

### Post by marrs101 on 2012-04-25
I think I managed to move it to my home folder, and I tried the whole process again, but no success...

---

### Post by marrs101 on 2012-04-25
I can not successfully perform the given commands.

sudo make
sudo make install
sudo ifconfig wlan0 down
sudo rmmod rt2860sta

I have checked the Synaptic Package Manager, and "gcc" is installed.
So I need further help please!
Thanks again!

---

### Post by jerome1232 on 2012-04-25
We need errors but I can think of a few things to check right off the bat.

make sure build-essential is installed

```
sudo apt-get install build-essential
```

Check the readme file for any instructions, I noticed from the output of your tar command that there is a readme file in there, have a look!

---

### Post by marrs101 on 2012-04-25
marrs@marrs101:~$ sudo apt-get install build-essential
[sudo] password for marrs: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-38 linux-headers-2.6.32-38-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch xz-utils
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc diffutils-doc
The following NEW packages will be installed
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
  xz-utils
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,572kB of archives.
After this operation, 24.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main libstdc++6-4.4-dev 4.4.3-4ubuntu5.1 [1,491kB]
Get: 2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main g++-4.4 4.4.3-4ubuntu5.1 [4,950kB]
Get: 3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main g++ 4:4.4.3-1ubuntu1 [1,442B]
Get: 4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main xz-utils 4.999.9beta+20091116-1 [228kB]
Get: 5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main patch 2.6-2ubuntu1 [123kB]
Get: 6 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main dpkg-dev 1.15.5.6ubuntu4.5 [654kB]
Get: 7 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main build-essential 11.4build1 [7,278B]
Get: 8 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main fakeroot 1.14.4-1ubuntu1 [118kB]
Fetched 7,572kB in 6s (1,083kB/s)                                              
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 177898 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.3-4ubuntu5.1_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.3-4ubuntu5.1_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package xz-utils.
Unpacking xz-utils (from .../xz-utils_4.999.9beta+20091116-1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.5.6ubuntu4.5_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4build1_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up xz-utils (4.999.9beta+20091116-1) ...
Setting up patch (2.6-2ubuntu1) ...
Setting up dpkg-dev (1.15.5.6ubuntu4.5) ...
Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libstdc++6-4.4-dev (4.4.3-4ubuntu5.1) ...
Setting up g++-4.4 (4.4.3-4ubuntu5.1) ...
Setting up g++ (4:4.4.3-1ubuntu1) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4build1) ...
marrs@marrs101:~$ 



now I'm reading the Readme.

---

### Post by jerome1232 on 2012-04-25
Now that build-essential is installed you should be able to install the drivers provided they don't need any additional packages (the readme should detail the packages they need if any)

---

### Post by marrs101 on 2012-04-25
I checked the Readme. ...not my level...

---

### Post by marrs101 on 2012-04-25
at Step 5, this is the problem:


marrs@marrs101:~$ sudo make
[sudo] password for marrs: 
make: *** No targets specified and no makefile found. Stop.
marrs@marrs101:~$

---

### Post by marrs101 on 2012-04-25
marrs@marrs101:~$ sudo make install
make: *** No rule to make target `install'. Stop.
marrs@marrs101

---

### Post by marrs101 on 2012-04-25
marrs@marrs101:~$ sudo ifconfig wlan0 down
wlan0: ERROR while getting interface flags: No such device
marrs@marrs101:~$

---

### Post by marrs101 on 2012-04-25
marrs@marrs101:~$ sudo rmmod rt2860sta
ERROR: Module rt2860sta does not exist in /proc/modules
marrs@marrs101:~$

---

### Post by Vaphell on 2012-04-25
```
marrs@marrs101:[COLOR="Red"]~[/COLOR]$ sudo make
```

this is your current location ($HOME that is) and i don't think you have extracted the code into your home dir. You should cd to the directory with the source code first. Make  is not going to automagically find the proper location.

usually things are compiled and installed with 3 commands
```
./configure
make
sudo make install
```

---

### Post by jerome1232 on 2012-04-25
reiterating, you need to run make inside the folder you extracted.

cd into the driver folder, use tab completion to make it easy

```
cd 2010*now hit tab*
make
make install
```

---

### Post by marrs101 on 2012-04-25
it was extracted to the /Download, than I moved it to my home folder.
marrs@marrs101:~$ cd 2010*
marrs@marrs101:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$

---

### Post by marrs101 on 2012-04-25
marrs@marrs101:~$ cd 2010*
marrs@marrs101:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ make
make -C tools
make[1]: Entering directory `/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/3.0.0-13-generic/build SUBDIRS=/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
make: *** /lib/modules/3.0.0-13-generic/build: No such file or directory. Stop.
make: *** [LINUX] Error 2
marrs@marrs101:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$

---

### Post by marrs101 on 2012-04-25
marrs@marrs101:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ make install
make -C /home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
rm -rf /etc/Wireless/RT2860STA
rm: cannot remove `/etc/Wireless/RT2860STA/RT2860STA.dat': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux'
make: *** [install] Error 2
marrs@marrs101:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$

---

### Post by jerome1232 on 2012-04-25
Please for the sake of readability, in the future post all output wrapped in code tags. To do so, go in advanced mode, then hihglight your output and press the # symbol.

> **marrs101 said:**
> marrs@marrs101:~$ cd 2010*
marrs@marrs101:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$ make
make -C tools
make[1]: Entering directory `/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools'
/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux/Makefile
make -C /lib/modules/3.0.0-13-generic/build SUBDIRS=/home/marrs/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux modules
[COLOR="Red"]make: *** /lib/modules/3.0.0-13-generic/build: No such file or directory.[/COLOR] Stop.
make: *** [LINUX] Error 2
marrs@marrs101:~/2010_07_16_RT2860_Linux_STA_v2.4.0.0$

I'm guessing that your missing a library. Searching the package manager I found a few possibilities that I believe would be good candidates, perhaps install [COLOR="RoyalBlue"]libsbuild-dev[/COLOR] and try again.

Did that readme file have a section about dependencies needed for building?

edit: Dont' try make install when you got errors from make, also make install must be run as root.

---

### Post by marrs101 on 2012-04-25
libsbuild-dev successfully installed.

#

---

### Post by marrs101 on 2012-04-25
the same error came back.

---

### Post by jerome1232 on 2012-04-25
Then it was the wrong dependency, check the readme for the dependencies. Usually it tells you what it needs, all I can do is do apt-cache search and keep guessing at what it wants.

---

### Post by marrs101 on 2012-04-25
I'm afraid You expecting too much... :-) I hoped for an easy solution, what even I can perform, but for me it looks way too complicated. I think we reached my limit. Maybe better find someone, who can actually do this on my pc. Not giving up, just annoyed by myself. Ok, I'm giving up... :-) I have no idea what "dependencies" are.

---

### Post by jerome1232 on 2012-04-25
It just means that your driver "depends" on certain programs being installed to build correctly. Normally a readme file (although poor documentation happens) will have a list of these programs that you need to have installed to build successfully. (Yours may not, I don't know)

Normally, when your installing with debian packages, or .debs. This is taken care of automatically, the package system handles all of this for you, but when building from source you have to depend on the documentation provided to you by the author, or your own guesses based on the errors being spewn at you.

---

### Post by marrs101 on 2012-04-25
Unfortunately, I could not find such list. :-( I have no further ideas...

---

### Post by marrs101 on 2012-04-30
Hi there!
 Still struggling.
 Maybe it was a silly idea, but I just tried that Bootinfo script thing. Well, I couldn't run it.
 Not happy to push You people, but what else I can do to fix this problem? Get professional help?

---

### Post by marrs101 on 2012-05-17
Well, the problem not solved, but the lack of interest makes me mark as "SOLVED" and close it down. :-(

---

