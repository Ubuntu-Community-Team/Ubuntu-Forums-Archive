---
title: "Google Earth keeps crashing on Ubuntu"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Wake Rider on 2008-10-29
Every time I click on Google Earth in Ubuntu 8.04 Hardy, it loads up but then crashes out. I have installed the 4.2 because the 4.3 beta won't even log in to the Google Earth servers. I got this information out of the crash logs, can someone please decipher and explain to me what I can do to fix it.

> CRASHLOGVER 1
CRASHLOGID 0xF2B4CE11
APPVERMAJOR 4
APPVERMINOR 2
APPVERBUILD 205
APPBUILDDATE Nov 13 2007
APPBUILDTIME 17:52:07
OSTYPE 11
OSVERMAJOR 2
OSVERMINOR 6
OSVERBUILD 24
OSVERPATCH 0
PID 7247
CRASHSIGNAL 11
CRASHTIME 1225260331
PROGRAMUPTIME 5

STACK 0x8057fb4
STACK 0x8058399
STACK 0xffffe500
STACK 0xf60219c6
STACK 0xf6023a6d
STACK 0xf60250ea
STACK 0xf60272eb
STACK 0xf6f7e904
STACK 0xf6f7e9aa
STACK 0xf7a3b06e
STACK 0xf7a38c2d
STACK 0xf7376f3f
STACK 0xf7382eae
STACK 0xf7383b6c
STACK 0xf738412c
STACK 0xf7a39a6f
STACK 0xf7a388c9
STACK 0xf7a388fb
STACK 0xf5fa34fb
STACK 0xf609009e

DSO googleearth-bin/0x8048000/111416
DSO linux-gate.so.1/0xffffe000/2028
DSO libbase.so/0xf7e4f000/669696
DSO libcomponent.so/0xf7e37000/86805
DSO libfusion.so/0xf7e32000/13124
DSO libgeobase.so/0xf7acc000/3443270
DSO libmath.so/0xf7ab1000/103833
DSO libwmsbase.so/0xf7a4c000/395459
DSO libnet.so/0xf7a01000/287819
DSO libalchemyext.so/0xf79fc000/15216
DSO libcollada.so/0xf76a3000/3388384
DSO libgoogleearth.so/0xf7536000/1439454
DSO libGLU.so.1/0xf74b8000/507779
DSO libcrypto.so.0.9.8/0xf7391000/1103016
DSO libcurl.so.3/0xf7368000/159800
DSO libfreeimage.so.3/0xf72a5000/770245
DSO libgcc_s.so.1/0xf729a000/39096
DSO libjpeg.so.62/0xf7276000/139688
DSO libmng.so.1/0xf7218000/364312
DSO libpng12.so.0/0xf71f0000/156964
DSO libqt-mt.so.3/0xf6aba000/7313347
DSO libqui.so.1/0xf6a1e000/621811
DSO libssl.so.0.9.8/0xf69e3000/221460
DSO libstdc++.so.6/0xf6908000/849472
DSO libtiff.so.3/0xf68ac000/364328
DSO libz.so.1/0xf6895000/86972
DSO libIGCore.so/0xf679e000/952308
DSO libIGGfx.so/0xf66e6000/704928
DSO libIGAttrs.so/0xf6683000/365780
DSO libIGDisplay.so/0xf666f000/70352
DSO libIGGui.so/0xf662d000/246068
DSO libIGSg.so/0xf651f000/1036804
DSO libIGCollision.so/0xf6510000/55044
DSO libIGMath.so/0xf64c6000/277228
DSO libIGUtils.so/0xf649f000/146568
DSO libIGOpt.so/0xf63c4000/841480
DSO libIGExportCommon.so/0xf633c000/517352
DSO libcommon.so/0xf623f000/997730
DSO librender.so/0xf61e4000/349174
DSO libauth.so/0xf6159000/548318
DSO libframework.so/0xf6142000/86398
DSO libm.so.6/0xf6106000/143208
DSO libc.so.6/0xf5fb7000/1347020
DSO libpthread.so.0/0xf5f9e000/80688
DSO libdl.so.2/0xf5f9a000/7424
DSO libXrender.so.1/0xf5f92000/28152
DSO libXcursor.so.1/0xf5f89000/31268
DSO libXft.so.2/0xf5f76000/67220
DSO libfreetype.so.6/0xf5f06000/438628
DSO libfontconfig.so.1/0xf5edc000/164768
DSO libXext.so.6/0xf5ece000/51440
DSO libX11.so.6/0xf5de7000/933472
DSO libSM.so.6/0xf5ddf000/26384
DSO libICE.so.6/0xf5dc6000/83208
DSO libGL.so.1/0xf5d22000/554694
DSO libGL.so.1/0xf5daa6e0/112416
DSO ld-linux.so.2/0xf7efc000/115196
DSO libXfixes.so.3/0xf5d1d000/12628
DSO libexpat.so.1/0xf5cfb000/124192
DSO libXau.so.6/0xf5cf8000/5460
DSO libxcb-xlib.so.0/0xf5cf6000/2636
DSO libxcb.so.1/0xf5cde000/91992
DSO libGLcore.so.1/0xf51c9000/11352191
DSO libGLcore.so.1/0xf5c9d880/263092
DSO libnvidia-tls.so.1/0xf51c6000/1328
DSO libXdmcp.so.6/0xf51c1000/15076
DSO libnss_compat.so.2/0xf47b6000/25536
DSO libnsl.so.1/0xf479e000/79940
DSO libnss_nis.so.2/0xf612c000/32204
DSO libnss_files.so.2/0xf4793000/35748
DSO libnss_dns.so.2/0xf47cf000/15000
DSO libresolv.so.2/0xf3f68000/60784
DSO libevll.so/0xf2762000/6108992
DSO libnavigate.so/0xefe10000/1336238
DSO liblayer.so/0xefbbf000/2359150
DSO libmeasure.so/0xefb0f000/696250
DSO libbasicIngest.so/0xefa24000/915434
DSO libgooglesearch.so/0xef969000/741326
DSO libinput_plugin.so/0xef92e000/232214
DSO libflightsim.so/0xef829000/1022678

---

### Post by Wake Rider on 2008-10-29
I tried turning Compiz off but even that didn't help. What's troubling is that I used to be able to run version 4.2 perfectly fine, it is only just recently that this has started happening. Now I can't run Google Earth at all on Ubuntu. Please Help!!:(:(

---

### Post by chewit on 2008-10-29
I get the same problem. The way I have fixed it is, not to do anything well google earth is loading. Don't even move your mouse. 

Google Earth won't crash after startup.

---

### Post by CRIMPS on 2008-12-28
I am having the same problem.  I will give you solution of not moving the mouse a try.  Regardless, this is very frustrating.  I have been under the impression that Google Earth is a little buggy.  However, I do believe there is a conflict with running Compiz (3d effects specifically) and starting Google Earth.

Im not a Programmer/Developer, but maybe I could help someone look into this further with offering some feedback? ;)

---

### Post by CRIMPS on 2009-02-17
I have always had a problem with upgrading from 8.04 to 8.10 due to Nvidia driver issues.  So, I reinstalled and went back to 8.04 on my laptop for more stable video.

I am not running compiz either.  I have no issues with starting and running Google Earth 5.0 now.  Im sure this is related.

---

