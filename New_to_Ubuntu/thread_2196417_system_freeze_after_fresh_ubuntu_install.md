---
title: "system freeze after fresh ubuntu install"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by antobbo on 2013-12-29
Hello guys, I have reinstalled ubuntu 12.04 on my dell xps 17.
I have installed it from a bootable USB. Now, the system freezes at random and well, the only alternative is to press the power button I am afraid.
I have updated the kernel ([http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23](http://askubuntu.com/questions/257617/how-can-i-upgrade-the-ubuntu-12-04-2-kernel-to-3-5-0-23)) thinking that this could have solved the problem but no joy.
I have no idea what's going on, can anybody give me a hand to diagnose and repair please?
thanks

---

### Post by 3grciii on 2013-12-29
I would start by diagnosing the hardware. In 30 years of supporting computers, I have never seen a healthy linux system freeze randomly (windows is another story). Some useful tools for this can be found on Hirens boot cd.
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
 I would begin by testing RAM with memtest 86+ and hdd with victoria, follow up with running video tests...

---

### Post by antobbo on 2013-12-29
hi thanks, but I think I might need a hand with all that if that's ok. I downloaded the zip file for memtest86 and in the instructions it says that:
> 1)Review the Makefile and adjust options as needed.
2) Type "make"
Where do I get the makefile from?
thanks

---

### Post by antobbo on 2013-12-29
ah hang on, I run the memtest from the grub menu where I select what operating system to run. the mem test is running now,I will post the results when it is finished

---

### Post by sandyd on 2013-12-29
Download from [http://memtest86.com/download.htm#free](http://memtest86.com/download.htm#free)
burn to CD or to USB, and boot from it, and memtest86 should run :)

---

### Post by antobbo on 2013-12-29
test run, no errors found (at the bottom it says pass complete no errors, even if it is running again now, I am not sure why)
[ATTACH=CONFIG]249004[/ATTACH]
What do you guys think I should do now?

---

### Post by mörgæs on 2013-12-29
Does it also freeze in a live boot of 13.10?

---

### Post by antobbo on 2013-12-29
I don't know I haven't tried 13.10 and to be honest I wouldn't want to, I'd rather fix this version if possible

---

### Post by jaxom98 on 2013-12-29
Hello antobbo, join the club.I have a similar problem from updating. The only difference is mine is down to about 1 minute to freeze.

---

### Post by antobbo on 2013-12-29
well surely there is got to be an explanation. When I first installed 12.04 a few years ago everything was ok. WHen I re-installed it today, this freeze business started. Now, 3grciii suggested a few tests. I have done the memetest and it seems clean. I am pretty confident that the HDD is ok so I would like to straight away test the video test, would the CPU/Video/Disk Performance Test 5.7 do at all? The problem is that I don't know how to build them for linux, those tests here [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd) have all executable files that I can't run in linux, does anybody know what to do?
thanks

---

### Post by antobbo on 2013-12-30
Ah, I have found some a testing tool under ubuntu, I thought I'd run the test and I don't seem to have found anything wrong, I am attaching the images of the restults:[ATTACH=CONFIG]249019[/ATTACH][ATTACH=CONFIG]249020[/ATTACH][ATTACH=CONFIG]249021[/ATTACH][ATTACH=CONFIG]249022[/ATTACH]
Also I was thinking that from memory the nvidia drives are known to cause issues in ubuntu, so would it be wise to perhaps disable them and try other drives, like xorg or something? If it is a good idea, could anybody assist me with that?
thanks

---

### Post by antobbo on 2013-12-30
Hello guys, I thought I'd post my log, it might help somebody to understand what's going on. I can see a lot of errors everywhere and I can see that the nvidia seems to have something to do with it
Hopefully somebody might be able to suggest something :-)?
thanks




