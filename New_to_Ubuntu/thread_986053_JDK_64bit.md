---
title: "JDK 64bit"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by Pergi on 2008-11-18
Hello all, i want to install on my Ubuntu 8.04 Server 64bit, the JDK 64 bit.
I have already installed the jdk 32bit. I installed with:

```
sudo apt-get install sun-java6-jdk
```

So now, i am asking if there is a package that inculde the jdk 64bit or a method to upgrade it. I visited also the site of Sun, but i didnt find the binarie of JDK 64bit to download it and install it.

If you know something that will help, please post a reply. Thank you :)

---

### Post by ggaaron on 2008-11-18
Can't you use openjdk (the default)? I believe that it will be 64bit when installed on 64bit system.

---

### Post by kingtaurus on 2008-11-18
You can use:
```

sudo update-alternatives --config java

```
to switch between installed versions of jvm.

---

### Post by Pergi on 2008-11-21
I tried the command
```
sudo update-alternatives --config java
```
and the result is to see at terminal the following

```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          2    /usr/bin/cacao
          3    /usr/lib/jvm/java-6-sun/jre/bin/java
```

Ahm, is something from the 3 options the jdk 64bits? i dont think but you know better :)

---

### Post by muniak on 2008-11-21
Option 1 is openjdk, which should be 64.

---

### Post by Pergi on 2008-11-21
Yes ok, but the option 1 has the asterisk (*) so this means that this is the version that is currently running.
So i have a question regarding what ggaaron said. When someone is installing the jdk with the command
```
apt-get install sun-java6-jdk
```
it will install automatically the jdk 32bits if the OS is 32bits and 64bit version if the OS is 64bits?
I am sorry if i didnt understand right :/

---

### Post by ggaaron on 2008-11-21
There is ia32-sun-java6-bin package so version without ia32 should be 64bit.

---

### Post by Pergi on 2008-11-27
Thank you all for your replies. I will try it.

---

### Post by scorp123 on 2008-11-27
> **Pergi said:**
>  When someone is installing the jdk with the command
```
apt-get install sun-java6-jdk
```
it will install automatically the jdk 32bits if the OS is 32bits and 64bit version if the OS is 64bits? Yes. Blame Sun Microsystems. They stubbornly refuse to release their Java SDK (hence the name: "sun-java6-jdk") for 64-bit Linux. If you want to use 64-bit Sun Java you have to use Sun's "Solaris" operating system.

Sometime back in 2006 they promised they'd release a version for 64-bit Linux ... but 2008 is almost over, it's soon 2009 ... and still nothing.

So if you have a 64-bit Linux OS you either have to live with a 32-bit Sun JDK or you have to consider the alternatives, such as OpenJDK. The problem here is that not all apps will 100% run with OpenJDK; but for most stuff it should still be OK.

Also: Why even 64-bit OS? If all you care about is to have full access to RAM, then you could also enable "PAE" (Physical Address Extension) in your kernel. This would allow a 32-bit Kernel to see up to 64 GB of RAM. Or if you are lazy as me you simply install the kernel image of "Ubuntu Server" because that one already has PAE enabled per default: ```
sudo apt-get install linux-server
```

PAE has a small performance hit though, somewhere between 5% to 15% ... but with modern CPU's you should not feel or see anything.

---

### Post by ggaaron on 2008-11-27
Why 64 bit? Because we can=) I can ask you the same question the other way, why 32 bit? (or why not 16 bit?)
And don't accuse Sun, OpenJDK is official Sun project, so they provide version that you can install on 64 bit system. And also OpenJDK is 100% compatible with java specification.

---

### Post by scorp123 on 2008-11-27
> **ggaaron said:**
> Why 64 bit? Because we can =)  You misunderstood the question, obviously. Only few people will _really_ ever make use of the full potential 64-bit offers; for the rest 32-bit + PAE would be more than enough. 

> **ggaaron said:**
>  I can ask you the same question the other way, why 32 bit?  I have to work with commercial apps that only exist for 32-bit Linux as far as their Linux versions is concerned. The only 64-bit versions of these apps that exist are for commercial UNIX OS'es. And I don't feel like running a HP-UX machine or having Solaris 10 on my boxes when a 32-bit Linux with PAE could do the job just as well. ;)

> **ggaaron said:**
>  (or why not 16 bit?)  As a matter of fact I have some ancient Sun boxes here, I think they are 16-bit :D  But it's highly unlikely that any modern OS would boot on those things :)

> **ggaaron said:**
>  And don't accuse Sun  But I do :D  Because I know and because I can :D

> **ggaaron said:**
>  OpenJDK is official Sun project, so they provide version that you can install on 64 bit system.  Yeah great: a limited version that is. A version which is not 100% compatible to their closed-source "Sun Jave 6" release; hence many apps I happen to know will not work with OpenJDK. 

