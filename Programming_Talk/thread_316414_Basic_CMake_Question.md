---
title: "Basic C/Make Question"
date: 2006-12-10
forum: Programming Talk
---

### Post by 64mgb on 2006-12-10
I'm a geek, but I've always been a Delphi guy, and in the last 8 or 9 years I've been doing ABAP (SAP).  I have dabbled with C a couple of times, but never really got into it.  So, if this question seems too basic, that's why.

I'm trying to tinker with some source code to see if I can get my Diamond PVR-560 tv card to work with ivtv.  When I do a 'make' from the ivtv-0.7.2 directory, it runs for a while, but then it starts spitting out errors:

ivtvctl.c:22:20: error: unitstd.h: No such file or directory
ivtvctl.c:23:78: error: features.h: No such file or directory

and many more.  In ivtvctl.c there are includes:
#include <unistd.h>
#include <features.h>
etc...

I assume that the brackets (<...>) mean "go look in the includes directory to find unistd.h".  My question is, how do I find out what this is set to?  How does it get set?  How do I change it?  And as a side question (I don't really expect an answer because you have no way of knowing what I've done) how did it get changed?  I used to be able to compile this.


Thanks!
Rich

---

### Post by tuxcantfly on 2006-12-10
unitstd.h and features.h are apparently Delphi-specific files. Maybe try removing the lines

#include <unistd.h>
#include <features.h>

hopefully, you didn't use too many Delphi-specific functions

---

### Post by bukwirm on 2006-12-10
Did you install the build-essential package? It is needed to compile programs.

unistd.h contains standard Unix functions
features.h appears to contain stuff used to enable various features

---

### Post by duff on 2006-12-10
> **64mgb said:**
> 
I assume that the brackets (<...>) mean "go look in the includes directory to find unistd.h". yes
>  My question is, how do I find out what this is set to?  Use the "-v" parameter when you compile (gcc -v foo.c) and look for **#include <...> search starts here:**
>  How does it get set? the compiler has some default ones it uses
>   How do I change it?  With the **-I** parameter. >  And as a side question (I don't really expect an answer because you have no way of knowing what I've done) how did it get changed?  I used to be able to compile this. have you tried making sure those files are there? ```
# locate unistd.h
# locate features.h
``` should show they are in /usr/include.

---

### Post by 64mgb on 2006-12-10
Thanks guys...these are not Delphi includes.  ivtvctl.c is exactly as I found it, so these are all unix includes.  And it's not just unistd and features...they were just examples.  And yes, those files exist...they are in many places, but I think the location that the program should be looking for them is either /usr/src/linux-headers-2.6.17-10/include/linux or /usr/include.

> **bukwirm said:**
> Did you install the build-essential package? It is needed to compile programs.

unistd.h contains standard Unix functions
features.h appears to contain stuff used to enable various features
I think this might be the answer...I am writing a how-to for myself so I can try some things and can document what I've done so I can re-do it, and this is the step I don't have in my how-to.  I knew it was necessary, but overlooked it.  I'll give it a try and let you know.

Thanks,
Rich

---