```
antobbo@antobbo-Dell-System-XPS-L702X:~$ grep -rnE "error|ERROR" /var/log 2>/dev/null
/var/log/kern.log:722:Dec 29 16:39:14 antobbo-Dell-System-XPS-L702X kernel: [    7.413454] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:1619:Dec 29 16:40:07 antobbo-Dell-System-XPS-L702X kernel: [    8.928170] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:2453:Dec 29 16:51:23 antobbo-Dell-System-XPS-L702X kernel: [    7.600872] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:3470:Dec 29 17:11:28 antobbo-Dell-System-XPS-L702X kernel: [   28.638394] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:4375:Dec 29 17:13:42 antobbo-Dell-System-XPS-L702X kernel: [   12.772394] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:5249:Dec 29 17:28:20 antobbo-Dell-System-XPS-L702X kernel: [   11.063276] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:6179:Dec 29 17:31:52 antobbo-Dell-System-XPS-L702X kernel: [   10.912781] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:6306:Dec 29 17:34:18 antobbo-Dell-System-XPS-L702X kernel: [  160.002383] traps: software-center[2494] trap int3 ip:7fdbce70ef9b sp:7fff1a902670 error:0
/var/log/kern.log:7084:Dec 29 17:43:43 antobbo-Dell-System-XPS-L702X kernel: [   15.120570] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:7976:Dec 29 17:46:42 antobbo-Dell-System-XPS-L702X kernel: [    7.468056] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:8125:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388190] end_request: I/O error, dev sr0, sector 0
/var/log/kern.log:8126:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388197] Buffer I/O error on device sr0, logical block 0
/var/log/kern.log:8127:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388202] Buffer I/O error on device sr0, logical block 1
/var/log/kern.log:8128:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388206] Buffer I/O error on device sr0, logical block 2
/var/log/kern.log:8129:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388209] Buffer I/O error on device sr0, logical block 3
/var/log/kern.log:8130:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388213] Buffer I/O error on device sr0, logical block 4
/var/log/kern.log:8131:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388217] Buffer I/O error on device sr0, logical block 5
/var/log/kern.log:8132:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388220] Buffer I/O error on device sr0, logical block 6
/var/log/kern.log:8133:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388224] Buffer I/O error on device sr0, logical block 7
/var/log/kern.log:8134:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388232] Buffer I/O error on device sr0, logical block 8
/var/log/kern.log:8943:Dec 29 17:54:13 antobbo-Dell-System-XPS-L702X kernel: [   11.562481] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:9866:Dec 29 18:39:27 antobbo-Dell-System-XPS-L702X kernel: [   10.208997] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:10915:Dec 29 18:51:52 antobbo-Dell-System-XPS-L702X kernel: [   15.461632] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:12092:Dec 29 20:44:35 antobbo-Dell-System-XPS-L702X kernel: [   15.740307] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:13008:Dec 29 20:57:27 antobbo-Dell-System-XPS-L702X kernel: [   11.854408] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:13903:Dec 29 21:01:02 antobbo-Dell-System-XPS-L702X kernel: [    8.185985] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:14794:Dec 29 22:13:51 antobbo-Dell-System-XPS-L702X kernel: [    8.452900] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:15716:Dec 29 22:21:49 antobbo-Dell-System-XPS-L702X kernel: [   13.329697] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:16659:Dec 29 22:25:37 antobbo-Dell-System-XPS-L702X kernel: [   12.476871] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:17461:Dec 29 22:37:45 antobbo-Dell-System-XPS-L702X kernel: [    9.603001] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:18317:Dec 29 22:49:01 antobbo-Dell-System-XPS-L702X kernel: [    7.559301] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:19241:Dec 29 23:05:41 antobbo-Dell-System-XPS-L702X kernel: [   17.446110] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:20026:Dec 30 09:56:14 antobbo-Dell-System-XPS-L702X kernel: [    8.296344] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:20967:Dec 30 10:04:01 antobbo-Dell-System-XPS-L702X kernel: [   11.563273] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:21787:Dec 30 10:38:26 antobbo-Dell-System-XPS-L702X kernel: [   15.585651] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:22676:Dec 30 11:02:07 antobbo-Dell-System-XPS-L702X kernel: [    8.249649] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:25678:Dec 30 16:47:41 antobbo-Dell-System-XPS-L702X kernel: [    8.124060] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:26546:Dec 30 16:50:20 antobbo-Dell-System-XPS-L702X kernel: [    8.443870] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:27416:Dec 30 16:56:37 antobbo-Dell-System-XPS-L702X kernel: [    8.195137] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:28340:Dec 30 17:09:03 antobbo-Dell-System-XPS-L702X kernel: [   10.544791] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:29192:Dec 30 17:46:09 antobbo-Dell-System-XPS-L702X kernel: [   11.945128] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:30066:Dec 30 17:54:27 antobbo-Dell-System-XPS-L702X kernel: [   10.554734] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/Xorg.0.log:15:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/jockey.log:7:2013-12-29 16:41:40,804 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
/var/log/jockey.log:15:2013-12-29 16:41:40,871 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
/var/log/jockey.log:20:2013-12-29 16:41:40,874 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
/var/log/jockey.log:25:2013-12-29 16:41:40,907 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
/var/log/jockey.log:35:2013-12-29 16:41:41,471 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates
/var/log/jockey.log:40:2013-12-29 16:41:41,477 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
/var/log/jockey.log:45:2013-12-29 16:41:41,482 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
/var/log/jockey.log:50:2013-12-29 16:41:41,497 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
/var/log/jockey.log:55:2013-12-29 16:41:41,503 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
/var/log/jockey.log:60:2013-12-29 16:41:43,717 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
/var/log/jockey.log:65:2013-12-29 16:41:43,723 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
/var/log/jockey.log:70:2013-12-29 16:41:43,729 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
/var/log/jockey.log:78:2013-12-29 16:41:45,936 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
/var/log/jockey.log:83:2013-12-29 16:41:45,948 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
/var/log/jockey.log:92:2013-12-29 16:41:46,042 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
/var/log/jockey.log:98:2013-12-29 16:41:46,389 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12
/var/log/jockey.log:103:2013-12-29 16:41:46,440 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
/var/log/jockey.log:108:2013-12-29 16:41:46,459 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
/var/log/jockey.log:113:2013-12-29 16:41:46,508 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
/var/log/jockey.log:119:2013-12-29 16:41:48,949 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
/var/log/jockey.log:124:2013-12-29 16:41:48,967 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13
/var/log/jockey.log:130:2013-12-29 16:41:50,151 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
/var/log/jockey.log:252:2013-12-29 16:41:56,211 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
/var/log/jockey.log:262:2013-12-29 16:41:58,543 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates
/var/log/jockey.log:272:2013-12-29 16:41:58,612 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
/var/log/jockey.log:468:2013-12-29 16:42:56,546 DEBUG: dpkg: error: dpkg status database is locked by another process
/var/log/jockey.log:470:SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
/var/log/jockey.log:472:2013-12-29 16:42:56,546 ERROR: Package failed to install:
/var/log/jockey.log:473:dpkg: error: dpkg status database is locked by another process
/var/log/jockey.log:475:SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
/var/log/jockey.log:477:2013-12-29 16:42:56,686 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
/var/log/jockey.log:479:2013-12-29 16:42:56,697 ERROR: xorg:nvidia_319: get_alternative_by_name(nvidia-319) returned nothing
/var/log/jockey.log:508:2013-12-29 17:34:28,191 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
/var/log/jockey.log:516:2013-12-29 17:34:28,234 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
/var/log/jockey.log:521:2013-12-29 17:34:28,237 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
/var/log/jockey.log:526:2013-12-29 17:34:28,321 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
/var/log/jockey.log:536:2013-12-29 17:34:28,676 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates
/var/log/jockey.log:541:2013-12-29 17:34:28,682 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
/var/log/jockey.log:546:2013-12-29 17:34:28,687 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
/var/log/jockey.log:551:2013-12-29 17:34:28,701 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
/var/log/jockey.log:556:2013-12-29 17:34:28,707 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
/var/log/jockey.log:561:2013-12-29 17:34:30,686 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
/var/log/jockey.log:566:2013-12-29 17:34:30,692 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
/var/log/jockey.log:571:2013-12-29 17:34:30,697 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
/var/log/jockey.log:579:2013-12-29 17:34:32,691 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
/var/log/jockey.log:584:2013-12-29 17:34:32,696 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
/var/log/jockey.log:593:2013-12-29 17:34:32,784 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
/var/log/jockey.log:599:2013-12-29 17:34:33,034 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12
/var/log/jockey.log:604:2013-12-29 17:34:33,048 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
/var/log/jockey.log:609:2013-12-29 17:34:33,053 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
/var/log/jockey.log:614:2013-12-29 17:34:33,067 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
/var/log/jockey.log:620:2013-12-29 17:34:35,268 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
/var/log/jockey.log:625:2013-12-29 17:34:35,274 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13
/var/log/jockey.log:631:2013-12-29 17:34:36,270 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
/var/log/jockey.log:769:2013-12-29 17:34:41,730 WARNING: modinfo for module nvidia_319 failed: ERROR: modinfo: could not find module nvidia_319
/var/log/jockey.log:779:2013-12-29 17:34:43,784 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates
/var/log/jockey.log:789:2013-12-29 17:34:43,805 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
/var/log/jockey.log:1040:2013-12-30 10:59:54,596 WARNING: modinfo for module vmxnet failed: ERROR: modinfo: could not find module vmxnet
/var/log/jockey.log:1048:2013-12-30 10:59:54,697 WARNING: modinfo for module ath_pci failed: ERROR: modinfo: could not find module ath_pci
/var/log/jockey.log:1053:2013-12-30 10:59:54,708 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl
/var/log/jockey.log:1058:2013-12-30 10:59:54,830 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
/var/log/jockey.log:1068:2013-12-30 10:59:55,363 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates
/var/log/jockey.log:1073:2013-12-30 10:59:55,383 WARNING: modinfo for module nvidia_current_updates failed: ERROR: modinfo: could not find module nvidia_current_updates
/var/log/jockey.log:1078:2013-12-30 10:59:55,401 WARNING: modinfo for module nvidia_experimental_304 failed: ERROR: modinfo: could not find module nvidia_experimental_304
/var/log/jockey.log:1083:2013-12-30 10:59:55,452 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current
/var/log/jockey.log:1091:2013-12-30 10:59:57,738 WARNING: modinfo for module nvidia_173 failed: ERROR: modinfo: could not find module nvidia_173
/var/log/jockey.log:1096:2013-12-30 10:59:57,757 WARNING: modinfo for module nvidia_173_updates failed: ERROR: modinfo: could not find module nvidia_173_updates
/var/log/jockey.log:1101:2013-12-30 10:59:57,773 WARNING: modinfo for module nvidia_experimental_310 failed: ERROR: modinfo: could not find module nvidia_experimental_310
/var/log/jockey.log:1109:2013-12-30 10:59:59,997 WARNING: modinfo for module nvidia_96 failed: ERROR: modinfo: could not find module nvidia_96
/var/log/jockey.log:1114:2013-12-30 11:00:00,016 WARNING: modinfo for module nvidia_96_updates failed: ERROR: modinfo: could not find module nvidia_96_updates
/var/log/jockey.log:1123:2013-12-30 11:00:00,126 WARNING: modinfo for module omapdrm_pvr failed: ERROR: modinfo: could not find module omapdrm_pvr
/var/log/jockey.log:1129:2013-12-30 11:00:00,515 WARNING: modinfo for module fglrx_experimental_12 failed: ERROR: modinfo: could not find module fglrx_experimental_12
/var/log/jockey.log:1134:2013-12-30 11:00:00,565 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates
/var/log/jockey.log:1139:2013-12-30 11:00:00,584 WARNING: modinfo for module fglrx_experimental_9 failed: ERROR: modinfo: could not find module fglrx_experimental_9
/var/log/jockey.log:1144:2013-12-30 11:00:00,634 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
/var/log/jockey.log:1150:2013-12-30 11:00:03,066 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not find module fglrx
/var/log/jockey.log:1155:2013-12-30 11:00:03,081 WARNING: modinfo for module fglrx_experimental_13 failed: ERROR: modinfo: could not find module fglrx_experimental_13
/var/log/jockey.log:1161:2013-12-30 11:00:04,307 WARNING: modinfo for module cedarview_gfx failed: ERROR: modinfo: could not find module cedarview_gfx
/var/log/jockey.log:1306:2013-12-30 11:00:14,927 WARNING: modinfo for module nvidia_304_updates failed: ERROR: modinfo: could not find module nvidia_304_updates
/var/log/jockey.log:1316:2013-12-30 11:00:15,002 WARNING: modinfo for module nvidia_304 failed: ERROR: modinfo: could not find module nvidia_304
/var/log/Xorg.0.log.old:15:	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
/var/log/syslog:726:Dec 29 16:39:14 antobbo-Dell-System-XPS-L702X kernel: [    7.413454] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:929:Dec 29 16:39:18 antobbo-Dell-System-XPS-L702X NetworkManager[1009]: <error> [1388335158.859693] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:1833:Dec 29 16:40:07 antobbo-Dell-System-XPS-L702X kernel: [    8.928170] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:2005:Dec 29 16:40:11 antobbo-Dell-System-XPS-L702X NetworkManager[993]: <error> [1388335211.964732] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:3092:Dec 29 16:51:23 antobbo-Dell-System-XPS-L702X kernel: [    7.600872] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:3318:Dec 29 16:51:30 antobbo-Dell-System-XPS-L702X NetworkManager[970]: <error> [1388335890.727075] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:3388:Dec 29 16:51:36 antobbo-Dell-System-XPS-L702X NetworkManager[970]: <error> [1388335896.345128] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:3389:Dec 29 16:51:36 antobbo-Dell-System-XPS-L702X NetworkManager[970]: <error> [1388335896.345140] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:4399:Dec 29 17:11:28 antobbo-Dell-System-XPS-L702X kernel: [   28.638394] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:4538:Dec 29 17:11:34 antobbo-Dell-System-XPS-L702X NetworkManager[1020]: <error> [1388337094.812213] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:4625:Dec 29 17:11:39 antobbo-Dell-System-XPS-L702X NetworkManager[1020]: <error> [1388337099.939313] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:4626:Dec 29 17:11:39 antobbo-Dell-System-XPS-L702X NetworkManager[1020]: <error> [1388337099.939327] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:5529:Dec 29 17:13:42 antobbo-Dell-System-XPS-L702X kernel: [   12.772394] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:5680:Dec 29 17:13:47 antobbo-Dell-System-XPS-L702X NetworkManager[1076]: <error> [1388337227.977440] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:5744:Dec 29 17:13:53 antobbo-Dell-System-XPS-L702X NetworkManager[1076]: <error> [1388337233.164745] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:5745:Dec 29 17:13:53 antobbo-Dell-System-XPS-L702X NetworkManager[1076]: <error> [1388337233.164774] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:6679:Dec 29 17:28:20 antobbo-Dell-System-XPS-L702X kernel: [   11.063276] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:6903:Dec 29 17:28:25 antobbo-Dell-System-XPS-L702X NetworkManager[1017]: <error> [1388338105.285705] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:6969:Dec 29 17:28:30 antobbo-Dell-System-XPS-L702X NetworkManager[1017]: <error> [1388338110.258307] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:6970:Dec 29 17:28:30 antobbo-Dell-System-XPS-L702X NetworkManager[1017]: <error> [1388338110.258341] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:7847:Dec 29 17:31:52 antobbo-Dell-System-XPS-L702X kernel: [   10.912781] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:8065:Dec 29 17:31:57 antobbo-Dell-System-XPS-L702X NetworkManager[1015]: <error> [1388338317.330855] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:8137:Dec 29 17:32:02 antobbo-Dell-System-XPS-L702X NetworkManager[1015]: <error> [1388338322.543045] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:8138:Dec 29 17:32:02 antobbo-Dell-System-XPS-L702X NetworkManager[1015]: <error> [1388338322.543070] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:8218:Dec 29 17:34:18 antobbo-Dell-System-XPS-L702X kernel: [  160.002383] traps: software-center[2494] trap int3 ip:7fdbce70ef9b sp:7fff1a902670 error:0
/var/log/syslog:9007:Dec 29 17:43:43 antobbo-Dell-System-XPS-L702X kernel: [   15.120570] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:9214:Dec 29 17:43:49 antobbo-Dell-System-XPS-L702X NetworkManager[1019]: <error> [1388339029.293490] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:9300:Dec 29 17:43:54 antobbo-Dell-System-XPS-L702X NetworkManager[1019]: <error> [1388339034.597272] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:9301:Dec 29 17:43:54 antobbo-Dell-System-XPS-L702X NetworkManager[1019]: <error> [1388339034.597302] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:10240:Dec 29 17:46:42 antobbo-Dell-System-XPS-L702X kernel: [    7.468056] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:10454:Dec 29 17:46:47 antobbo-Dell-System-XPS-L702X NetworkManager[1008]: <error> [1388339207.404487] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:10544:Dec 29 17:46:53 antobbo-Dell-System-XPS-L702X NetworkManager[1008]: <error> [1388339213.220425] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:10545:Dec 29 17:46:53 antobbo-Dell-System-XPS-L702X NetworkManager[1008]: <error> [1388339213.220437] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:10633:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388190] end_request: I/O error, dev sr0, sector 0
/var/log/syslog:10634:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388197] Buffer I/O error on device sr0, logical block 0
/var/log/syslog:10635:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388202] Buffer I/O error on device sr0, logical block 1
/var/log/syslog:10636:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388206] Buffer I/O error on device sr0, logical block 2
/var/log/syslog:10637:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388209] Buffer I/O error on device sr0, logical block 3
/var/log/syslog:10638:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388213] Buffer I/O error on device sr0, logical block 4
/var/log/syslog:10639:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388217] Buffer I/O error on device sr0, logical block 5
/var/log/syslog:10640:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388220] Buffer I/O error on device sr0, logical block 6
/var/log/syslog:10641:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388224] Buffer I/O error on device sr0, logical block 7
/var/log/syslog:10642:Dec 29 17:49:32 antobbo-Dell-System-XPS-L702X kernel: [  180.388232] Buffer I/O error on device sr0, logical block 8
/var/log/syslog:11455:Dec 29 17:54:13 antobbo-Dell-System-XPS-L702X kernel: [   11.562481] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:11666:Dec 29 17:54:17 antobbo-Dell-System-XPS-L702X NetworkManager[1038]: <error> [1388339657.745318] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:11754:Dec 29 17:54:22 antobbo-Dell-System-XPS-L702X NetworkManager[1038]: <error> [1388339662.785735] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:11755:Dec 29 17:54:22 antobbo-Dell-System-XPS-L702X NetworkManager[1038]: <error> [1388339662.785758] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:12672:Dec 29 18:39:27 antobbo-Dell-System-XPS-L702X kernel: [   10.208997] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:12888:Dec 29 18:39:31 antobbo-Dell-System-XPS-L702X NetworkManager[1019]: <error> [1388342371.698106] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:12966:Dec 29 18:39:36 antobbo-Dell-System-XPS-L702X NetworkManager[1019]: <error> [1388342376.837158] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:12967:Dec 29 18:39:36 antobbo-Dell-System-XPS-L702X NetworkManager[1019]: <error> [1388342376.837175] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:13994:Dec 29 18:51:52 antobbo-Dell-System-XPS-L702X kernel: [   15.461632] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:14133:Dec 29 18:51:57 antobbo-Dell-System-XPS-L702X NetworkManager[1034]: <error> [1388343117.822054] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:14201:Dec 29 18:52:02 antobbo-Dell-System-XPS-L702X NetworkManager[1034]: <error> [1388343122.833291] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:14202:Dec 29 18:52:02 antobbo-Dell-System-XPS-L702X NetworkManager[1034]: <error> [1388343122.833313] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:14405:Dec 29 18:54:47 antobbo-Dell-System-XPS-L702X NetworkManager[1034]: <error> [1388343287.308713] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:14572:Dec 29 18:59:16 antobbo-Dell-System-XPS-L702X NetworkManager[1034]: <error> [1388343556.208658] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:14631:Dec 29 18:59:23 antobbo-Dell-System-XPS-L702X NetworkManager[1034]: <error> [1388343563.796491] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
/var/log/syslog:14647:Dec 29 18:59:25 antobbo-Dell-System-XPS-L702X NetworkManager[1034]: <error> [1388343565.23905] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:15763:Dec 29 20:44:35 antobbo-Dell-System-XPS-L702X kernel: [   15.740307] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:15984:Dec 29 20:44:40 antobbo-Dell-System-XPS-L702X NetworkManager[1015]: <error> [1388349880.106378] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:16060:Dec 29 20:44:45 antobbo-Dell-System-XPS-L702X NetworkManager[1015]: <error> [1388349885.174545] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:16061:Dec 29 20:44:45 antobbo-Dell-System-XPS-L702X NetworkManager[1015]: <error> [1388349885.174558] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:16924:Dec 29 20:57:27 antobbo-Dell-System-XPS-L702X kernel: [   11.854408] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:17140:Dec 29 20:57:32 antobbo-Dell-System-XPS-L702X NetworkManager[1020]: <error> [1388350652.561699] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:17221:Dec 29 20:57:37 antobbo-Dell-System-XPS-L702X NetworkManager[1020]: <error> [1388350657.614855] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:17222:Dec 29 20:57:37 antobbo-Dell-System-XPS-L702X NetworkManager[1020]: <error> [1388350657.614866] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:18065:Dec 29 21:01:02 antobbo-Dell-System-XPS-L702X kernel: [    8.185985] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:18281:Dec 29 21:01:07 antobbo-Dell-System-XPS-L702X NetworkManager[1018]: <error> [1388350867.448569] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:18365:Dec 29 21:01:13 antobbo-Dell-System-XPS-L702X NetworkManager[1018]: <error> [1388350873.400613] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:18366:Dec 29 21:01:13 antobbo-Dell-System-XPS-L702X NetworkManager[1018]: <error> [1388350873.400643] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:19175:Dec 29 22:13:51 antobbo-Dell-System-XPS-L702X kernel: [    8.452900] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:19453:Dec 29 22:14:29 antobbo-Dell-System-XPS-L702X NetworkManager[1003]: <error> [1388355269.230985] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:19516:Dec 29 22:14:34 antobbo-Dell-System-XPS-L702X NetworkManager[1003]: <error> [1388355274.512074] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:19517:Dec 29 22:14:34 antobbo-Dell-System-XPS-L702X NetworkManager[1003]: <error> [1388355274.512094] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:20338:Dec 29 22:21:49 antobbo-Dell-System-XPS-L702X kernel: [   13.329697] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:20557:Dec 29 22:21:55 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388355715.442061] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:20635:Dec 29 22:22:00 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388355720.629543] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:20636:Dec 29 22:22:00 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388355720.629582] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:20741:Dec 29 22:25:13 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388355913.712820] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:20742:Dec 29 22:25:13 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388355913.712836] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Disconnected from D-Bus (or argument error during call)
/var/log/syslog:21577:Dec 29 22:25:37 antobbo-Dell-System-XPS-L702X kernel: [   12.476871] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:21729:Dec 29 22:25:42 antobbo-Dell-System-XPS-L702X NetworkManager[1004]: <error> [1388355942.49962] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:21804:Dec 29 22:25:48 antobbo-Dell-System-XPS-L702X NetworkManager[1004]: <error> [1388355948.362863] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:21805:Dec 29 22:25:48 antobbo-Dell-System-XPS-L702X NetworkManager[1004]: <error> [1388355948.362882] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:21896:Dec 29 22:26:57 antobbo-Dell-System-XPS-L702X NetworkManager[1004]: <error> [1388356017.871368] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:21897:Dec 29 22:26:57 antobbo-Dell-System-XPS-L702X NetworkManager[1004]: <error> [1388356017.871932] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Disconnected from D-Bus (or argument error during call)
/var/log/syslog:22665:Dec 29 22:37:45 antobbo-Dell-System-XPS-L702X kernel: [    9.603001] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:22886:Dec 29 22:37:50 antobbo-Dell-System-XPS-L702X NetworkManager[976]: <error> [1388356670.615350] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:22966:Dec 29 22:37:56 antobbo-Dell-System-XPS-L702X NetworkManager[976]: <error> [1388356676.94956] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:22967:Dec 29 22:37:56 antobbo-Dell-System-XPS-L702X NetworkManager[976]: <error> [1388356676.94985] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:23765:Dec 29 22:49:01 antobbo-Dell-System-XPS-L702X kernel: [    7.559301] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:23978:Dec 29 22:49:06 antobbo-Dell-System-XPS-L702X NetworkManager[979]: <error> [1388357346.116650] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:24070:Dec 29 22:49:12 antobbo-Dell-System-XPS-L702X NetworkManager[979]: <error> [1388357352.90018] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:24071:Dec 29 22:49:12 antobbo-Dell-System-XPS-L702X NetworkManager[979]: <error> [1388357352.90030] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:24178:Dec 29 23:00:39 antobbo-Dell-System-XPS-L702X NetworkManager[979]: <error> [1388358039.378774] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:24179:Dec 29 23:00:39 antobbo-Dell-System-XPS-L702X NetworkManager[979]: <error> [1388358039.378791] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Disconnected from D-Bus (or argument error during call)
/var/log/syslog:24998:Dec 29 23:05:41 antobbo-Dell-System-XPS-L702X kernel: [   17.446110] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:25924:Dec 30 09:56:14 antobbo-Dell-System-XPS-L702X kernel: [    8.296344] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:27023:Dec 30 10:04:01 antobbo-Dell-System-XPS-L702X kernel: [   11.563273] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:27209:Dec 30 10:06:12 antobbo-Dell-System-XPS-L702X NetworkManager[1058]: <error> [1388397972.480962] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:27271:Dec 30 10:06:17 antobbo-Dell-System-XPS-L702X NetworkManager[1058]: <error> [1388397977.489298] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:27272:Dec 30 10:06:17 antobbo-Dell-System-XPS-L702X NetworkManager[1058]: <error> [1388397977.489352] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:28088:Dec 30 10:38:26 antobbo-Dell-System-XPS-L702X kernel: [   15.585651] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:28304:Dec 30 10:38:30 antobbo-Dell-System-XPS-L702X NetworkManager[972]: <error> [1388399910.373154] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:28380:Dec 30 10:38:35 antobbo-Dell-System-XPS-L702X NetworkManager[972]: <error> [1388399915.724786] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:28381:Dec 30 10:38:35 antobbo-Dell-System-XPS-L702X NetworkManager[972]: <error> [1388399915.724815] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:28484:Dec 30 10:39:13 antobbo-Dell-System-XPS-L702X NetworkManager[972]: <error> [1388399953.847454] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
/var/log/syslog:28527:Dec 30 10:40:12 antobbo-Dell-System-XPS-L702X NetworkManager[972]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
/var/log/syslog:28626:Dec 30 10:41:10 antobbo-Dell-System-XPS-L702X NetworkManager[972]: <error> [1388400070.967552] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:29374:Dec 30 11:02:07 antobbo-Dell-System-XPS-L702X kernel: [    8.249649] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:29614:Dec 30 11:02:13 antobbo-Dell-System-XPS-L702X NetworkManager[1000]: <error> [1388401333.385166] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:29713:Dec 30 11:02:21 antobbo-Dell-System-XPS-L702X NetworkManager[1000]: <error> [1388401341.713817] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:29714:Dec 30 11:02:21 antobbo-Dell-System-XPS-L702X NetworkManager[1000]: <error> [1388401341.713831] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:32938:Dec 30 16:47:41 antobbo-Dell-System-XPS-L702X kernel: [    8.124060] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:33178:Dec 30 16:47:47 antobbo-Dell-System-XPS-L702X NetworkManager[1004]: <error> [1388422067.615677] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:34018:Dec 30 16:50:20 antobbo-Dell-System-XPS-L702X kernel: [    8.443870] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:34261:Dec 30 16:50:26 antobbo-Dell-System-XPS-L702X NetworkManager[952]: <error> [1388422226.547396] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:34358:Dec 30 16:50:34 antobbo-Dell-System-XPS-L702X NetworkManager[952]: <error> [1388422234.142258] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:34359:Dec 30 16:50:34 antobbo-Dell-System-XPS-L702X NetworkManager[952]: <error> [1388422234.142280] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:35137:Dec 30 16:56:37 antobbo-Dell-System-XPS-L702X kernel: [    8.195137] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:35376:Dec 30 16:56:43 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388422603.739679] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:35473:Dec 30 16:56:51 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388422611.501004] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:35474:Dec 30 16:56:51 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388422611.501022] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:35583:Dec 30 17:08:38 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388423318.454535] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:35584:Dec 30 17:08:38 antobbo-Dell-System-XPS-L702X NetworkManager[1013]: <error> [1388423318.454547] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Disconnected from D-Bus (or argument error during call)
/var/log/syslog:36410:Dec 30 17:09:03 antobbo-Dell-System-XPS-L702X kernel: [   10.544791] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:36616:Dec 30 17:09:08 antobbo-Dell-System-XPS-L702X NetworkManager[971]: <error> [1388423348.235237] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:36712:Dec 30 17:09:16 antobbo-Dell-System-XPS-L702X NetworkManager[971]: <error> [1388423356.642390] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:36713:Dec 30 17:09:16 antobbo-Dell-System-XPS-L702X NetworkManager[971]: <error> [1388423356.642414] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:36821:Dec 30 17:45:44 antobbo-Dell-System-XPS-L702X NetworkManager[971]: <error> [1388425544.462247] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:36822:Dec 30 17:45:44 antobbo-Dell-System-XPS-L702X NetworkManager[971]: <error> [1388425544.462261] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Disconnected from D-Bus (or argument error during call)
/var/log/syslog:37603:Dec 30 17:46:09 antobbo-Dell-System-XPS-L702X kernel: [   11.945128] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:37849:Dec 30 17:46:15 antobbo-Dell-System-XPS-L702X NetworkManager[964]: <error> [1388425575.358755] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:37991:Dec 30 17:46:47 antobbo-Dell-System-XPS-L702X NetworkManager[964]: <error> [1388425607.110448] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:37992:Dec 30 17:46:47 antobbo-Dell-System-XPS-L702X NetworkManager[964]: <error> [1388425607.110469] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:38760:Dec 30 17:54:27 antobbo-Dell-System-XPS-L702X kernel: [   10.554734] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:39010:Dec 30 17:54:33 antobbo-Dell-System-XPS-L702X NetworkManager[967]: <error> [1388426073.230744] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:39109:Dec 30 17:54:41 antobbo-Dell-System-XPS-L702X NetworkManager[967]: <error> [1388426081.436609] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:39110:Dec 30 17:54:41 antobbo-Dell-System-XPS-L702X NetworkManager[967]: <error> [1388426081.436624] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Binary file /var/log/apport.log matches
/var/log/dmesg.0:731:[   11.945128] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
Binary file /var/log/auth.log matches
/var/log/dpkg.log:2592:2013-08-20 17:57:32 install libgpg-error0 <none> 1.10-2ubuntu1
/var/log/dpkg.log:2593:2013-08-20 17:57:32 status half-installed libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2594:2013-08-20 17:57:32 status unpacked libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:2595:2013-08-20 17:57:32 status unpacked libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:7880:2013-08-20 17:59:01 configure libgpg-error0 1.10-2ubuntu1 <none>
/var/log/dpkg.log:7881:2013-08-20 17:59:01 status unpacked libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:7882:2013-08-20 17:59:01 status half-configured libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:7883:2013-08-20 17:59:01 status installed libgpg-error0 1.10-2ubuntu1
/var/log/dpkg.log:17684:2013-12-29 17:03:24 install libgpg-error0:i386 <none> 1.10-2ubuntu1
/var/log/dpkg.log:17685:2013-12-29 17:03:24 status half-installed libgpg-error0:i386 1.10-2ubuntu1
/var/log/dpkg.log:17686:2013-12-29 17:03:24 status unpacked libgpg-error0:i386 1.10-2ubuntu1
/var/log/dpkg.log:17687:2013-12-29 17:03:25 status unpacked libgpg-error0:i386 1.10-2ubuntu1
Binary file /var/log/apt/term.log matches
Binary file /var/log/apt/history.log matches
/var/log/cups/access_log:21:localhost - - [29/Dec/2013:19:09:48 +0000] "POST / HTTP/1.1" 200 186 Renew-Subscription client-error-not-found
/var/log/bootstrap.log:464:update-rc.d: error: insserv rejected the script header
/var/log/dmesg:730:[   10.554734] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
antobbo@antobbo-Dell-System-XPS-L702X:~$ 



```

