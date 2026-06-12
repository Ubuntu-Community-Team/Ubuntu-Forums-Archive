---
title: "HOWTO: Dual head with i810 driver and 855GM hardware"
date: 2006-04-05
forum: Outdated Tutorials &amp; Tips
---

### Post by pestilence4hr on 2006-04-05
These instructions will get dual head working in breezy on video cards that use
the i810 driver.  I have a 855GM on an dell inspiron 700m, and this
works for me.  The procedure for dapper is easier (but similar), since the patch
mentioned in the bug report below can be applied directly to the dapper
source.

The symptom of this problem is documented in [URL="https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-i810/+bug/26341"]Bug
#26341[/URL], primarily, I get the following error when trying to use dual
head configs:

```

(EE) I810(0): vm86() syscall generated signal 11.

```

First, make sure you have the following line in your
/etc/apt/sources.list:

```

deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

```


Next, update apt and grab the source and dependencies:

```

mkdir i810temp
cd i810temp
sudo apt-get update
apt-get source xserver-xorg-driver-i810
sudo apt-get build-dep xserver-xorg-driver-i810

```

Now grab this file [000_stolen_from_HEAD_i810.diff.gz]("http://ubuntuforums.org/attachment.php?attachmentid=8042&stc=1&d=1144274101") and replace the one
that is in the source package:

```

gunzip 000_stolen_from_HEAD_i810.diff.gz
mv xorg-6.8.2/debian/patches/000_stolen_from_HEAD_i810.diff 000_stolen_from_HEAD_i810.diff_old
mv 000_stolen_from_HEAD_i810.diff xorg-6.8.2/debian/patches/

```

Now edit the file xorg-6.8.2/debian/changelog to have the following at
the top:

```

xorg (6.8.2-77dual) breezy; urgency=low

  * Patched for dual head configs using patch found here: 
  *   https://bugs.freedesktop.org/attachment.cgi?id=4323
  *   (credit: Alan Hourihane)

 -- John Fettig <jfettig@uiuc.edu>  Wed, 05 Apr 2006 14:41:08 -0500


```

Now all that is left is to build the package and install it.  For this
you need "fakeroot", so grab that and go:

```

sudo aptitude install fakeroot
cd xorg-6.8.2
sudo dpkg-buildpackage -rfakeroot -b

```

This last step will take a while, even on fast machines.

Now you will have a bunch of .deb files, you only need to install the
i810 one.

```

cd ../
sudo dpkg -i xserver-xorg-driver-i810_6.8.2-77dual_i386.deb

```

Now you need to reboot (I think a reboot is neccessary, to reinitialize
the video hardware), and it should work.  A working dual head config is
also attached to the bug report mentioned above.

---

### Post by torf on 2006-05-29
Thank you for the how-to.  I've tried the entire process twice, however I keep getting errors when I run this command:
sudo dpkg-buildpackage -rfakeroot -b

Here are the errors:
```
i810_driver.c:77:16: error: Xv.h: No such file or directory
make[8]: *** [i810_driver.o] Error 1
make[8]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver/hw/xfree86/drivers/i810'
make[7]: *** [all] Error 2
make[7]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver/hw/xfree86/drivers'
make[6]: *** [all] Error 2
make[6]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver/hw/xfree86'
make[5]: *** [hw/xfree86] Error 2
make[5]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc'
make[2]: *** [World] Error 2
make[2]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc'
make[1]: *** [World] Error 2
make[1]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc'
make: *** [stampdir/build] Error 2
```

I though I had followed the how-to exactly. Any idea as to what went wrong? Thanks.

---