> **ggaaron said:**
>  And also OpenJDK is 100% compatible with java specification. See here and answer my question there:
[http://ubuntuforums.org/showthread.php?p=5995226](http://ubuntuforums.org/showthread.php?p=5995226)

So you have OpenJDK and a 64-bit Linux? Fine then, could you then please try out something for me? Go to this URL from Sun's web site and try if you can login and if you can open any apps:
[https://sgddemo.sun.com/](https://sgddemo.sun.com/)

For the record, that's just one of the commercial apps that I mentioned above and it's from Sun too ... and it's heavily Java based:

Sun Secure Global Desktop
[http://www.sun.com/software/products/sgd/index.jsp](http://www.sun.com/software/products/sgd/index.jsp)

And the funny thing is that it would not work with OpenJDK (which according to you is sponsored by Sun too?) when I tried.

But maybe things have changed? So please: can you please go to that URL and try it out?  I know that it works perfectly with Sun's Java (on 32-bit) .... But does it work too with OpenJDK and 64-bit? It did not when I tried a few weeks ago. But maybe there was an update? Can you try please and tell me? :)

---

### Post by ggaaron on 2008-11-27
> **scorp123 said:**
> You misunderstood the question, obviously. Only few people will _really_ ever make use of the full potential 64-bit offers; for the rest 32-bit + PAE would be more than enough. 

Anyone that would have a need for PAE would use 64bit's potential, from what you say it has a huge performance impact. But I will agree with you that boxes with less than 4GB of memory will probably not use much of 64bit advantages and certainly will hit higher memory usage disadvantage.
> **scorp123 said:**
> 
 Yeah great: a limited version that is. A version which is not 100% compatible to their closed-source "Sun Jave 6" release; hence many apps I happen to know will not work with OpenJDK. 

Sun released all the source code for their JDK they could and the rest was developed as icedtea project and this is what Ubuntu calls OpenJDK. It's not a limited version for sure, in fact it has even come upgrades (zero, shark). The problem may be 64bit browser plugin that doesn't work always from what I can tell. Because of issues with browser plugin I can't even run java test application, so your site doesn't work too, but if you have some not proprietary applications that I could download and test then give me a link.

---

### Post by scorp123 on 2008-11-27
> **ggaaron said:**
>  so your site doesn't work too **For me and most users this is precisely all that counts. It does not work.** And there are more examples where OpenJDK on 64-bit fails miserably. So I have to use Sun's original Java 6 SDK, I have to use their web-browser plugin, I have to use 32-bit. And if I have more than 4 GB RAM I have to use 32-bit + PAE. And the performance hit is not as dramatic as it might sound, it's negligible.

I am not saying "64-bit is bad" or something like that .... it's just that contrary to some of the claims one can read around the forums here it's not as "troublefree" as some people claim. What I am saying is "if you run into too much trouble: consider using 32-bit Linux with PAE". That's all. :)

---

### Post by ggaaron on 2008-11-27
> **scorp123 said:**
> **For me and most users this is precisely all that counts. It does not work.**
Unfortunately that is what most people are only interested about=(
For me it is trouble free - everything works as it would with 32bit.

---

### Post by scorp123 on 2008-11-27
> **ggaaron said:**
> For me it is trouble free - everything works as it would with 32bit. Lucky you. If I want all the stuff to work I am either stuck with 32-bit Linux and PAE (which basically is a "workaround") or I'd have to use a commercial UNIX variant ... they are tip top as server OS but as desktop OS they kinda suck :D

---

### Post by ggaaron on 2008-11-27
Solaris is going more desktop friendly. There should be a new release somewhere this month, I'm eager to see it, and it's free in both senses of the word.

---

### Post by scorp123 on 2008-11-27
> **ggaaron said:**
> Solaris is going more desktop friendly. I know. But the current "Solaris Express" releases (= the future Solaris 11) are not that super-duper stable. It's like a lottery ... build 98 was solid, build 99 was a pile of crap, build 100 was better but still shaky, build 101 looks pretty solid again ...

And OpenSolaris 2008.05 is nice, looks and feels like a Linux distro ... but some of the stuff I work with doesn't like OpenSolaris, e.g. there are too many things from Solaris missing .... so it's not an alternative for me either.

> **ggaaron said:**
>  There should be a new release somewhere this month Solaris 10 Update 6 got released end of October; but it's still Solaris 10. So I assume you can't mean that? Solaris "Express" gets released every Friday or so. The DVD releases are now at build 103 whereas the CD release is still at build 98.

---

### Post by ggaaron on 2008-11-27
I've meant opensolaris. I've tired it before an as you've said - things were missing and others were not working, I hope it will be better (at least usable) this time.

---

### Post by scorp123 on 2008-11-27
> **ggaaron said:**
> I've meant opensolaris.  Yes, OpenSolaris 2008.11 should be out now. Now that they finally have a package manager too I will try if I can upgrade my experimental 2008.05 installation to 2008.11 .... the GUI front-end pretty much looks and feels like Synaptic. Sometimes I wish they'd integrate that into their commercial Solaris 10 releases, that would be nice.

I guess we stop here, we're way too off-topic :D

---

### Post by scorp123 on 2008-12-17
Finally!!!

Sun has finally released a 64-bit Java Plugin :D
[https://jdk6.dev.java.net/6uNea.html](https://jdk6.dev.java.net/6uNea.html)

---