---

### Post by antobbo on 2013-12-30
right guys, I think I found out something...not sure how critical this is but it might help.I had 2 crashes in the last 20 minutes, one at about 21.24 (UK time) and another one at 21.30.
Now, I checked the log again and I found these entries at exactly 21.24 and 21.29:


```
/var/log/syslog:46093:Dec 30 21:24:17 antobbo-Dell-System-XPS-L702X kernel: [    8.316016] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:46301:Dec 30 21:24:22 antobbo-Dell-System-XPS-L702X NetworkManager[966]: <error> [1388438662.933509] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:46393:Dec 30 21:24:27 antobbo-Dell-System-XPS-L702X NetworkManager[966]: <error> [1388438667.900696] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:46394:Dec 30 21:24:27 antobbo-Dell-System-XPS-L702X NetworkManager[966]: <error> [1388438667.900713] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
/var/log/syslog:46512:Dec 30 21:29:10 antobbo-Dell-System-XPS-L702X NetworkManager[966]: <error> [1388438950.282745] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:46513:Dec 30 21:29:10 antobbo-Dell-System-XPS-L702X NetworkManager[966]: <error> [1388438950.282795] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Disconnected from D-Bus (or argument error during call)
/var/log/syslog:47299:Dec 30 21:29:33 antobbo-Dell-System-XPS-L702X kernel: [   10.989701] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
/var/log/syslog:47508:Dec 30 21:29:40 antobbo-Dell-System-XPS-L702X NetworkManager[969]: <error> [1388438980.219503] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 0)
/var/log/syslog:47604:Dec 30 21:29:45 antobbo-Dell-System-XPS-L702X NetworkManager[969]: <error> [1388438985.231152] [nm-dns-dnsmasq.c:393] update(): dnsmasq not available on the bus, can't update servers.
/var/log/syslog:47605:Dec 30 21:29:45 antobbo-Dell-System-XPS-L702X NetworkManager[969]: <error> [1388438985.231166] [nm-dns-dnsmasq.c:395] update(): dnsmasq owner not found on bus: Could not get owner of name 'uk.org.thekelleys.dnsmasq': no such name
Binary file /var/log/apport.log matches
```


So what does that tell us? 
One is what gregm pointed out before, an issue with the network card. I can't explain that, the laptop connects to the network. Is there any package I can download to fix this?
Dnsmasq I have reade it has something to do with the network as well. Can it be disabled - and if so is it a good idea?
ANd then more worrkingly there is this: EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro. I think this has something to do with the HD partition?!

---

