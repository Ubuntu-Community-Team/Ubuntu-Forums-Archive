---
title: "Having difficulty compiling Realtek WiFi drivers"
date: 2011-11-15
forum: Packaging and Compiling Programs
---

### Post by hotweiss on 2011-11-15
My ping in Ubuntu is twice as high as it is in Windows.  So I thought maybe I should give the latest official Realtek drivers a try.  When I try compiling them, I get this error:

> make -C /lib/modules/3.2.0-999-generic/build M=/home/paul/Downloads/rtl modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-999-generic'
  CC [M]  /home/paul/Downloads/rtl/base.o
In file included from /home/paul/Downloads/rtl/base.c:31:0:
/home/paul/Downloads/rtl/wifi.h:1496:24: error: field &#8216;irq_tasklet&#8217; has incomplete type
/home/paul/Downloads/rtl/wifi.h:1497:24: error: field &#8216;irq_prepare_bcn_tasklet&#8217; has incomplete type
/home/paul/Downloads/rtl/base.c: In function &#8216;_rtl_init_hw_ht_capab&#8217;:
/home/paul/Downloads/rtl/base.c:210:3: error: implicit declaration of function &#8216;in_interrupt&#8217; [-Werror=implicit-function-declaration]
/home/paul/Downloads/rtl/base.c:210:3: error: implicit declaration of function &#8216;in_atomic&#8217; [-Werror=implicit-function-declaration]
/home/paul/Downloads/rtl/base.c:210:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:221:4: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:230:4: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;_rtl_init_mac80211&#8217;:
/home/paul/Downloads/rtl/base.c:310:4: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_init_core&#8217;:
/home/paul/Downloads/rtl/base.c:454:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:459:4: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: At top level:
/home/paul/Downloads/rtl/base.c:760:1: warning: data definition has no type or storage class [enabled by default]
/home/paul/Downloads/rtl/base.c:760:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/paul/Downloads/rtl/base.c:760:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_tx_mgmt_proc&#8217;:
/home/paul/Downloads/rtl/base.c:775:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_action_proc&#8217;:
/home/paul/Downloads/rtl/base.c:809:4: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:824:6: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:856:4: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:861:4: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_is_special_data&#8217;:
/home/paul/Downloads/rtl/base.c:904:5: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:925:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_tx_agg_start&#8217;:
/home/paul/Downloads/rtl/base.c:965:2: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_tx_agg_stop&#8217;:
/home/paul/Downloads/rtl/base.c:996:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:1000:2: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_rx_agg_start&#8217;:
/home/paul/Downloads/rtl/base.c:1041:2: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_rx_agg_stop&#8217;:
/home/paul/Downloads/rtl/base.c:1060:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:1064:2: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_tx_agg_oper&#8217;:
/home/paul/Downloads/rtl/base.c:1087:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:1091:2: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_watchdog_wq_callback&#8217;:
/home/paul/Downloads/rtl/base.c:1256:5: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: At top level:
/home/paul/Downloads/rtl/base.c:1408:1: warning: data definition has no type or storage class [enabled by default]
/home/paul/Downloads/rtl/base.c:1408:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;EXPORT_SYMBOL&#8217; [-Wimplicit-int]
/home/paul/Downloads/rtl/base.c:1408:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/paul/Downloads/rtl/base.c: In function &#8216;rtl_recognize_peer&#8217;:
/home/paul/Downloads/rtl/base.c:1573:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:1580:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:1585:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:1590:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c:1595:3: warning: format &#8216;%lx&#8217; expects argument of type &#8216;long unsigned int&#8217;, but argument 5 has type &#8216;int&#8217; [-Wformat]
/home/paul/Downloads/rtl/base.c: At top level:
/home/paul/Downloads/rtl/base.c:1657:15: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/paul/Downloads/rtl/base.c:1658:15: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/paul/Downloads/rtl/base.c:1659:15: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/paul/Downloads/rtl/base.c:1660:16: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/paul/Downloads/rtl/base.c:1661:20: error: expected declaration specifiers or &#8216;...&#8217; before string constant
cc1: some warnings being treated as errors

make[2]: *** [/home/paul/Downloads/rtl/base.o] Error 1
make[1]: *** [_module_/home/paul/Downloads/rtl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-999-generic'
make: *** [all] Error 2

Any ideas?  Thanks.

---

### Post by hangelwen on 2011-11-17
> **hotweiss said:**
> My ping in Ubuntu is twice as high as it is in Windows.  So I thought maybe I should give the latest official Realtek drivers a try.  When I try compiling them, I get this error:



Any ideas?  Thanks.

I got the same errors. Did you figure it out? Thanks~

---

### Post by Bachstelze on 2011-11-17
I'll hazard a guess that the driver is not compatible with your kernel version.

---

### Post by hotweiss on 2011-11-18
> **Bachstelze said:**
> I'll hazard a guess that the driver is not compatible with your kernel version.

That's what I was thinking.  Oh well, the ping difference is not noticeable anyways.

And no, I haven't figured out the solution.

---

### Post by hotweiss on 2011-11-21
Here's something in interesting.  In Kubuntu my ping is the same as it is in Windows.  Kubuntu has come a long way. I think I am switching to it.

---

### Post by exclusive213 on 2011-11-25
I was trying the same thing as you. In my scenario I was trying to build for the Realtek 8192e under the 3.1.2 kernel under mint. It sucks that I can't use it because 3.1.2 feels smoother then 2.6

---

### Post by Mamsaac on 2011-12-16
Add a

#include <linux/interrupt.h>

to the top of wifi.h

That solves the problems and it builds just fine.

---

### Post by danger89 on 2011-12-17
Same problem (also after #include <linux/interrupt.h> added to the wifi.h) :(

Using Linux Kernel 3.0.0-14

Solution below this post.

---

### Post by danger89 on 2011-12-17
Thanks to the developer L. Finger of the driver, I will share the patch files in order to compile the latest version under Linux Kernel 3.2.


The 'compile_fixes' file should be used first.

Usage (if you have kernel 3.2.0.x):
> cd /rtl modules../
patch -p1 < {/path/to/patch/compile_fixes}
patch -p1 < {/path/to/patch/fixes_for_3_2}
sudo su
make
make install
reboot

Please check the attachment.

Mirror #1: [http://www.2shared.com/file/D9_srknK/patch_files.html](http://www.2shared.com/file/D9_srknK/patch_files.html)
Mirror #2: [http://www.mediafire.com/?426x5cttmn8vbth](http://www.mediafire.com/?426x5cttmn8vbth)
Mirror #3: [http://www.megafileupload.com/en/file/335362/patch-files-zip.html](http://www.megafileupload.com/en/file/335362/patch-files-zip.html)
Mirror #4: [http://www.filedropper.com/patchfiles](http://www.filedropper.com/patchfiles)

---

