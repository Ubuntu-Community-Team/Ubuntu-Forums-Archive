---
title: "Compiling error 'strlen' was not declared in this scope"
date: 2010-06-19
forum: Packaging and Compiling Programs
---

### Post by royevans on 2010-06-19
So I found out about Makehuman two days ago and thought how much this would help me with making models and the like, so I install the 1.0 Alpha 5 build (deb) and all was working fine until I tried to import a dae from MH to blender I keep getting this Python script error, so I try the mhx format from MH and it works, but, BAM, no edit mode. So I look around for tuts on how to fix these errors, but, none of them have anything to do with my problem at all so I decide to go back to a version that has been tested and that was 0.9.1 rc1. But here, I have to say, google failed be, I have honestly googled the mess out of my computer, here is the error I get ```
make[2]: Entering directory `/home/anon/Desktop/animorph-0.3/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -I..    -Wall -g -O2 -MT BodySettings.lo -MD -MP -MF .deps/BodySettings.Tpo -c -o BodySettings.lo BodySettings.cpp
 g++ -DHAVE_CONFIG_H -I. -I.. -Wall -g -O2 -MT BodySettings.lo -MD -MP -MF .deps/BodySettings.Tpo -c BodySettings.cpp  -fPIC -DPIC -o .libs/BodySettings.o
BodySettings.cpp: In member function 'void Animorph::BodySettings::fromStream(std::ifstream&)':
BodySettings.cpp:54: error: 'strlen' was not declared in this scope
make[2]: *** [BodySettings.lo] Error 1
make[2]: Leaving directory `/home/anon/Desktop/animorph-0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/anon/Desktop/animorph-0.3'
make: *** [all] Error 2

```
What I did was look for ```
'strlen' was not declared in this scope
``` but to no avail then I looked for ```
BodySettings.cpp:54: error: 'strlen' was not declared in this scope
``` and again nothing, the closest I got to solving this problem was [this link](http://www.makehuman.org/forum/viewtopic.php?f=3&t=207&p=868) which led me to [this link](http://gcc.gnu.org/gcc-4.3/porting_to.html) but the first one does not, to my knowledge, explain *how*, as in what has to be done in the terminal or folder, to get past this. I have been trying to compile this for four days, all the while googling the problem and trying different links but most don't even get a response (others that had this problem and posted) and the ones that do  are ***way*** above my current level of understanding of ubuntu. It's not through lack of trying that I am not able to understand it just is not clicking *what* it is I have to do. Any help would be ***greatly*** appreciated.

---

### Post by SevenMachines on 2010-06-20
have you tried adding 
#include <cstring> 
to the .cpp file? sounds like its missing that header

---

### Post by SevenMachines on 2010-06-20
actually having a look at makehuman, it seems there is .deb files for ubuntu to download and even a repository you can add. Unless you are really keen on compiling it yourself, using the repository would seem to be a good idea

---

### Post by royevans on 2010-06-20
> have you tried adding 
#include <cstring> 
to the .cpp file? sounds like its missing that header

Now when you say that, do you mean all thirty-five of them or just one specific one?
*I just looked at the error again and I see "BodySettings.cpp" I am going to try that.
**Thanks, it gets me past that but then I run into this error ```
In file included from VertexVector.cpp:2:
../include/animorph/util.h: In function 'void Animorph::stringTokeni(const std::string&, const std::string&, T&)':
../include/animorph/util.h:169: error: 'atoi' is not a member of 'std'
../include/animorph/util.h:174: error: 'atoi' is not a member of 'std'
make[2]: *** [VertexVector.lo] Error 1
make[2]: Leaving directory `/home/anon/Desktop/animorph-0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/anon/Desktop/animorph-0.3'
make: *** [all] Error 2

```

> **SevenMachines said:**
> actually having a look at makehuman, it seems there is .deb files for ubuntu to download and even a repository you can add. Unless you are really keen on compiling it yourself, using the repository would seem to be a good idea

I have tried the 1.0 Alpha X Makehuman debs as well as the 9.0 deb but none of them work how other's work, the Collada export always errors out but I figured out the one I have yet to try was the 9.1 rc1 version which is the one that many many MANY tutorials use.

---

### Post by SevenMachines on 2010-06-20
util.h needs
#include <cstdlib>

---

### Post by royevans on 2010-06-20
> **SevenMachines said:**
> util.h needs
#include <cstdlib>

This is indeed get me past my little problem, thank you, however, i decided to grow some balls and try the nightly build along with the 2.5 Alpha of blender, which works like a charm. I will move this thread to solved.

---

### Post by OpenMinded on 2011-08-24
> **royevans said:**
> This is indeed get me past my little problem, thank you, however, i decided to grow some balls and try the nightly build along with the 2.5 Alpha of blender, which works like a charm. I will move this thread to solved.

What fixed it for me was adding include "string.h" in the files the error occured.
In my case that was disco-matic .

---

