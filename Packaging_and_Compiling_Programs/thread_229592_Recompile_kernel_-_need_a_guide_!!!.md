---
title: "Recompile kernel - need a guide !!!"
date: 2006-08-04
forum: Packaging and Compiling Programs
---

### Post by mintyfresh on 2006-08-04
hey there.

I have Ubuntu 6.06 amd64 server with kernel 2.6.15-23-amd64-server

I need to recompile the kernel so that the FPS or Hz is higher because I am running high tickrate gameservers on the server. I am told that I should need it at 1000Hz or something.

I have already tried to compile a newer kernel and failed. 2.6.17

Basically, if anyone can help me by writing a short step-by-step guide on how to achieve what I need, it'd be much appreciated.

*fingers crossed*

---

### Post by mintyfresh on 2006-08-04
I was told to run make menuconfig by someone and this happens..

root@cursed:/usr/src/linux-2.6.17# make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  SHIPPED scripts/kconfig/zconf.tab.c
  SHIPPED scripts/kconfig/lex.zconf.c
  SHIPPED scripts/kconfig/zconf.hash.c
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:31:20: error: curses.h: No such file or direct       ory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:128: error: syntax error before âuse_colorsâ
scripts/kconfig/lxdialog/dialog.h:128: warning: type defaults to âintâ in declar       ation of âuse_colorsâ
scripts/kconfig/lxdialog/dialog.h:128: warning: data definition has no type or s       torage class
scripts/kconfig/lxdialog/dialog.h:129: error: syntax error before âuse_shadowâ
scripts/kconfig/lxdialog/dialog.h:129: warning: type defaults to âintâ in declar       ation of âuse_shadowâ
scripts/kconfig/lxdialog/dialog.h:129: warning: data definition has no type or s       torage class
scripts/kconfig/lxdialog/dialog.h:131: error: syntax error before âattributesâ
scripts/kconfig/lxdialog/dialog.h:131: warning: type defaults to âintâ in declar       ation of âattributesâ
scripts/kconfig/lxdialog/dialog.h:131: warning: data definition has no type or s       torage class
scripts/kconfig/lxdialog/dialog.h:143: error: syntax error before â*â token
scripts/kconfig/lxdialog/dialog.h:143: warning: function declaration isnât a pro       totype
scripts/kconfig/lxdialog/dialog.h:146: error: syntax error before â*â token
scripts/kconfig/lxdialog/dialog.h:146: warning: function declaration isnât a pro       totype
scripts/kconfig/lxdialog/dialog.h:147: error: syntax error before â*â token
scripts/kconfig/lxdialog/dialog.h:147: warning: function declaration isnât a pro       totype
scripts/kconfig/lxdialog/dialog.h:148: error: syntax error before â*â token
scripts/kconfig/lxdialog/dialog.h:148: warning: function declaration isnât a pro       totype
scripts/kconfig/lxdialog/dialog.h:149: error: syntax error before â*â token
scripts/kconfig/lxdialog/dialog.h:150: warning: function declaration isnât a pro       totype
scripts/kconfig/lxdialog/dialog.h:151: error: syntax error before â*â token
scripts/kconfig/lxdialog/dialog.h:151: warning: function declaration isnât a pro       totype
scripts/kconfig/lxdialog/checklist.c:31: error: syntax error before â*â token
scripts/kconfig/lxdialog/checklist.c:33: warning: function declaration isnât a p       rototype
scripts/kconfig/lxdialog/checklist.c: In function âprint_itemâ:
scripts/kconfig/lxdialog/checklist.c:37: warning: implicit declaration of functi       on âwattrsetâ
scripts/kconfig/lxdialog/checklist.c:37: error: âwinâ undeclared (first use in t       his function)
scripts/kconfig/lxdialog/checklist.c:37: error: (Each undeclared identifier is r       eported only once
scripts/kconfig/lxdialog/checklist.c:37: error: for each function it appears in.       )
scripts/kconfig/lxdialog/checklist.c:38: warning: implicit declaration of functi       on âwmoveâ
scripts/kconfig/lxdialog/checklist.c:38: error: âchoiceâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c:40: warning: implicit declaration of functi       on âwaddchâ
scripts/kconfig/lxdialog/checklist.c:43: error: âselectedâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:44: warning: implicit declaration of functi       on âwprintwâ
scripts/kconfig/lxdialog/checklist.c:44: error: âstatusâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c:47: warning: implicit declaration of functi       on âmvwaddchâ
scripts/kconfig/lxdialog/checklist.c:47: error: âitemâ undeclared (first use in        this function)
scripts/kconfig/lxdialog/checklist.c:49: warning: implicit declaration of functi       on âwaddstrâ
scripts/kconfig/lxdialog/checklist.c:52: warning: implicit declaration of functi       on âwrefreshâ
scripts/kconfig/lxdialog/checklist.c: At top level:
scripts/kconfig/lxdialog/checklist.c:59: error: syntax error before â*â token
scripts/kconfig/lxdialog/checklist.c:61: warning: function declaration isnât a p       rototype
scripts/kconfig/lxdialog/checklist.c: In function âprint_arrowsâ:
scripts/kconfig/lxdialog/checklist.c:62: error: âwinâ undeclared (first use in t       his function)
scripts/kconfig/lxdialog/checklist.c:62: error: âyâ undeclared (first use in thi       s function)
scripts/kconfig/lxdialog/checklist.c:62: error: âxâ undeclared (first use in thi       s function)
scripts/kconfig/lxdialog/checklist.c:64: error: âscrollâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c:76: error: âheightâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c:79: error: âitem_noâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:79: error: âchoiceâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c: At top level:
scripts/kconfig/lxdialog/checklist.c:95: error: syntax error before â*â token
scripts/kconfig/lxdialog/checklist.c:96: warning: function declaration isnât a p       rototype
scripts/kconfig/lxdialog/checklist.c: In function âprint_buttonsâ:
scripts/kconfig/lxdialog/checklist.c:97: error: âwidthâ undeclared (first use in        this function)
scripts/kconfig/lxdialog/checklist.c:98: error: âheightâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c:100: error: âdialogâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:100: error: âselectedâ undeclared (first us       e in this function)
scripts/kconfig/lxdialog/checklist.c: In function âdialog_checklistâ:
scripts/kconfig/lxdialog/checklist.c:117: error: âWINDOWâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: âdialogâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:117: error: âlistâ undeclared (first use in        this function)
scripts/kconfig/lxdialog/checklist.c:117: warning: left-hand operand of comma ex       pression has no effect
scripts/kconfig/lxdialog/checklist.c:117: warning: statement with no effect
scripts/kconfig/lxdialog/checklist.c:121: warning: implicit declaration of funct       ion âendwinâ
scripts/kconfig/lxdialog/checklist.c:122: warning: implicit declaration of funct       ion âfprintfâ
scripts/kconfig/lxdialog/checklist.c:122: warning: incompatible implicit declara       tion of built-in function âfprintfâ
scripts/kconfig/lxdialog/checklist.c:122: error: âstderrâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:140: error: âCOLSâ undeclared (first use in        this function)
scripts/kconfig/lxdialog/checklist.c:141: error: âLINESâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c:143: error: âstdscrâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:145: warning: implicit declaration of funct       ion ânewwinâ
scripts/kconfig/lxdialog/checklist.c:146: warning: implicit declaration of funct       ion âkeypadâ
scripts/kconfig/lxdialog/checklist.c:146: error: âTRUEâ undeclared (first use in        this function)
scripts/kconfig/lxdialog/checklist.c:166: warning: implicit declaration of funct       ion âsubwinâ
scripts/kconfig/lxdialog/checklist.c:199: warning: implicit declaration of funct       ion âwnoutrefreshâ
scripts/kconfig/lxdialog/checklist.c:201: warning: implicit declaration of funct       ion âdoupdateâ
scripts/kconfig/lxdialog/checklist.c:204: warning: implicit declaration of funct       ion âwgetchâ
scripts/kconfig/lxdialog/checklist.c:211: error: âKEY_UPâ undeclared (first use        in this function)
scripts/kconfig/lxdialog/checklist.c:211: error: âKEY_DOWNâ undeclared (first us       e in this function)
scripts/kconfig/lxdialog/checklist.c:221: error: âFALSEâ undeclared (first use i       n this function)
scripts/kconfig/lxdialog/checklist.c:222: warning: implicit declaration of funct       ion âscrollokâ
scripts/kconfig/lxdialog/checklist.c:223: warning: implicit declaration of funct       ion âwscrlâ
scripts/kconfig/lxdialog/checklist.c:282: warning: incompatible implicit declara       tion of built-in function âfprintfâ
scripts/kconfig/lxdialog/checklist.c:283: warning: implicit declaration of funct       ion âdelwinâ
scripts/kconfig/lxdialog/checklist.c:287: error: âKEY_LEFTâ undeclared (first us       e in this function)
scripts/kconfig/lxdialog/checklist.c:288: error: âKEY_RIGHTâ undeclared (first u       se in this function)
make[2]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make[1]: *** [menuconfig] Error 2
make: *** [menuconfig] Error 2

