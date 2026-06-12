---
title: "dlink DWA-125 USB wireless adaptor help needed"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by thirdnipple on 2012-07-07
Hi everyone!

I installed ubuntu 12.04 for the first time yesterday and so for it's awesome.  However, I'm having problems installing my DLink DWA 125 wireless usb adapter.  

I'm a total beginner and I'm I tried to find instructions but I couldn't get them to work.  I downloaded the RT3070 driver but I can't seem to install it.  I'm super new to terminal and I would like to practice more but I need to get this working before I can experiment more with easir things :(

Any help would be really appreciated.  Detailed instructions would be even more appreciated.  Thanks :)

---

### Post by mapes12 on 2012-07-07
Now that you have the RT3070 driver you need to extract it then install it. There is a Youtube video that shows the Terminal commands how to do this here:-

[http://www.youtube.com/watch?v=ZkfQr72znUU](http://www.youtube.com/watch?v=ZkfQr72znUU)

EDIT: If you Google **ubuntu dlink DWA-125 USB** there are plenty of HowTo's. I've never had much luck with ndiswrapper.

---

### Post by kurt18947 on 2012-07-07
I hope someone more knowledgeable about Ralink chipsets checks in.  I avoid Ralink and Broadcom if possible, preferring RealTek or Atheros for their (better IMO) Linux support.   If no one else comes along, you could consider NDISwrapper.  I am not a fan of NDISwrapper, preferring native Linux drivers  but if no one better versed with Ralink comes along, NDISwrapper may be an option.    NDISwrapper is available in the software center or via Synaptic.

The thing with NDISWrapper is that you must use Win2K or WinXP drivers and there must be .inf and.sys files available.   The Dlink DWA-125 drivers on Dlink's site look like they qualify.  The 'drivers' folder has XP and XP64 .inf and .sys files in it which is what NDISwrapper needs.  You need to know your adapter version, (A or B) and Linux type, 32 bit or 64 bit.  If your Linux O.S. is 32 bit you need to use the Windows XP x86 drivers.  If your Linux O.S. is 64 bit you'd need to use the WinXP X64 drivers.  To determine 32 or 64 bit linux, you could check "system monitor."  The first page will say something like
> Release 12.04 (precise) **64-bit** Here's a link to Dlink's driver download page:
[http://dlink.com/us/en/home-solutions/support/product/dwa-125-wireless-n-nano-usb-adapter](http://dlink.com/us/en/home-solutions/support/product/dwa-125-wireless-n-nano-usb-adapter)

Good luck with you new adventures.

Edit:  I see Mapes12 posted a link while I was typing.  If you can install native drivers, that would be my preference.

---

### Post by thirdnipple on 2012-07-07
Thanks a lot for the help!  I'm really hoping this is going to work but I'm having trouble getting into the driver directory (I'm really new to ubuntu).  This is what I have typed in and I can't figure out why it's not working:


krzysztof@krzysztof-PC:~/Downloads$ ls
DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
DPO_RT3070_LinuxSTA_V2.3.0.4_20100604.tar.bz2
krzysztof@krzysztof-PC:~/Downloads$ cd DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/
bash: cd: DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/: Not a directory

I'm embarrassed to post this cause I know it's going to be something obvious, but this is just really new to me.  

Thanks :oops:

---

### Post by doctorbighands on 2012-07-07
> krzysztof@krzysztof-PC:~/Downloads$ cd DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/

Take away the slash at the very end, and you've got it. :)

Contrary to previous posters, I've had great success with ndiswrapper in the past. Just make sure you get the package called "ndisgtk", and you don't have to deal with the command line at all.

Good luck!

---

### Post by thirdnipple on 2012-07-07
I typed in:

krzysztof@krzysztof-PC:~/Downloads$ ls
DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
DPO_RT3070_LinuxSTA_V2.3.0.4_20100604.tar.bz2
krzysztof@krzysztof-PC:~/Downloads$ cd DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
bash: cd: DPO_RT3070_LinuxSTA_V2.3.0.4_20100604: Not a directory
krzysztof@krzysztof-PC:~/Downloads$ 

but it's still not working.  I'm starting to miss DOS (haha not really) but there must be something else I am doing wrong.

---

### Post by mapes12 on 2012-07-07
```
krzysztof@krzysztof-PC:~/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604 ls
```Can you type in this and post the output please.

---

### Post by thirdnipple on 2012-07-07
I can't because I can't seem to get into the DPO_RT3070_LinuxSTA_V2.3.0.4_20100604 directory.  I keep getting a message saying that it's not a directory when I try to get in.

```
krzysztof@krzysztof-PC:~/Downloads$ ls
DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
DPO_RT3070_LinuxSTA_V2.3.0.4_20100604.tar.bz2
krzysztof@krzysztof-PC:~/Downloads$ cd DPO_RT3070_LinuxSTA_V2.3.0.4_20100604
bash: cd: DPO_RT3070_LinuxSTA_V2.3.0.4_20100604: Not a directory
krzysztof@krzysztof-PC:~/Downloads$ 
```

---

### Post by mapes12 on 2012-07-07
I can see it's not a Directory. Hence the line I suggested to find the file so that we can work out how to extract the driver.

---

### Post by thirdnipple on 2012-07-07
ok, I see what the problem was.  I did not realize the folder had to be extracted twice.  I actually made it to the last step and have run into an issue:

```
root@krzysztof-PC:/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# cd os/linuxroot@krzysztof-PC:/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux# lscfg80211.c  Makefile.6     rt_linux.o     rt_profile.o   sta_ioctl.o
config.mk   modules.order  rt_main_dev.c  rt_usb.c       usb_main_dev.c
Makefile    rt_ate.c       rt_main_dev.o  rt_usb_util.c  vr_ikans.c
Makefile.4  rt_linux.c     rt_profile.c   sta_ioctl.c
root@krzysztof-PC:/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux# insmod rt3070sta.ko
insmod: can't read 'rt3070sta.ko': No such file or directory

```

in the video there are more files in this directory, including rt3070sta.ko

Have I missed a step.  Sorry to be such a noob.

---

### Post by mapes12 on 2012-07-07
I think you missed the "make"command:-

```
root@krzysztof-PC:/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# make
```

---

### Post by thirdnipple on 2012-07-07
I did run that command.  This is what happened:

```
root@krzysztof-PC:/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604# make
make -C tools
make[1]: Entering directory `/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/tools'
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/tools/bin2h
cp -f os/linux/Makefile.6 /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/Makefile
make -C /lib/modules/3.2.0-26-generic-pae/build SUBDIRS=/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-26-generic-pae'
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_md5.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_aes.o
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_aes.c: In function ‘WscEncryptData’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_aes.c:1522:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_aes.c:1592:1: warning: the frame size of 1360 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_aes.c:2265:1: warning: the frame size of 1096 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/mlme.o
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/mlme.c:4322:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined [-Wsequence-point]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/mlme.c:4683:1: warning: the frame size of 1720 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_wep.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/action.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_data.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/rtmp_init.o
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/rtmp_init.c: In function ‘NICInitAsicFromEEPROM’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/rtmp_init.c:2501:10: warning: unused variable ‘RFValue’ [-Wunused-variable]
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_aes.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_sync.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/eeprom.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_info.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/dfs.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/spectrum.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/rt_channel.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_profile.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_asic.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/assoc.o
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/assoc.c: In function ‘MlmeAssocReqAction’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/assoc.c:377:11: warning: unused variable ‘pInfo’ [-Wunused-variable]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/assoc.c:374:18: warning: unused variable ‘infoPos’ [-Wunused-variable]
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/auth.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sync.o
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sync.c:1079:1: warning: the frame size of 1260 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sync.c:773:1: warning: the frame size of 1260 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sync.c:1736:1: warning: the frame size of 1312 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sanity.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/connect.o
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/connect.c:351:1: warning: the frame size of 1744 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/wpa.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.o
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c:1481:3: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’ [-Wparentheses]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c:606:1: warning: the frame size of 1288 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c:1979:1: warning: the frame size of 1588 bytes is larger than 1024 bytes [-Wframe-larger-than=]
In file included from /usr/src/linux-headers-3.2.0-26-generic-pae/arch/x86/include/asm/uaccess.h:573:0,
                 from /usr/src/linux-headers-3.2.0-26-generic-pae/arch/x86/include/asm/sections.h:5,
                 from /usr/src/linux-headers-3.2.0-26-generic-pae/arch/x86/include/asm/hw_irq.h:26,
                 from include/linux/irq.h:357,
                 from /usr/src/linux-headers-3.2.0-26-generic-pae/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/include/os/rt_linux.h:49,
                 from /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/include/rtmp_os.h:42,
                 from /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/include/rt_config.h:67,
                 from /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c:40:
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c:3061:28:
/usr/src/linux-headers-3.2.0-26-generic-pae/arch/x86/include/asm/uaccess_32.h:211:26: warning: call to ‘copy_from_user_overflow’ declared with attribute warning: copy_from_user() buffer size is not provably correct [enabled by default]
In function ‘copy_from_user’,
    inlined from ‘RTMPSetInformation’ at /home/krzysztof/Downloads/DPO_RT3070_LinuxSTA_V2.3.0.4_20100604/os/linux/../../os/linux/sta_ioctl.c:3538:28:
/usr/src/linux-headers-3.2.0-26-generic-pae/arch/x86/include/asm/uaccess_32.h:211:
```

---

### Post by mapes12 on 2012-07-07
Restart your machine and try the wifi adapter again.

---

### Post by thirdnipple on 2012-07-07
I restarted but it's not working.

Should I run some of the commands again?

---

### Post by thirdnipple on 2012-07-07
Format C: ?

---

### Post by thirdnipple on 2012-07-08
I finally managed to get it to work!  I followed the instructions here:

[http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html](http://kaustav.codebinders.com/2011/10/install-dwa-125-wireless-driver-on-ubuntu-11-10.html)

Thank you very much for your help.  I'm going to have a beer and try and work through some easier things than this.  

you guys helped me learn a lot about terminal in 1 day.  thanks again :)

---

### Post by stoneguy on 2012-08-13
Looks like the kernel crowd finally got this one integrated. With a 3.2.6 kernel and a DWA-125A2, all I had to do was include rt2x00usb, rt2800usb, rt2x00lib, and rt2800lib in /etc/modules, and after the reboot, I had wireless.

No compilation required, thank goodness. I went down that road with two source bundles and never did get a clean make.

---

### Post by thirdnipple on 2012-08-14
How would I include those?

---

