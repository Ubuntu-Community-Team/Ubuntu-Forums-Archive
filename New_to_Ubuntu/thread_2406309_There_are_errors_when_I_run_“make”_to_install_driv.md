---
title: "There are errors when I run “make” to install driver of i40e on the Ubuntu 18.04.1(Se"
date: 2018-11-19
forum: New to Ubuntu
---

### Post by yu1yu1yu1 on 2018-11-19
[FONT=Ubuntu][Intel i40e driver link ]("https://downloadcenter.intel.com/zh-cn/download/28306/-pcie-linux-40-")
[Ubuntu 18.04.1 ISO link]("http://cdimage.ubuntu.com/releases/18.04.1/release/")
[/FONT]
[FONT=Ubuntu][COLOR=#000080]Kernel: Linux ubuntu 4.15.0-29-generic #31-Ubuntu SMP Tue Jul 17 15:39:52 UTC 2018 x86_64 [/COLOR][/FONT][COLOR=#000080][FONT=Ubuntu]x86_64 [/FONT][/COLOR][COLOR=#000080][FONT=Ubuntu]x86_64 GNU/Linux[/FONT][/COLOR][FONT=Ubuntu][COLOR=#000080]
Make: GNU Make 4.1
GCC: Thread model:  posix  --------gcc version 7.3.0(Ubuntu 7.3.0-16ubuntu3)

When I ran &#8220;make&#8221; to install i40e driver,I get the error &#8220;cc1: error: code model kernel does not support PIC mode&#8221;[/COLOR]

  [ATTACH=CONFIG]281695[/ATTACH][/FONT]
[FONT=Ubuntu]

[COLOR=#000080]
Then I searched the solution on the Internet, I tried the way as follow that looks like useful for others,[/COLOR][/FONT][COLOR=#000080]
[B]
"vim /usr/src/linux-headers-4.15.0-29-generic/arch/x86/Makefile"[/B]

[B]// adding explicit -fno-PIE to KBUILD_CFLAGS in the kernel headers Makefile.
KBUILD_CFLAGS += -mno-mmx -mno-sse -mno-sse2 -mno-3dnow
KBUILD_CFLAGS += $(call cc-option,-mno-avs,) -fno-PIE // add in this line[/B][/COLOR]


[ATTACH=CONFIG]281696[/ATTACH]

[FONT=Ubuntu]

[COLOR=#000080]**But at last, new errors happen, I don&#8217;t know how to solve it.**[/COLOR]
[/FONT]
[FONT=Ubuntu][URL="https://ubuntucommunity.s3-us-east-2.amazonaws.com/original/2X/3/3a1ae71ac13378ccb3e153cfc398c0968a88dbd5.JPG"][IMG]https://ubuntucommunity.s3-us-east-2.amazonaws.com/optimized/2X/3/3a1ae71ac13378ccb3e153cfc398c0968a88dbd5_1_690x840.JPG[/IMG][COLOR=#FFFFFF]**1.J**[/COLOR]
[/URL][/FONT]
[COLOR=#000080][FONT=Ubuntu]Please help me!!![/FONT][/COLOR]

---

### Post by yu1yu1yu1 on 2018-11-20
Is there anyone hit this similar[FONT=Tahoma, Arial][COLOR=#434343] [/COLOR][/FONT]problem? 

My dear friends, could you please give me some tips on that? I would be really benefited if you could give me some suggestions&#8230; Thanks for your kind help in advance, guys!

---

