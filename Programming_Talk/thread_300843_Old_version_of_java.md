---
title: "Old version of java"
date: 2006-11-16
forum: Programming Talk
---

### Post by Rindwind on 2006-11-16
Hi.

I was wondering if anyone out there have any experience with getting a older version of java(jdk1.2.2) to run on Dappler.

I've downloaded jdk1.2.2 from sun and extracted to /usr/local/sun-jdk1.2.2/

However running it gives this error:

tord@tord-linux:~$ /usr/local/sun-jdk1.2.2/bin/java -version
Can't load library "/usr/local/sun-jdk1.2.2/jre/lib/i386/libjava.so", because /usr/local/sun-jdk1.2.2/jre/lib/i386/libjava.so: symbol __libc_wait, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
Could not create the Java virtual machine.

/lib/libc.so.6 points to /lib/libc-2.3.6.so, so it appares to be a compatibility issue between the version of libc that it's compiled for an the currently installed version.

Blackdown's version of jdk1.2.2 seemes to have the same issue...

So... any suggestions on how to fix this compatibility issue(have already tried to installed the libstdc++2.10-glibc2.2 package with no result) or where to get a hold of a java-1.2 compiler that will work with current libc would be welcome..

---

### Post by hod139 on 2006-11-16
Can I ask why you want to install an older version?  Newer versions are faster, more secure, and have a larger standard library.  

Your old Java code "should" still build on a more recent version (albeit maybe with more warnings), and if it doesn't I would image an easy job to port the code.

So again, why would you want such an old version?

---

### Post by Rindwind on 2006-11-16
Short answer... cause I have to..

Longer version:
My code is a piece of an older (and very large) system that runs on 1.2 which uses various features no longer present or have been changed in the newer versions. Rewriting it all to java-1.5 which we use for new projects, would therefor require *alot* of work..

---

### Post by hod139 on 2006-11-16
I'm not sure about 1.2, but it may be possible to install 1.4 which should be more backwards compatible no?  Anyways, I guess I can't offer much.

---

### Post by shining on 2006-11-16
I thought that GNU java (gcj / gij) was installed by default, and actually, it doesn't even support java 5. Did you try it?

If it isn't installed, just do:
```

sudo apt-get install gij gcj

```

Then, if it's the only deb package providing java, you can just use javac and java.
If it isn't the only one, you need to do:
```

sudo update-alternatives --config java
sudo update-alternatives --config javac

```
and pick up GNU java.

---

### Post by Rindwind on 2006-11-17
Nope.. 1.4 is to new.. :)
Allready have gjc installed

---

### Post by shining on 2006-11-17
You could google for the error:
[http://www.google.fr/search?hl=fr&ie=UTF-8&oe=UTF-8&q=symbol+__libc_wait%2C+version+GLIBC_2.0+not+defined+in+file+libc.so.6+with+link+time+reference&btnG=Rechercher&meta=](http://www.google.fr/search?hl=fr&ie=UTF-8&oe=UTF-8&q=symbol+__libc_wait%2C+version+GLIBC_2.0+not+defined+in+file+libc.so.6+with+link+time+reference&btnG=Rechercher&meta=)

Here someone explains how sun java is broken:
[http://sources.redhat.com/ml/libc-alpha/2002-04/msg00145.html](http://sources.redhat.com/ml/libc-alpha/2002-04/msg00145.html)

There is a workaround that is found in several places that might fix it.
See "workaround for the buggy JVM" in the middle of this page:
[http://nextre.it/oracledocs/oracle9ionsles9amd64.html](http://nextre.it/oracledocs/oracle9ionsles9amd64.html)

By the way, aren't jdk backward compatible?
I joined it quite late, I only started learning java last year for school. We started with java 1.4, but also had an overview 1.5 changes, Our teacher said jdk 1.5 still supported 1.4 code. Maybe it's only between 2 consecutive releases?

---

### Post by David Mulligan on 2006-12-09
I had this problem too and managed to find the solution.

1) install package libstdc++2.10-glibc2.2
2) execute: sudo ln -s /usr/lib/libstdc++-libc6.2-2.so.3 /usr/lib/libstdc++-libc6.1-1.so.2
3) Grab libcwait.c and compile it as per the instructions at [IBM]("http://www-1.ibm.com/support/docview.wss?rs=463&context=SSKTMJ&dc=DB520&uid=swg21173500&loc=en_US&cs=UTF-8&lang=en&rss=ct463lotus")  The link in the article is broken but the contents of libcwait.c are included below.
4) execute: LD_PRELOAD=/usr/lib/libcwait.so;export LD_PRELOAD

I placed the LD_PRELOAD statement in my ~/.bash_profile script.  I assume there is a better place for it but it works for me.

Best of luck!
David 

PS - Some code depends on very specific versions of the JRE.  I am not talking about tiny applets or tiny applications like Azureus but rather mammoth multithreaded apps like application servers.

PPS - I love Azureus but relatively speaking it is tiny.

---

### Post by Rindwind on 2006-12-11
It did the trick.
Thanks.

---