---

### Post by 23meg on 2006-08-04
[edited out; see post #6]

---

### Post by recursv on 2006-08-04
By the looks of that error message, you are missing the ncurses library I think. I could be well wrong though. That library is only used for displaying a pretty menu for setting the config options and can be avoided using the old config options in your current kernel.

As I was chatting to you earlier, I thought I would add to this thread - for any one else who can contribute - that you have followed the guide on [https://wiki.kubuntu.org/KernelCustomBuild]("https://wiki.kubuntu.org/KernelCustomBuild")

As you were able to download the source code and patch it for the amd64 chip, the next step should be to ```
make oldconfig
``` which should generate the config used in the current kernel version (which from our discussion, and for the benefit of others, is 2.6.15-amd64 ). That should ask a few questions relating to the configuration you wish. Most of the default answers should be ok for your needs. Just make sure you watch out for the question about your cpu timing and select the 1000hz option. 
Once that finishes, you should be able to build the kernel.
This can be done by typing :
```
make bzImage
make modules
make modules_install
make install
```

That will compile the kernel and the kernel modules and install them for you. The next step is to setup the boot loader. This is the dodgy part as you have to trust that no mistakes have been made :)

Ubuntu uses grub, which I have no experience with as I have always used lilo. (I am a slackware fan)
A two second google returns a red hat guide to configuring grub [http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-custom-kernel-bootloader.html]("http://www.redhat.com/docs/manuals/linux/RHL-7.3-Manual/custom-guide/s1-custom-kernel-bootloader.html")
But I don't know how relevant that is and you should probably look for a ubuntu guide instead. 

You want to configure grub so that it boots the new kernel. This is where the danger comes in. If the boot fails, I understand you have no physical access to the machine so it will be a game to get someone to boot the old kernel version for you. 

Ok, thats my 2 cents for the moment. Its late and all. Best of luck and I will check back here to see how you are getting on tomorrow. Hopefully someone a little more helpfull comes along.

ps: As an after thought, make sure you get / patch the kernel for the amd64 architecture.

---

### Post by recursv on 2006-08-04
> **23meg said:**
> [http://www.ubuntuforums.org/showthread.php?t=229592](http://www.ubuntuforums.org/showthread.php?t=229592)

But, that is this thread ???

---

### Post by 23meg on 2006-08-04
> **recursv said:**
> But, that is this thread ???
Apologies, that was a late night typo. I meant this one:

[http://www.ubuntuforums.org/showthread.php?t=85064](http://www.ubuntuforums.org/showthread.php?t=85064)

---

### Post by recursv on 2006-08-05
Good thread. Easy to follow. Cheers

---

### Post by mintyfresh on 2006-08-05
this is as far up as my putty output went

"
/boot/config-2.6.15-23-amd64-server:1449:warning: trying to assign nonexistent symbol PRISM2_USB
/boot/config-2.6.15-23-amd64-server:1450:warning: trying to assign nonexistent symbol PRISM2_PCI
/boot/config-2.6.15-23-amd64-server:1451:warning: trying to assign nonexistent symbol PRISM2_PLX
/boot/config-2.6.15-23-amd64-server:1452:warning: trying to assign nonexistent symbol PRISM2_CS
/boot/config-2.6.15-23-amd64-server:1453:warning: trying to assign nonexistent symbol NET_ACX
/boot/config-2.6.15-23-amd64-server:1454:warning: trying to assign nonexistent symbol NET_ACX_PCI
/boot/config-2.6.15-23-amd64-server:1455:warning: trying to assign nonexistent symbol NET_ACX_USB
/boot/config-2.6.15-23-amd64-server:1463:warning: trying to assign nonexistent symbol PRISM54_SOFTMAC
/boot/config-2.6.15-23-amd64-server:1464:warning: trying to assign nonexistent symbol NET_RT2600
/boot/config-2.6.15-23-amd64-server:1465:warning: trying to assign nonexistent symbol NET_RT2500
/boot/config-2.6.15-23-amd64-server:1466:warning: trying to assign nonexistent symbol NET_RT2400
/boot/config-2.6.15-23-amd64-server:1467:warning: trying to assign nonexistent symbol NET_RTL818X
/boot/config-2.6.15-23-amd64-server:1468:warning: trying to assign nonexistent symbol NET_RTL8187
/boot/config-2.6.15-23-amd64-server:1469:warning: trying to assign nonexistent symbol IPW3945
/boot/config-2.6.15-23-amd64-server:1470:warning: trying to assign nonexistent symbol IPW3945_DEBUG
/boot/config-2.6.15-23-amd64-server:1471:warning: trying to assign nonexistent symbol IPW3945_MONITOR
/boot/config-2.6.15-23-amd64-server:1472:warning: trying to assign nonexistent symbol NET_MRV8K
/boot/config-2.6.15-23-amd64-server:1514:warning: trying to assign nonexistent symbol VENDOR_SANGOMA
/boot/config-2.6.15-23-amd64-server:1575:warning: trying to assign nonexistent symbol NDISWRAPPER
/boot/config-2.6.15-23-amd64-server:1712:warning: trying to assign nonexistent symbol MISDN_DRV
/boot/config-2.6.15-23-amd64-server:1713:warning: trying to assign nonexistent symbol MISDN_MEMDEBUG
/boot/config-2.6.15-23-amd64-server:1714:warning: trying to assign nonexistent symbol MISDN_AVM_FRITZ
/boot/config-2.6.15-23-amd64-server:1715:warning: trying to assign nonexistent symbol MISDN_HFCPCI
/boot/config-2.6.15-23-amd64-server:1716:warning: trying to assign nonexistent symbol MISDN_HFCMULTI
/boot/config-2.6.15-23-amd64-server:1717:warning: trying to assign nonexistent symbol MISDN_HFCUSB
/boot/config-2.6.15-23-amd64-server:1718:warning: trying to assign nonexistent symbol MISDN_SPEEDFAX
/boot/config-2.6.15-23-amd64-server:1719:warning: trying to assign nonexistent symbol MISDN_W6692
/boot/config-2.6.15-23-amd64-server:1720:warning: trying to assign nonexistent symbol MISDN_DSP
/boot/config-2.6.15-23-amd64-server:1794:warning: trying to assign nonexistent symbol INPUT_ACERHK
/boot/config-2.6.15-23-amd64-server:1819:warning: trying to assign nonexistent symbol ECC
/boot/config-2.6.15-23-amd64-server:1847:warning: trying to assign nonexistent symbol SERIAL_8250_ACPI
/boot/config-2.6.15-23-amd64-server:2043:warning: trying to assign nonexistent symbol SENSORS_RTC8564
/boot/config-2.6.15-23-amd64-server:2045:warning: trying to assign nonexistent symbol RTC_X1205_I2C
/boot/config-2.6.15-23-amd64-server:2055:warning: trying to assign nonexistent symbol W1_MATROX
/boot/config-2.6.15-23-amd64-server:2056:warning: trying to assign nonexistent symbol W1_DS9490
/boot/config-2.6.15-23-amd64-server:2057:warning: trying to assign nonexistent symbol W1_DS9490_BRIDGE
/boot/config-2.6.15-23-amd64-server:2058:warning: trying to assign nonexistent symbol W1_THERM
/boot/config-2.6.15-23-amd64-server:2059:warning: trying to assign nonexistent symbol W1_SMEM
/boot/config-2.6.15-23-amd64-server:2061:warning: trying to assign nonexistent symbol W1_DS2433_CRC
/boot/config-2.6.15-23-amd64-server:2109:warning: trying to assign nonexistent symbol AVERATEC_5100P
/boot/config-2.6.15-23-amd64-server:2110:warning: trying to assign nonexistent symbol PACKARDBELL_E5
/boot/config-2.6.15-23-amd64-server:2162:warning: trying to assign nonexistent symbol VIDEO_AUDIO_DECODER
/boot/config-2.6.15-23-amd64-server:2163:warning: trying to assign nonexistent symbol VIDEO_DECODER
/boot/config-2.6.15-23-amd64-server:2245:warning: trying to assign nonexistent symbol DVB_TDA80XX
/boot/config-2.6.15-23-amd64-server:2267:warning: trying to assign nonexistent symbol DVB_ATMEL_AT76C651
/boot/config-2.6.15-23-amd64-server:2275:warning: trying to assign nonexistent symbol DVB_NXT2002
/boot/config-2.6.15-23-amd64-server:2288:warning: trying to assign nonexistent symbol DXR3
/boot/config-2.6.15-23-amd64-server:2289:warning: trying to assign nonexistent symbol EM8300
/boot/config-2.6.15-23-amd64-server:2290:warning: trying to assign nonexistent symbol EM8300_LOOPBACK
/boot/config-2.6.15-23-amd64-server:2291:warning: trying to assign nonexistent symbol EM8300_UCODETIMEOUT
/boot/config-2.6.15-23-amd64-server:2292:warning: trying to assign nonexistent symbol EM8300_DICOMFIX
/boot/config-2.6.15-23-amd64-server:2293:warning: trying to assign nonexistent symbol EM8300_DICOMCTRL
/boot/config-2.6.15-23-amd64-server:2294:warning: trying to assign nonexistent symbol EM8300_DICOMPAL
/boot/config-2.6.15-23-amd64-server:2295:warning: trying to assign nonexistent symbol ADV717X
/boot/config-2.6.15-23-amd64-server:2296:warning: trying to assign nonexistent symbol ADV717X_SWAP
/boot/config-2.6.15-23-amd64-server:2297:warning: trying to assign nonexistent symbol ADV717X_PIXELPORT16BIT
/boot/config-2.6.15-23-amd64-server:2298:warning: trying to assign nonexistent symbol ADV717X_PIXELPORTPAL
/boot/config-2.6.15-23-amd64-server:2299:warning: trying to assign nonexistent symbol BT865
/boot/config-2.6.15-23-amd64-server:2325:warning: symbol value 'm' invalid for FB_VESA
/boot/config-2.6.15-23-amd64-server:2342:warning: trying to assign nonexistent symbol FB_RADEON_OLD
/boot/config-2.6.15-23-amd64-server:2350:warning: trying to assign nonexistent symbol FB_ATY_XL_INIT
/boot/config-2.6.15-23-amd64-server:2369:warning: trying to assign nonexistent symbol FB_IMAC
/boot/config-2.6.15-23-amd64-server:2418:warning: trying to assign nonexistent symbol SND_GENERIC_DRIVER
/boot/config-2.6.15-23-amd64-server:2495:warning: trying to assign nonexistent symbol BT_ALSA
/boot/config-2.6.15-23-amd64-server:2501:warning: trying to assign nonexistent symbol OBSOLETE_OSS_DRIVER
/boot/config-2.6.15-23-amd64-server:2569:warning: trying to assign nonexistent symbol OBSOLETE_OSS_USB_DRIVER
/boot/config-2.6.15-23-amd64-server:2609:warning: trying to assign nonexistent symbol USB_MTOUCH
/boot/config-2.6.15-23-amd64-server:2610:warning: trying to assign nonexistent symbol USB_ITMTOUCH
/boot/config-2.6.15-23-amd64-server:2611:warning: trying to assign nonexistent symbol USB_EGALAX
/boot/config-2.6.15-23-amd64-server:2618:warning: trying to assign nonexistent symbol USB_SYNAPTICS
/boot/config-2.6.15-23-amd64-server:2619:warning: trying to assign nonexistent symbol USB_CPADDEV
/boot/config-2.6.15-23-amd64-server:2640:warning: trying to assign nonexistent symbol USB_QC
/boot/config-2.6.15-23-amd64-server:2641:warning: trying to assign nonexistent symbol USB_SPCA5XX
/boot/config-2.6.15-23-amd64-server:2642:warning: trying to assign nonexistent symbol USB_PODXTPRO
/boot/config-2.6.15-23-amd64-server:2644:warning: trying to assign nonexistent symbol USB_OV511_DECOMP
/boot/config-2.6.15-23-amd64-server:2645:warning: trying to assign nonexistent symbol USB_OV518_DECOMP
/boot/config-2.6.15-23-amd64-server:2669:warning: trying to assign nonexistent symbol USB_EAGLE
/boot/config-2.6.15-23-amd64-server:2670:warning: trying to assign nonexistent symbol USB_ZD1211
/boot/config-2.6.15-23-amd64-server:2671:warning: trying to assign nonexistent symbol USB_ATMEL
/boot/config-2.6.15-23-amd64-server:2672:warning: trying to assign nonexistent symbol USB_RT2570
/boot/config-2.6.15-23-amd64-server:2887:warning: trying to assign nonexistent symbol RELAYFS_FS
/boot/config-2.6.15-23-amd64-server:2896:warning: trying to assign nonexistent symbol ASFS_FS
/boot/config-2.6.15-23-amd64-server:2897:warning: trying to assign nonexistent symbol ASFS_DEFAULT_CODEPAGE
/boot/config-2.6.15-23-amd64-server:2898:warning: trying to assign nonexistent symbol ASFS_RW
/boot/config-2.6.15-23-amd64-server:2917:warning: trying to assign nonexistent symbol SQUASHFS
/boot/config-2.6.15-23-amd64-server:2918:warning: trying to assign nonexistent symbol SQUASHFS_1_0_COMPATIBILITY
/boot/config-2.6.15-23-amd64-server:2919:warning: trying to assign nonexistent symbol SQUASHFS_2_0_COMPATIBILITY
/boot/config-2.6.15-23-amd64-server:2927:warning: trying to assign nonexistent symbol UNION_FS
/boot/config-2.6.15-23-amd64-server:2974:warning: trying to assign nonexistent symbol GFS_FS
/boot/config-2.6.15-23-amd64-server:2975:warning: trying to assign nonexistent symbol GFS_FS_LOCK_HARNESS
/boot/config-2.6.15-23-amd64-server:2976:warning: trying to assign nonexistent symbol GFS_FS_LOCK_NOLOCK
/boot/config-2.6.15-23-amd64-server:2977:warning: trying to assign nonexistent symbol GFS_FS_LOCK_DLM
/boot/config-2.6.15-23-amd64-server:2978:warning: trying to assign nonexistent symbol GFS_FS_LOCK_GULM
/boot/config-2.6.15-23-amd64-server:3076:warning: trying to assign nonexistent symbol INIT_DEBUG
/boot/config-2.6.15-23-amd64-server:3088:warning: trying to assign nonexistent symbol SECURITY_REALTIME
/boot/config-2.6.15-23-amd64-server:3151:warning: trying to assign nonexistent symbol CLUSTER
/boot/config-2.6.15-23-amd64-server:3152:warning: trying to assign nonexistent symbol CLUSTER_DLM
/boot/config-2.6.15-23-amd64-server:3153:warning: trying to assign nonexistent symbol CLUSTER_DLM_PROCLOCKS
*
* Linux Kernel Configuration
*
*
* Code maturity level options
*
Prompt for development and/or incomplete code/drivers (EXPERIMENTAL) [Y/n/?] y
*
* General setup
*
Local version - append to kernel release (LOCALVERSION) []
Automatically append version information to the version string (LOCALVERSION_AUTO) [N/y/?] n
Support for paging of anonymous memory (swap) (SWAP) [Y/n/?] y
System V IPC (SYSVIPC) [Y/n/?] y
POSIX Message Queues (POSIX_MQUEUE) [Y/n/?] y
BSD Process Accounting (BSD_PROCESS_ACCT) [Y/n/?] y
  BSD Process Accounting version 3 file format (BSD_PROCESS_ACCT_V3) [Y/n/?] y
Sysctl support (SYSCTL) [Y/n/?] y
Auditing support (AUDIT) [Y/n/?] y
  Enable system-call auditing support (AUDITSYSCALL) [N/y/?] n
Kernel .config support (IKCONFIG) [N/y/?] n
Cpuset support (CPUSETS) [N/y/?] n
Kernel->user space relay support (formerly relayfs) (RELAY) [N/y/?] (NEW) make[1]: *** [oldconfig] Interrupt
make: *** [oldconfig] Interrupt
"

---

### Post by mintyfresh on 2006-08-05
And there wasn't an option for the CPU timing.

---

### Post by mintyfresh on 2006-08-05
I got further this time, after using apt-get in that guys guide.

But it skipped past the step of selecting the CPU timer, it auto-selected it!

kernel crash dumps (EXPERIMENTAL) (CRASH_DUMP) [N/y/?] (NEW) n
Enable seccomp to safely compute untrusted bytecode (SECCOMP) [Y/n/?] y
Timer frequency
> 1. 100 HZ (HZ_100)
  2. 250 HZ (HZ_250)
  3. 1000 HZ (HZ_1000)
choice[1-3?]: 1
Function reordering (REORDER) [N/y/?] (NEW)

---

### Post by mintyfresh on 2006-08-05
Im doing ok now, I figured a few things out, you can change it later in the menuconfig. Just ignore my last few posts.

---

### Post by mintyfresh on 2006-08-05
it worked - thanks!!!

---