### Post by halfvolle melk on 2006-05-29
The error states that *Xv.h* can't be found. A [search for the contents of packages](http://packages.ubuntu.com/) shows that [*Xv.h*](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=Xv.h&searchmode=searchfiles&case=insensitive&version=breezy&arch=i386) is in *x11proto-video-dev*.
[http://packages.ubuntu.com/breezy/x11/x11proto-video-dev](http://packages.ubuntu.com/breezy/x11/x11proto-video-dev)

Installing it
```
sudo apt-get install x11proto-video-dev
```
and trying to build the package again *might* resolve the issue, though I'm *not at all sure*.
Hope my guessing helps.

---

### Post by torf on 2006-05-29
Good suggestion, I honestly forgot to check. Unfortunately, x11proto-video-dev was already installed:

```

$ sudo apt-get install x11proto-video-dev
Reading package lists... Done
Building dependency tree... Done
x11proto-video-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

$ sudo find / | grep Xv.h
/usr/include/X11/extensions/Xv.h

```

I tried running the command again, and while it was taking its time to do its thing I copied the Xv.h file into the same directory as i810_driver.c - The result of this was still failure, but new errors:
```

i830_driver.c:196: error: &#8216;PCI_CHIP_E7221_G&#8217; undeclared here (not in a function)
i830_driver.c:197: error: &#8216;PCI_CHIP_I915_GM&#8217; undeclared here (not in a function)
i830_driver.c:198: error: &#8216;PCI_CHIP_I945_G&#8217; undeclared here (not in a function)
i830_driver.c:580: warning: no previous prototype for &#8216;I830GetBestRefresh&#8217;
i830_driver.c: In function &#8216;GetDisplayDevices&#8217;:
i830_driver.c:754: warning: comparison between pointer and integer
i830_driver.c: In function &#8216;SetPipeAccess&#8217;:
i830_driver.c:826: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:826: warning: comparison between pointer and integer
i830_driver.c: In function &#8216;SetDisplayDevices&#8217;:
i830_driver.c:875: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;specifiedMonitor&#8217;
i830_driver.c:881: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;leaving&#8217;
i830_driver.c: In function &#8216;I830DetectMemory&#8217;:
i830_driver.c:1326: warning: implicit declaration of function &#8216;IS_I915GM&#8217;
i830_driver.c:1326: warning: nested extern declaration of &#8216;IS_I915GM&#8217;
i830_driver.c:1326: warning: implicit declaration of function &#8216;IS_I945G&#8217;
i830_driver.c:1326: warning: nested extern declaration of &#8216;IS_I945G&#8217;
i830_driver.c: In function &#8216;I830BIOSPreInit&#8217;:
i830_driver.c:2084: warning: case label value is less than minimum value for type
i830_driver.c:2087: warning: case label value is less than minimum value for type
i830_driver.c:2090: warning: case label value is less than minimum value for type
i830_driver.c:2203: warning: comparison between pointer and integer
i830_driver.c:2227: warning: comparison between pointer and integer
i830_driver.c:2305: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;fixedPipe&#8217;
i830_driver.c:2305: warning: statement with no effect
i830_driver.c:2310: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;fixedPipe&#8217;
i830_driver.c:2310: warning: statement with no effect
i830_driver.c:2312: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;fixedPipe&#8217;
i830_driver.c:2312: warning: statement with no effect
i830_driver.c:2317: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;specifiedMonitor&#8217;
i830_driver.c:2317: warning: statement with no effect
i830_driver.c:2398: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;specifiedMonitor&#8217;
i830_driver.c:2398: warning: statement with no effect
i830_driver.c:2448: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:2448: warning: passing argument 3 of &#8216;xf86GetOptValBool&#8217; from incompatible pointer type
i830_driver.c:2449: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:2456: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:2456: warning: statement with no effect
i830_driver.c:2457: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;rotate&#8217;
i830_driver.c:2457: warning: statement with no effect
i830_driver.c:2461: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:2461: warning: statement with no effect
i830_driver.c:2462: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;rotate&#8217;
i830_driver.c:2462: warning: statement with no effect
i830_driver.c:2473: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:2483: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;checkDevices&#8217;
i830_driver.c:2483: warning: statement with no effect
i830_driver.c:2486: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;checkDevices&#8217;
i830_driver.c:2486: warning: statement with no effect
i830_driver.c:2490: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;checkDevices&#8217;
i830_driver.c:2494: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;checkDevices&#8217;
i830_driver.c:2494: warning: statement with no effect
i830_driver.c:2498: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;checkDevices&#8217;
i830_driver.c:2498: warning: statement with no effect
i830_driver.c:2745: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:2745: warning: statement with no effect
i830_driver.c:2748: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;fixedPipe&#8217;
i830_driver.c:2748: warning: comparison between pointer and integer
i830_driver.c:2750: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;fixedPipe&#8217;
i830_driver.c:2750: warning: statement with no effect
i830_driver.c:2753: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;fixedPipe&#8217;
i830_driver.c:2781: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:2781: warning: comparison between pointer and integer
i830_driver.c:2784: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:3042: warning: implicit declaration of function &#8216;I830GetModePool&#8217;
i830_driver.c:3042: warning: nested extern declaration of &#8216;I830GetModePool&#8217;
i830_driver.c:3042: warning: assignment makes pointer from integer without a cast
i830_driver.c:3267: warning: implicit declaration of function &#8216;I830PrintModes&#8217;
i830_driver.c:3267: warning: nested extern declaration of &#8216;I830PrintModes&#8217;
i830_driver.c:3278: warning: implicit declaration of function &#8216;I830SetModeParameters&#8217;
i830_driver.c:3278: warning: nested extern declaration of &#8216;I830SetModeParameters&#8217;
i830_driver.c:3324: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:3330: error: &#8216;I810shadowFBSymbols&#8217; undeclared (first use in this function)
i830_driver.c:3330: error: (Each undeclared identifier is reported only once
i830_driver.c:3330: error: for each function it appears in.)
i830_driver.c:3330: warning: passing argument 1 of &#8216;xf86LoaderReqSymLists&#8217; from incompatible pointer type
i830_driver.c: In function &#8216;SaveHWState&#8217;:
i830_driver.c:3557: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:3557: warning: comparison between pointer and integer
i830_driver.c:3558: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:3558: warning: passing argument 2 of &#8216;SetBIOSPipe&#8217; makes integer from pointer without a cast
i830_driver.c:3566: error: &#8216;struct _VESARec&#8217; has no member named &#8216;stateRefresh&#8217;
i830_driver.c:3566: warning: statement with no effect
i830_driver.c: In function &#8216;RestoreHWState&#8217;:
i830_driver.c:3632: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:3632: warning: comparison between pointer and integer
i830_driver.c:3633: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;origPipe&#8217;
i830_driver.c:3633: warning: passing argument 2 of &#8216;SetBIOSPipe&#8217; makes integer from pointer without a cast
i830_driver.c:3679: error: &#8216;struct _VESARec&#8217; has no member named &#8216;stateRefresh&#8217;
i830_driver.c:3679: warning: passing argument 3 of &#8216;SetRefreshRate&#8217; makes integer from pointer without a cast
i830_driver.c: In function &#8216;I830BIOSScreenInit&#8217;:
i830_driver.c:4697: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;rotate&#8217;
i830_driver.c:4704: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:4705: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowPitch&#8217;
i830_driver.c:4705: warning: statement with no effect
i830_driver.c:4706: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowPtr&#8217;
i830_driver.c:4706: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowPitch&#8217;
i830_driver.c:4706: error: invalid operands to binary *
i830_driver.c:4706: warning: passing argument 1 of &#8216;Xalloc&#8217; makes integer from pointer without a cast
i830_driver.c:4706: warning: statement with no effect
i830_driver.c:4707: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowPitch&#8217;
i830_driver.c:4707: error: invalid operands to binary /
i830_driver.c:4707: warning: statement with no effect
i830_driver.c:4708: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowPtr&#8217;
i830_driver.c:4708: warning: statement with no effect
i830_driver.c:4710: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowPtr&#8217;
i830_driver.c:4710: warning: statement with no effect
i830_driver.c:4738: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:4777: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;shadowFB&#8217;
i830_driver.c:4778: error: &#8216;I830RefreshArea&#8217; undeclared (first use in this function)
i830_driver.c:4779: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;rotate&#8217;
i830_driver.c:4780: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;PointerMoved&#8217;
i830_driver.c:4781: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;PointerMoved&#8217;
i830_driver.c:4781: warning: statement with no effect
i830_driver.c:4782: error: &#8216;I830PointerMoved&#8217; undeclared (first use in this function)
i830_driver.c:4782: warning: statement with no effect
i830_driver.c:4786: error: &#8216;I830RefreshArea8&#8217; undeclared (first use in this function)
i830_driver.c:4786: warning: statement with no effect
i830_driver.c:4789: error: &#8216;I830RefreshArea16&#8217; undeclared (first use in this function)
i830_driver.c:4789: warning: statement with no effect
i830_driver.c:4792: error: &#8216;I830RefreshArea24&#8217; undeclared (first use in this function)
i830_driver.c:4792: warning: statement with no effect
i830_driver.c:4795: error: &#8216;I830RefreshArea32&#8217; undeclared (first use in this function)
i830_driver.c:4795: warning: statement with no effect
i830_driver.c: In function &#8216;I830BIOSLeaveVT&#8217;:
i830_driver.c:4962: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;leaving&#8217;
i830_driver.c:4962: warning: statement with no effect
i830_driver.c:4964: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;devicesTimer&#8217;
i830_driver.c:4965: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;devicesTimer&#8217;
i830_driver.c:4965: warning: passing argument 1 of &#8216;TimerCancel&#8217; from incompatible pointer type
i830_driver.c:4966: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;devicesTimer&#8217;
i830_driver.c:4966: warning: statement with no effect
i830_driver.c: In function &#8216;I830DetectMonitorChange&#8217;:
i830_driver.c:5074: warning: assignment makes pointer from integer without a cast
i830_driver.c: At top level:
i830_driver.c:5182: warning: no previous prototype for &#8216;I830CheckModeSupport&#8217;
i830_driver.c: In function &#8216;I830BIOSEnterVT&#8217;:
i830_driver.c:5226: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;leaving&#8217;
i830_driver.c:5226: warning: statement with no effect
i830_driver.c:5309: warning: implicit declaration of function &#8216;I830DRIResume&#8217;
i830_driver.c:5309: warning: nested extern declaration of &#8216;I830DRIResume&#8217;
i830_driver.c:5323: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;checkDevices&#8217;
i830_driver.c:5324: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;devicesTimer&#8217;
i830_driver.c:5324: warning: statement with no effect
i830_driver.c: In function &#8216;I830BIOSCloseScreen&#8217;:
i830_driver.c:5488: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;devicesTimer&#8217;
i830_driver.c:5489: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;devicesTimer&#8217;
i830_driver.c:5489: warning: passing argument 1 of &#8216;TimerCancel&#8217; from incompatible pointer type
i830_driver.c:5490: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;devicesTimer&#8217;
i830_driver.c:5490: warning: statement with no effect
i830_driver.c: In function &#8216;I830CheckDevicesTimer&#8217;:
i830_driver.c:5651: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5651: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5651: warning: statement with no effect
i830_driver.c:5652: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5652: warning: statement with no effect
i830_driver.c:5666: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5666: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5667: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5667: error: invalid operands to binary &
i830_driver.c:5668: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5668: error: invalid operands to binary &
i830_driver.c:5672: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5672: error: invalid operands to binary &
i830_driver.c:5673: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5673: error: invalid operands to binary &
i830_driver.c:5682: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5682: error: invalid operands to binary &
i830_driver.c:5682: warning: passing argument 1 of &#8216;CountBits&#8217; makes integer from pointer without a cast
i830_driver.c:5683: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5683: error: invalid operands to binary &
i830_driver.c:5683: error: invalid operands to binary >>
i830_driver.c:5683: warning: passing argument 1 of &#8216;CountBits&#8217; makes integer from pointer without a cast
i830_driver.c:5689: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5689: error: invalid operands to binary &
i830_driver.c:5689: warning: passing argument 1 of &#8216;CountBits&#8217; makes integer from pointer without a cast
i830_driver.c:5690: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5690: error: invalid operands to binary &
i830_driver.c:5690: error: invalid operands to binary >>
i830_driver.c:5690: warning: passing argument 1 of &#8216;CountBits&#8217; makes integer from pointer without a cast
i830_driver.c:5714: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5714: error: invalid operands to binary &
i830_driver.c:5715: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5715: error: invalid operands to binary <<
i830_driver.c:5715: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5715: error: invalid operands to binary |
i830_driver.c:5715: warning: statement with no effect
i830_driver.c:5717: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5717: error: invalid operands to binary <<
i830_driver.c:5717: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5717: error: invalid operands to binary |
i830_driver.c:5717: warning: statement with no effect
i830_driver.c:5721: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5721: warning: comparison between pointer and integer
i830_driver.c:5721: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5721: warning: comparison between pointer and integer
i830_driver.c:5729: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5729: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5729: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 4 has type &#8216;struct PciChipsets *&#8217;
i830_driver.c:5729: warning: format &#8216;%x&#8217; expects type &#8216;unsigned int&#8217;, but argument 5 has type &#8216;struct PciChipsets *&#8217;
i830_driver.c:5732: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;specifiedMonitor&#8217;
i830_driver.c:5732: warning: statement with no effect
i830_driver.c:5740: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice2&#8217;
i830_driver.c:5740: error: &#8216;struct _I830Rec&#8217; has no member named &#8216;lastDevice1&#8217;
i830_driver.c:5740: error: invalid operands to binary |
i830_driver.c:5740: warning: statement with no effect
make[8]: *** [i830_driver.o] Error 1
make[8]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver/hw/xfree86/drivers/i810'
make[7]: *** [all] Error 2
make[7]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver/hw/xfree86/drivers'
make[6]: *** [all] Error 2
make[6]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver/hw/xfree86'
make[5]: *** [hw/xfree86] Error 2
make[5]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs/Xserver'
make[4]: *** [all] Error 2
make[4]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc/programs'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc'
make[2]: *** [World] Error 2
make[2]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc'
make[1]: *** [World] Error 2
make[1]: Leaving directory `/home/jon/i810temp/xorg-6.8.2/build-tree/xc'
make: *** [stampdir/build] Error 2

```

I'm guessing that I'm missing some other header file.  Perhaps I need to add something to my environment variables so that the header files can be used during this build...

Thank you very much for your help. Further advice and aid are greatly appreciated.

---

### Post by torf on 2006-05-30
I ended up trying to copy all of the headers from  /usr/include/X11/extensions/ and placing them in the directory where the driver is being compiled - this yielded the same errors.  Any ideas? Thank you.

---

### Post by pestilence4hr on 2006-06-30
I don't know what the issue might be, and it is indeed strange.  Perhaps I have some development headers installed that aren't dependencies of the driver source package.  If you ran
sudo apt-get build-dep xserver-xorg-driver-i810
then I don't know what else to tell you.

The good news is that they applied this patch to the dapper driver package.  So if you install dapper, things should be fixed (although i'm still in breezy so I can't verify).  

You might also live dangerously and try installing the dapper package in breezy, but it might not work, I really don't know.

---

