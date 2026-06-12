---
title: "implicit declaration of function ‘memcpy’..."
date: 2008-04-23
forum: Packaging and Compiling Programs
---

### Post by zka on 2008-04-23
/fe$ make
gcc -g -Wall -Werror -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DAUTOCONF=1 -DTMPDIR=\"/tmp\" -DHAVE_LIBM=1 -DHAVE_LIBNSL=1 -DHAVE_INET_ATON=1    -c -o fe_forward.o fe_forward.c
cc1: warnings being treated as errors
fe_forward.c: In function ‘fe_process’:
fe_forward.c:160: warning: implicit declaration of function ‘memcpy’
fe_forward.c:160: warning: incompatible implicit declaration of built-in function ‘memcpy’
fe_forward.c:162: warning: implicit declaration of function ‘ntohs’
make: *** [fe_forward.o] Error 1


Ok.. i googled around and still dont get it. It seems I need to do something to my ubuntu hardy installation in order to get it to work. The solution that was posted on some forums is to install build-esential which i already have ! 

Other solution is to use #include <string.h> in order to fix the memcpy error, but I cant find how to fix the ntohs one as I dont know what header to include plus that i plan on adding other functions too like htonl etc..


So.. what do I need to do ? It is worth mentioning that the code works perfectly on my uni solaris machines but not on my laptop....

I would really prefer the real fix by letting my ubuntu know what stuff to use (so that it will work without me adding any headers). 


Help please !

PS: Just started using ubuntu few weeks ago so please make it simple...

Have succesfully installed gcc 4.2, build essential and maybe some other packages that came with codeblocks (note that i am not using codeblocks to try to run or write code for this program as it requires to cat> some files sa input which makes me use the terminal etc..)

---

### Post by gug@fnal.gov on 2008-04-23
Hi,
   Try looking in the man pages for htonl, for example. I am not at my Ubunto system but according to the man pages on RHEL the proper include file is:
 #include <netinet/in.h>

---

### Post by bite on 2008-04-23
> **zka said:**
> /fe$ make
gcc -g -Wall -Werror -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DAUTOCONF=1 -DTMPDIR=\"/tmp\" -DHAVE_LIBM=1 -DHAVE_LIBNSL=1 -DHAVE_INET_ATON=1    -c -o fe_forward.o fe_forward.c
cc1: warnings being treated as errors
fe_forward.c: In function ‘fe_process’:
fe_forward.c:160: warning: implicit declaration of function ‘memcpy’
fe_forward.c:160: warning: incompatible implicit declaration of built-in function ‘memcpy’
fe_forward.c:162: warning: implicit declaration of function ‘ntohs’
make: *** [fe_forward.o] Error 1


Ok.. i googled around and still dont get it. It seems I need to do something to my ubuntu hardy installation in order to get it to work. The solution that was posted on some forums is to install build-esential which i already have ! 

Other solution is to use #include <string.h> in order to fix the memcpy error,


correct

> 
 but I cant find how to fix the ntohs one


#include <arpa/inet.h>

>  as I dont know what header to include plus that i plan on adding other functions too like htonl


#include <arpa/inet.h>

>  etc..


So.. what do I need to do ? It is worth mentioning that the code works perfectly on my uni solaris machines but not on my laptop....

I would really prefer the real fix by letting my ubuntu know what stuff to use (so that it will work without me adding any headers). 


the "real fix" is to include what needs to be included.

> 

Help please !

PS: Just started using ubuntu few weeks ago so please make it simple...

Have succesfully installed gcc 4.2, build essential and maybe some other packages that came with codeblocks (note that i am not using codeblocks to try to run or write code for this program as it requires to cat> some files sa input which makes me use the terminal etc..)

---

### Post by zka on 2008-04-23
Damn that was fast ! I'll be sure to try that right now..

One question still remains.. Why do I need to add those headers while the program compiles and works on the solaris machines....?

---

### Post by bite on 2008-04-23
> **zka said:**
> Damn that was fast ! I'll be sure to try that right now..

