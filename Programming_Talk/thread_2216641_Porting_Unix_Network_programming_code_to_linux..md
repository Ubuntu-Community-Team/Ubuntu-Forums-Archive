---
title: "Porting Unix Network programming code to linux."
date: 2014-04-13
forum: Programming Talk
---

### Post by kedarbhatia on 2014-04-13
Hello,

I was trying to get the R.stevens UNP code to run on linux machine. The code in the book has been run on UNIX/BSD variants.
I have tried to follow the instructions on[ ]("http://www.kegel.com/unpv1/")_[http://www.kegel.com/unpv1/](http://www.kegel.com/unpv1/)_

desktop:~/unpv12ep-0.2/unpv12e/server$ sh ../../test.sh 40000 3000
serv00 not found.  Are you in the right directory?

desktop:~/unpv12ep-0.2/unpv12e/server$ ls | grep serv00.c
serv00.c

Not sure why i see that altough the  serv00.c is present  in the directory.

I am running, Ubuntu 13.10.

Thank You.

---

### Post by CharlesA on 2014-04-13
Did you build the program before trying to run it?

---

### Post by dwhitney67 on 2014-04-13
> **kedarbhatia said:**
> Hello,
I have tried to follow the instructions on[ ]("http://www.kegel.com/unpv1/")_[http://www.kegel.com/unpv1/](http://www.kegel.com/unpv1/)_


Apparently you missed the step noted in **bold-text** below:
```

tar -xzvf unpv12ep-0.2.tar.gz
cd unpv12ep-0.2
**sh build.sh**
cd unpv12e/server
sh ../../test.sh PORT NITER
grep time *.out

```

Btw, I am not aware that Stevens' code will build on Linux.  Had he still been here amongst the living, I'm sure he would have updated his code base.  That being said, if you are not comfortable with C programming, then you might be disappointed that getting the programs to compile is not going to be a "walk in the park"... it will require some effort of understanding the differences between old-school Unix and Linux.

---

### Post by kedarbhatia on 2014-04-15
[@ [COLOR=#C61919]CharlesA[/COLOR]]("http://ubuntuforums.org/member.php?u=923868") I did tried compiling and i get lot of errors since we need to include UNP.h header. after includin the file i still get errors.

[**[COLOR=#000000]@dwhitney67[/COLOR]**]("http://ubuntuforums.org/member.php?u=322753") I think i missed putting that step up, i have tried all the steps  including 
**sh build.sh** in that sequence but still get the same result

I tried the steps given the README file ...but still get errors when i run make command..

I have attached the file.
================
In the README section of the attached file it is mentioned that the code has been successfully tested on 586- redhat 4.2  so i think it should port..

Appretiate the help..

---

### Post by dwhitney67 on 2014-04-15
> **kedarbhatia said:**
> [@ [COLOR=#C61919]CharlesA[/COLOR]]("http://ubuntuforums.org/member.php?u=923868") I did tried compiling and i get lot of errors since we need to include UNP.h header. after includin the file i still get errors.

[**[COLOR=#000000]@dwhitney67[/COLOR]**]("http://ubuntuforums.org/member.php?u=322753") I think i missed putting that step up, i have tried all the steps  including 
**sh build.sh** in that sequence but still get the same result

I tried the steps given the README file ...but still get errors when i run make command..

I have attached the file.
================
In the README section of the attached file it is mentioned that the code has been successfully tested on 586- redhat 4.2  so i think it should port..

Appretiate the help..

Besides trying to get the ancient Steven's code to build, what is your ultimate goal?  Would it not be better to write from scratch your own code, perhaps following a how-to type of guide?

IMHO, the Steven's book should only be used as a guide.  The s/w example libraries/examples are ancient -- and that being said -- they will NOT build under Linux.  You will either have to apply patches or make other changes to the build scripts, configure file(s) and/or source code to work around the problems.

If you download the [unpv12ep]("http://www.kegel.com/unpv1/unpv12ep-0.2.tar.gz") tar-ball package, it already contains some patches that will be helpful for Linux.  However, I found that they are incomplete.

I've included a tar-ball (with this post) that contains additional patches that should be copied to the unpv12ep-0.2 directory ***before*** you run the build.sh script.

YMMV depending on what you are attempting to accomplish with the unpv12ep library.  I was able to generate code using GCC 4.6.3 on my 64-bit Kubuntu 12.04 system.

P.S.  You should consider reading [Beej's Guide to Network Programming]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html").

---

### Post by kedarbhatia on 2014-04-17
I want to learn to network programming in general. I thought if i can get the code to compile i can understand the concepts better.
even with the patch files unable to get my code to run..
you are right, starting from scratch would be better..
i came across  [Beej's Guide to Network Programming]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html") yesterday...I see its more relavant to linux.
Once i am done with this guide ill go back to the UNP book as it is more indepth and covers protocols.

Thanks.

---

### Post by dwhitney67 on 2014-04-17
> **kedarbhatia said:**
> ...
i came across  [Beej's Guide to Network Programming]("http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html") yesterday...I see its more relavant to linux.
Once i am done with this guide ill go back to the UNP book as it is more indepth and covers protocols.

Thanks.

This is an excellent strategy, and one that I would wholeheartedly recommend.  Beej's Guide will start off simple, and keep it simple and entertaining.  Refer to the Stevens' book only for cases where esoteric information is needed (e.g. how to setup multicasting).

---