### Post by 64mgb on 2006-12-10
Rats...same thing  :( 

Rich

---

### Post by 64mgb on 2006-12-12
Just a quick update on this.  I ended up starting over from scratch (luckily I'm doing this on a test box) because somewhere along the line I moved or deleted the files that were in /usr/include, which is where gcc was looking for the includes.  I guess I shouldn't do this stuff while I'm drinking beer.  LOL

Rich

---

### Post by syklops on 2006-12-13
Hi,

I too have a basic C question. Can someone help?

Below is code that I wrote today. It takes a number from the command line, and checks if that number is 9 or is it 10, and if it is neither it says it was neither. Please ignore the daft sounding concept, its purpose is for something slightly different.

The problem is, it seems argv[1] is returning the number of arguments, not the value of the argument. When I compile and run it, I get 

"you didnt enter 9 or 10, you entered 2". 

if i give it 2 arguments it says I entered 3 and so on.

Any one any ideas?

<--- code follows -->

#include <stdio.h>
#include <stdlib.h>

main( int num, int argc, char *argv[])
{
        argv[1] = (char *) &num;
        if ( num == 9)
        printf("you entered number 9\n");
        else if ( num == 10)
        printf("you entered number 10\n");
        else
        printf("you didnt enter 9 or 10, you entered %d\n", num);

}

---

### Post by superm1 on 2006-12-15
> **64mgb said:**
> Just a quick update on this.  I ended up starting over from scratch (luckily I'm doing this on a test box) because somewhere along the line I moved or deleted the files that were in /usr/include, which is where gcc was looking for the includes.  I guess I shouldn't do this stuff while I'm drinking beer.  LOL

Rich

Probably a bit late, but you didn't have to compile all of ivtv from scratch..... There was a wiki page explaining how to use ivtv either in dapper or edgy:
[https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

---

### Post by rplantz on 2006-12-15
> **syklops said:**
> 

```

#include <stdio.h>
#include <stdlib.h>

main( int num, int argc, char *argv[])
{
        argv[1] = (char *) &num;
        if ( num == 9)
        printf("you entered number 9\n");
        else if ( num == 10)
        printf("you entered number 10\n");
        else
        printf("you didnt enter 9 or 10, you entered %d\n", num);

}
```

You cannot arbitrarily change the arguments to main(). The first one will be the number of arguments on the command line plus one for the command that launches your program. The fact that you call it "num" does not change that fact.

The second argument to main() will be a pointer to pointers to each of the (space delimited) words on the command line when you invoke your program.

You are missing an important concept here. The arguments on the command line are C-style text strings. For example, if you run your program with
```

myProg 9

```
the argument to your program is the string "9", not the number 9. You need to write the code to convert it to an int.

I recommend that you get a book like "Beginning Linux Programming" by Richard Stones and Neil Matthew (Wrox Press). Their explanations are pretty good, and their examples are quite practical (as opposed to theoretical).

---

### Post by jmc1024 on 2006-12-16
Try to find a C book.  I recommend C Primer Plus and the ANSI C books.  
See if you understand the changes I made.  If not reply directly and I'll
help.

Mark

#include <stdio.h>
#include <stdlib.h>

int main( int argc, char *argv[])
{
        int num = atoi(argv[1]);
        if ( num == 9)
        printf("you entered number 9\n");
        else if ( num == 10)
        printf("you entered number 10\n");
        else
        printf("you didnt enter 9 or 10, you entered %d\n", num);

}


> **syklops said:**
> Hi,

I too have a basic C question. Can someone help?

Below is code that I wrote today. It takes a number from the command line, and checks if that number is 9 or is it 10, and if it is neither it says it was neither. Please ignore the daft sounding concept, its purpose is for something slightly different.

The problem is, it seems argv[1] is returning the number of arguments, not the value of the argument. When I compile and run it, I get 

"you didnt enter 9 or 10, you entered 2". 

if i give it 2 arguments it says I entered 3 and so on.

Any one any ideas?

<--- code follows -->

#include <stdio.h>
#include <stdlib.h>

main( int num, int argc, char *argv[])
{
        argv[1] = (char *) &num;
        if ( num == 9)
        printf("you entered number 9\n");
        else if ( num == 10)
        printf("you entered number 10\n");
        else
        printf("you didnt enter 9 or 10, you entered %d\n", num);

}

---

### Post by syklops on 2006-12-27
Hi,

I was away for a bit and have just gotten a chance to reply now. Thanks for your help. I understand what you mean and believe I have fixed it. I will rewrite and see if it works. In the meantime I rewrote the program in perl, which worked fine.

Thanks for your help.

---

### Post by 64mgb on 2006-12-28
OK...I've gone way beyond my initial question...I've been doing a lot of tinkering trying to get a TV card to work with V4L and IVTV.  But now I can't figure out how to get past a kernel version problem.  When I try to 'make' in the V4L folder it wants to use /lib/modules/2.6.17-10-generic/build, but since I've recompiled the kernel I need it to use /lib/modules/2.6.17.14-ubuntu1/build.  How do I make 'make' understand this?

Here's what I mean:

rich@testbox:/usr/src/linux-headers-2.6.17.14-ubuntu1/v4l-dvb-kernel/v4l$ sudo make
creating symbolic links...
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/usr/src/linux-headers-2.6.17.14-ubuntu1/v4l-dvb-kernel/v4l  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [_module_/usr/src/linux-headers-2.6.17.14-ubuntu1/v4l-dvb-kernel/v4l]

Thanks,
Rich

---

### Post by superm1 on 2006-12-28
> **64mgb said:**
> OK...I've gone way beyond my initial question...I've been doing a lot of tinkering trying to get a TV card to work with V4L and IVTV.  But now I can't figure out how to get past a kernel version problem.  When I try to 'make' in the V4L folder it wants to use /lib/modules/2.6.17-10-generic/build, but since I've recompiled the kernel I need it to use /lib/modules/2.6.17.14-ubuntu1/build.  How do I make 'make' understand this?

Here's what I mean:

rich@testbox:/usr/src/linux-headers-2.6.17.14-ubuntu1/v4l-dvb-kernel/v4l$ sudo make
creating symbolic links...
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/usr/src/linux-headers-2.6.17.14-ubuntu1/v4l-dvb-kernel/v4l  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [_module_/usr/src/linux-headers-2.6.17.14-ubuntu1/v4l-dvb-kernel/v4l]

Thanks,
Rich
Do you need both v4l and ivtv?  Or are you just assuming v4l needs to be installed before ivtv?  If the latter, then don't do this.  follow the ivtv howto on [https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy).  If the former, then you will have some troubles building this and we will need to work through this.

---

### Post by 64mgb on 2006-12-28
Hi superm1 -

Yea, I need both.  I'm trying to get a Diamond PVR-560 card working.  It has an Xceive XC3028 tuner chip, which isn't supported in IVTV, but I've found some information ([http://www.gossamer-threads.com/lists/ivtv/devel/32112](http://www.gossamer-threads.com/lists/ivtv/devel/32112)) about how to make it work and it involves compiling against the V4L repository (I got that directly from Markus Rechberger).  I think I'm very, very close (FINALLY) to making this work, but am stuck on this version mismatch problem.

Thanks,
Rich

---

### Post by superm1 on 2006-12-29
> **64mgb said:**
> Hi superm1 -

Yea, I need both.  I'm trying to get a Diamond PVR-560 card working.  It has an Xceive XC3028 tuner chip, which isn't supported in IVTV, but I've found some information ([http://www.gossamer-threads.com/lists/ivtv/devel/32112](http://www.gossamer-threads.com/lists/ivtv/devel/32112)) about how to make it work and it involves compiling against the V4L repository (I got that directly from Markus Rechberger).  I think I'm very, very close (FINALLY) to making this work, but am stuck on this version mismatch problem.

Thanks,
Rich
Rich,
I did run across someone else that had to do something very similar to get a diamond card working.  I'm not sure if he ever managed though.
Basically, you won't be able to follow the exact build ubuntuish build process unless your very careful how you do things here (or you'll run into version mismatch problems like you hit or to unrecognized symbol problems).  It is probably easier at this point to ditch the ubuntu package for ivtv and do it from source since your already doing v4l from source, but i'll give you a rough idea of how it has to go if your interested:

1) Basically, say you have the headers in /usr/src/linux point to the headers for your running kernel.  You have to have the v4l sources here as well.  so if there is a directory in there that had tuner.h, but v4l sources had a newer one, you want v4l sources overwritting this.
2) After this is all setup, do the standard make, make install for v4l sources from /usr/src/linux
3) grab the source for ivtv
```
apt-get source ivtv-source
```4) install devscripts build-essential
```
apt-get install devscripts build-essential
```5) You will have to apply that patch inside this source directory
6) Bump debian/changelog by adding a new entry with an unofficial1 to the end of the version
```
dch -i
```
7) build the source package
```
debuild -S 
```
8) build binary package
```
sudo dpkg-buildpackage
```
9) install the source package and rebuild per the ivtv wiki page.

---

### Post by 64mgb on 2007-01-02
I finally found the solution to my version mismatch problem.  After a ton of tinkering and reading and researching, I found that the Makefile for the V4L tree has a rule called "release".  When I entered "make release 2.6.19.1" it created the proper environment for compiling for the 2.6.19.1 kernel.  Now I can compile V4L and IVTV and modprobe IVTV successfully, with no errors in dmesg!  Of course, my TV card still does not tune, but I'm (very slowly) getting there!

Rich

---

### Post by superm1 on 2007-01-02
> **64mgb said:**
> I finally found the solution to my version mismatch problem.  After a ton of tinkering and reading and researching, I found that the Makefile for the V4L tree has a rule called "release".  When I entered "make release 2.6.19.1" it created the proper environment for compiling for the 2.6.19.1 kernel.  Now I can compile V4L and IVTV and modprobe IVTV successfully, with no errors in dmesg!  Of course, my TV card still does not tune, but I'm (very slowly) getting there!

Rich
Keep a log of how you get this all together as you finally get this working.  I'm sure there are other people that will appreciate reading a wiki page explaining how to get this working once you get it :)

---