One question still remains.. Why do I need to add those headers while the program compiles and works on the solaris machines....?

Probably on solaris the necessary headers are already available through other headers.

---

### Post by zka on 2008-04-23
That would explain it then. Just tried adding the necessary headers  and it works like a charm...

Thanks for the fast and accurate posts ! You are the best =)

---

### Post by PypeBros on 2008-04-24
generally, you can tell which include file contain prototype for which function by invoking the manpage of that function.

e.g. man -S2 memcpy revealed:
```

NAME
       memcpy - copy memory area

SYNOPSIS
       #include <string.h>

       void *memcpy(void *dest, const void *src, size_t n);

```

(oh, you might need to install manpages-dev and manpages-posix-dev for this to work properly, of course ;) )

---

### Post by zka on 2008-04-24
Ok going to do that right now. That will save me some time in the future when programming on my new laptop. Thanks again for all the answers!

---

### Post by chrl.boss on 2008-04-24
Hello Everyone,

If you are looking for really cheap hosting, you might take a look at
[http://www.webhosting-rated.com](http://www.webhosting-rated.com)

Thanks,
Charlie.

---

### Post by bite on 2008-04-24
> **chrl.boss said:**
> Hello Everyone,

If you are looking for really cheap hosting, you might take a look at
[http://www.webhosting-rated.com](http://www.webhosting-rated.com)

Thanks,
Charlie.

No, I'm not. And I reported this disturbing spam.

---

### Post by inkpen on 2011-09-26
Appears that Ubuntu has changed <strings.h> to <string.h>, any reason why?

> **PypeBros said:**
> generally, you can tell which include file contain prototype for which function by invoking the manpage of that function.

e.g. man -S2 memcpy revealed:
```

NAME
       memcpy - copy memory area

SYNOPSIS
       #include <string.h>

       void *memcpy(void *dest, const void *src, size_t n);

```(oh, you might need to install manpages-dev and manpages-posix-dev for this to work properly, of course ;) )

---

### Post by Bachstelze on 2011-09-26
Uh, it has always been string.h...

---

### Post by bite on 2011-09-27
> **inkpen said:**
> Appears that Ubuntu has changed <strings.h> to <string.h>, any reason why?

They are two different headers.

---

### Post by inkpen on 2011-09-27
> **Bachstelze said:**
> Uh, it has always been string.h...

Well, I was reading this thread because I pulled some code out to  compile on my brand spank'n new ubuntu install.  The problem is that the  gcc compiler that comes with ubuntu doesn't support strings.h, which is  a superset of string.h.  

After some further research, the gcc complier (as well as the windows  compiler) that I used a couple years ago did.  Turns out that strings.h  is a BSD branch of the UNIX evolutionary chain.  Everybody (well, at  least I did) that learned on UNIX uses strings.h.  Seems that everything  has been standardized by POSIX and some of the strings.h functionality  has been lost, while other functionality has been given another name  (e.g. bcmp ==> memcmp)...  At least that is my perspective on it...  :)

---

### Post by Bachstelze on 2011-09-27
> **inkpen said:**
>  The problem is that the  gcc compiler that comes with ubuntu doesn't support strings.h, which is  a superset of string.h.  


Define "support", because strings.h is certainly there.

[http://packages.ubuntu.com/search?searchon=contents&keywords=strings.h&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=strings.h&mode=exactfilename&suite=natty&arch=any)

But it is non-standard, so probably shouldn't be relied on if you can avoid it.

---

### Post by inkpen on 2011-09-28
> **Bachstelze said:**
> Define "support", because strings.h is certainly there.

[http://packages.ubuntu.com/search?searchon=contents&keywords=strings.h&mode=exactfilename&suite=natty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=strings.h&mode=exactfilename&suite=natty&arch=any)

But it is non-standard, so probably shouldn't be relied on if you can avoid it.

I was just bringing this up because the original thread was from a guy that had the  problem that I did... for some reason, code that compiles on older platforms using strings.h no longer works the same way, and you need to change it to string.h (for memcpy).

---

