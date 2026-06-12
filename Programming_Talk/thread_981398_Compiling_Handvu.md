---
title: "Compiling Handvu"
date: 2008-11-13
forum: Programming Talk
---

### Post by BattMatt on 2008-11-13
I'm trying to play around with the webcam gesture program handvu, but it won't compile on my Toshiba Portege M700 running Intrepid.  After downloading and unpacking the source from [http://www.movesinstitute.org/~kolsch/HandVu/HandVu.html#download](http://www.movesinstitute.org/~kolsch/HandVu/HandVu.html#download), I ran ./configure without incident.  But here's what happens when I try to run make:

partain@partain-tablet:~/Desktop/handvu-beta3$ make
make  all-recursive
make[1]: Entering directory `/home/partain/Desktop/handvu-beta3'
Making all in cubicles
make[2]: Entering directory `/home/partain/Desktop/handvu-beta3/cubicles'
if /bin/bash ../libtool --tag=CXX --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/opencv     -DTARGET_SYSTEM=\"i686-pc-linux-gnu\" -DIMG_LIB_OPENCV -DII_TYPE_FLOAT  -O3  -MT IntegralFeatures.lo -MD -MP -MF ".deps/IntegralFeatures.Tpo" -c -o IntegralFeatures.lo IntegralFeatures.cpp; \
	then mv -f ".deps/IntegralFeatures.Tpo" ".deps/IntegralFeatures.Plo"; else rm -f ".deps/IntegralFeatures.Tpo"; exit 1; fi
 g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/opencv -DTARGET_SYSTEM=\"i686-pc-linux-gnu\" -DIMG_LIB_OPENCV -DII_TYPE_FLOAT -O3 -MT IntegralFeatures.lo -MD -MP -MF .deps/IntegralFeatures.Tpo -c IntegralFeatures.cpp  -fPIC -DPIC -o .libs/IntegralFeatures.o
IntegralFeatures.cpp: In member function 'featnum CIntegralFeature::GetNumIncarnations() const':
IntegralFeatures.cpp:202: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CLeftRightIF::CLeftRightIF(int, int)':
IntegralFeatures.cpp:234: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CLeftRightIF::CLeftRightIF(int, int, int, int, int, int, int)':
IntegralFeatures.cpp:264: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CLeftRightIF::CLeftRightIF(std::istream&, int, int)':
IntegralFeatures.cpp:275: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp:282: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CUpDownIF::CUpDownIF(int, int)':
IntegralFeatures.cpp:551: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CUpDownIF::CUpDownIF(int, int, int, int, int, int, int)':
IntegralFeatures.cpp:560: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CUpDownIF::CUpDownIF(std::istream&, int, int)':
IntegralFeatures.cpp:594: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp:602: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CLeftCenterRightIF::CLeftCenterRightIF(int, int)':
IntegralFeatures.cpp:850: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CLeftCenterRightIF::CLeftCenterRightIF(int, int, int, int, int, int, int, int)':
IntegralFeatures.cpp:859: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CLeftCenterRightIF::CLeftCenterRightIF(std::istream&, int, int)':
IntegralFeatures.cpp:894: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp:902: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CSevenColumnsIF::CSevenColumnsIF(int, int)':
IntegralFeatures.cpp:1199: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CSevenColumnsIF::CSevenColumnsIF(int, int, int, int, int, int, int, int, int, int, int, int)':
IntegralFeatures.cpp:1207: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CSevenColumnsIF::CSevenColumnsIF(std::istream&, int, int)':
IntegralFeatures.cpp:1254: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp:1262: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CDiagIF::CDiagIF(int, int)':
IntegralFeatures.cpp:1682: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CDiagIF::CDiagIF(int, int, int, int, int, int, int, int)':
IntegralFeatures.cpp:1691: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CDiagIF::CDiagIF(std::istream&, int, int)':
IntegralFeatures.cpp:1726: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp:1735: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CFourBoxesIF::CFourBoxesIF(int, int)':
IntegralFeatures.cpp:2096: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CFourBoxesIF::CFourBoxesIF(int, int, const CRect*, const CRect*, const CRect*, const CRect*)':
IntegralFeatures.cpp:2103: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp: In constructor 'CFourBoxesIF::CFourBoxesIF(std::istream&, int, int)':
IntegralFeatures.cpp:2144: error: 'ULONG_LONG_MAX' was not declared in this scope
IntegralFeatures.cpp:2149: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp:2156: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp:2163: error: 'alloca' was not declared in this scope
IntegralFeatures.cpp:2170: error: 'alloca' was not declared in this scope
make[2]: *** [IntegralFeatures.lo] Error 1
make[2]: Leaving directory `/home/partain/Desktop/handvu-beta3/cubicles'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/partain/Desktop/handvu-beta3'
make: *** [all] Error 2
partain@partain-tablet:~/Desktop/handvu-beta3$

---

### Post by tylerdurd on 2008-12-11
Same error :(, haven't you find any solution ?

---

### Post by vtikha on 2009-01-30
Hi,

Had the same problems but with a bit of effort managed to get it working.
You will need to include <limits.h> but:
ULONG_LONG_MAX is nonstandard and will not appear in <limits.h> therefore modify the code to use ULLONG_MAX which is covered.

I then encountered many other issues and had to include <stdio.h> <cstring> <limits.h> <stdlib.h> <string.h> to different files (don t remember them all at the moment)

Eventually it will compile.
Hope it works,

---

### Post by Branimir on 2009-01-30
"
ULONG_LONG_MAX is nonstandard and will not appear in <limits.h> therefore modify the code to use ULLONG_MAX which is covered.
"

Isn't it simpler to just add #define ULONG_LONG_MAX ULLONG_MAX
in limits.h?

Greetsa, Branimir.

---

### Post by jeffjanzen on 2009-01-30
@vtikha: any chance i could persuade you package a deb and upload it here/post a link?

i'm dying to give this a try, but i'm not much of a programmer.

---

### Post by david.shah on 2009-10-15
There were 7 files that needed to be modified for handvu-beta3 to compile on my machine. If you open each of these up in vi or your editor of choice and add the following, (assuming that any other dependencies are installed properly) you should be good to go! I should note, you may not need to add all of the include statements (I got lazy and just copied and pasted as I went along, regardless of wether they were needed or not out of avoidence of running into same errors as I continued)

**File 0: handvu-beta3/cubicles/IntegralFeatures.cpp**
*around lines 65 - 75 add*
#include<limits.h>
#include<stdio.h>
#include<cstring>
#include<stdlib.h>
#include<string.h>              
#include<alloca.h>              

**File 1: handvu-beta3/cubicles/IntegralFeaturesSame.cpp**
*around lines 68 - 77 add*
#include<limits.h>
#include<stdio.h>
#include<cstring>
#include<stdlib.h>
#include<string.h>              
#include<alloca.h>

**File 2: handvu-beta3/cubicles/CascadeFileParser.yy**
*around lines 63-68 add*
#include<string.h>

**File 3: handvu-beta3/cubicles/Scanner.h**
*around lines 62 - 65 add*
#include<limits.h>

**File 4: handvu-beta3/cubicles/IntegralImage.cxx**
*around lines 69 - 71 add*
#include<stdio.h>
#include<string.h>

**File 5: handvu-beta3/handvu/Mask.cpp**
*around lines 28 - 34 add*
#include<limits.h>
 #include<stdio.h>
 #include<cstring>
 #include<stdlib.h>
 #include<string.h>              
 #include<alloca.h>

**File 6: handvu-beta3/handvu/FileHandling.cpp**
*around lines 28 - 34 add*
#include<limits.h>
  #include<stdio.h>
  #include<cstring>
  #include<stdlib.h>
  #include<string.h>              
  #include<alloca.h>

once you've add all that, save and make! You should be good to go! Good luck!

---

### Post by sbsbessa on 2009-10-20
Thanks david.shah for your help, I applied your suggested changes and almost got it going.
I then realised that adding **#include<limits.h> **to **handvu/HandVu.cpp** and **handvu/CubicleWrapper.cpp** would solve the problem.

make already works without errors, now I'll try to figure how to start a demo...

---

### Post by pk_vex on 2010-03-31
Hi,

Did anyone get handVu to work?

I was finally able to successfully compile and install handvu following this guide on installing openCV:

[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

However, when I try to run the hvOpenCV example, I get a segmentation fault.  Anyone have this issue, or if possible, explain what steps you took to setup and install handvu successfully?

---

### Post by protoolz on 2010-04-19
I was getting errors about __BEGIN__ and __END__ and so I replaced it with __CV_BEGIN__ and __CV_END__ respectively, as someone stated here: [http://www.lewin.nu/~erl/blogs/erls/labels/3d.html](http://www.lewin.nu/~erl/blogs/erls/labels/3d.html) and this fixed this problem.

Later on in the build process I get the following error:

In file included from LearnedColor.h:28,
                 from HandVu.cpp:30:
OpticalFlow.h:154: error: ISO C++ forbids declaration of 'CvConDensation' with no type
OpticalFlow.h:154: error: expected ';' before '*' token
make[2]: *** [HandVu.lo] Error 1
make[2]: Leaving directory

I fixed this by adding #include <cvaux.h> to OpticalFlow.h

I had gotten another error about: invalid conversion from `const char*' to `char*' in file FileHandling.cpp so I modified the following

char* slashpos = strrchr(path, '/'); 
to 
const char* slashpos = strrchr(path, '/');


char* dotpos = strrchr(path, '.');
to 
const char* dotpos = strrchr(path, '.');

---

### Post by dhysk on 2010-04-19
Thank you so much protools, i was having these issue myself. I got to the "OpticalFlow.h:154: error: ISO C++ forbids declaration of 'CvConDensation' with no type"

and got stuck. I don't want to backtrack but I'm tring to learn more about programing.  I figured something was missing an include line but how did you find ware it was missing and what exactly needed to be included?

---

### Post by AdagioParaCuerdas on 2010-05-20
I am working on ubuntu 10.04

Two modifications were needed to complete the **make** command.

The one by david.shah, this is also explaned in a [chinese forum]("http://translate.google.com/translate?hl=en&sl=zh-TW&u=http://wadefs.blogspot.com/2010/01/build-handvu-beta3-on-ubuntu.html&ei=1gv1S9GCO4H48AbG_tX9Cg&sa=X&oi=translate&ct=result&resnum=1&ved=0CBUQ7gEwAA&prev=/search%3Fq%3Dhttp://wadefs.blogspot.com/2010/01/build-handvu-beta3-on-ubuntu.html%26hl%3Den") with a patch

> **david.shah said:**
> There were 7 files that needed to be modified for handvu-beta3 to compile on my machine. If you open each of these up in vi or your editor of choice and add the following, (assuming that any other dependencies are installed properly) you should be good to go! I should note, you may not need to add all of the include statements (I got lazy and just copied and pasted as I went along, regardless of wether they were needed or not out of avoidence of running into same errors as I continued)

**File 0: handvu-beta3/cubicles/IntegralFeatures.cpp**
*around lines 65 - 75 add*
#include<limits.h>
#include<stdio.h>
#include<cstring>
#include<stdlib.h>
#include<string.h>              
#include<alloca.h>              

**File 1: handvu-beta3/cubicles/IntegralFeaturesSame.cpp**
*around lines 68 - 77 add*
#include<limits.h>
#include<stdio.h>
#include<cstring>
#include<stdlib.h>
#include<string.h>              
#include<alloca.h>

**File 2: handvu-beta3/cubicles/CascadeFileParser.yy**
*around lines 63-68 add*
#include<string.h>

**File 3: handvu-beta3/cubicles/Scanner.h**
*around lines 62 - 65 add*
#include<limits.h>

**File 4: handvu-beta3/cubicles/IntegralImage.cxx**
*around lines 69 - 71 add*
#include<stdio.h>
#include<string.h>

**File 5: handvu-beta3/handvu/Mask.cpp**
*around lines 28 - 34 add*
#include<limits.h>
 #include<stdio.h>
 #include<cstring>
 #include<stdlib.h>
 #include<string.h>              
 #include<alloca.h>

**File 6: handvu-beta3/handvu/FileHandling.cpp**
*around lines 28 - 34 add*
#include<limits.h>
  #include<stdio.h>
  #include<cstring>
  #include<stdlib.h>
  #include<string.h>              
  #include<alloca.h>

once you've add all that, save and make! You should be good to go! Good luck!

the other was the one by protoolz, about invalid data type conversion

> **protoolz said:**
> I was getting errors about __BEGIN__ and __END__ and so I replaced it with __CV_BEGIN__ and __CV_END__ respectively, as someone stated here: [http://www.lewin.nu/~erl/blogs/erls/labels/3d.html](http://www.lewin.nu/~erl/blogs/erls/labels/3d.html) and this fixed this problem.

Later on in the build process I get the following error:

In file included from LearnedColor.h:28,
                 from HandVu.cpp:30:
OpticalFlow.h:154: error: ISO C++ forbids declaration of 'CvConDensation' with no type
OpticalFlow.h:154: error: expected ';' before '*' token
make[2]: *** [HandVu.lo] Error 1
make[2]: Leaving directory

I fixed this by adding #include <cvaux.h> to OpticalFlow.h

I had gotten another error about: invalid conversion from `const char*' to `char*' in file FileHandling.cpp so I modified the following

char* slashpos = strrchr(path, '/'); 
to 
const char* slashpos = strrchr(path, '/');


char* dotpos = strrchr(path, '.');
to 
const char* dotpos = strrchr(path, '.');

thank you.

---

### Post by pupox on 2010-12-07
I compile handvu fine using all tips on this topic, but when i run hvOpenCV, it show normally the video, however when it recognize a hand gesture it crached wit a segmentation fault.
Please tell me how to fix it.

---

### Post by Polina on 2011-02-17
I cannot find the download link for the handvu sources in handvu's homepage, can you please tell me where I can find it? I've been searching for a while for them. 
I'am asking you, because it seems you already found them since you had compiled them.

---

### Post by Polina on 2011-02-18
I've resolved the problem: i've just googled "download handvu-beta3.tar"  and found them here: [http://www.hackchina.com/dlpre.php?lang=en&id=112967](http://www.hackchina.com/dlpre.php?lang=en&id=112967)
[]("http://ubuntuforums.org/member.php?u=620885")

---

### Post by Om.Ethcelon on 2011-03-26
Hello
i have succesfully compiled handvu
but when i run hvOpenCV
i get "
you need to specify a conductor file as first argument
for example: ../config/default.conductor
"
please help?

---

### Post by mdr83 on 2013-01-31
No one has posted on this thread in a while, but I have found some of the comments very helpful so far in setting up Handvu, so I thought I would write about my issue. I am running Ubuntu 12.04 on a OMAP processor. I have gotten to the make step in the process and have changed all files as specified. However, I am having real issues with the FileHandling.cpp file during make. My original error was that sprintf was "out of scope", and I have tried many things from new header files to using snprintf to even trying to comment out large portions of the file which have all created additional errors. Has anyone dealt with this problem before? If not, could someone who has gotten the make to work post their version of the FileHandling.cpp file? I feel like I must be making some very minor but obvious mistake here.

---

