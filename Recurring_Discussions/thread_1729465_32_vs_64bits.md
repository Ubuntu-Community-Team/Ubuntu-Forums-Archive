---
title: "32 vs 64bits?"
date: 2011-04-15
forum: Recurring Discussions
---

### Post by zietbukuel on 2011-04-15
In the download page says that they recommend the 32bit distro, why is that? nowadays almost everyone has a 64 bit computer with multiple cores (at least 2). Can anyone care to explain why they recommend this over the 64bit version? Thanks.:confused:

---

### Post by jmd448 on 2011-04-15
alot of software is still 32 bit, also i believe the java virtual machine is 32 bit, though i dont think that matters, so things tend to run better in there native architecture/less pron to problems. This is changing but 64 is still not as fully supported as 32 bit is. I am not a computer scientist, unlike my roommate, this is simply from my own observations.

---

### Post by zietbukuel on 2011-04-15
Thanks, anyone else?

---

### Post by 3rdalbum on 2011-04-15
Flash on 64-bit doesn't work with webcams as far as I can tell, whereas on 32-bit it apparently works. 32-bit Debian packages don't "just install" on 64-bit.

But really, these are very weak reasons to recommend 32-bit over 64-bit. If you have a 64-bit capable computer, then just use 64-bit.

---

### Post by Vaphell on 2011-04-15
2 main reasons - hassle with some software (hi adobe and skype) and RAM (32bit supports natively up to 4GB though there are kernel versions that work around the issue, also 64bit pointers are bigger than 32bit pointers so machines with modest amounts of memory usually are better off with 32 bit system)

---

### Post by zietbukuel on 2011-04-15
I have a quad-core processor with 4gb Ram, does that make it "modest"?

---

### Post by mastablasta on 2011-04-15
no. go ahead with 64 bit. ;-)

---

### Post by wolfen69 on 2011-04-15
> **zietbukuel said:**
> I have a quad-core processor with 4gb Ram, does that make it "modest"?

You have plenty of computer to run 64bit. I've been using it for 2 years with no problems. ymmv.

---

### Post by Sef on 2011-04-15
Moved to Recurring Discussions.

---

### Post by NightwishFan on 2011-04-15
I say if you have a 64-bit processor use a 64-bit OS. Not even flash works poorly any more.

---

### Post by NMFTM on 2011-04-15
> **3rdalbum said:**
> Flash on 64-bit doesn't work with webcams as  far as I can tell, whereas on 32-bit it apparently works. 32-bit Debian  packages don't "just install" on 64-bit.
It'll often still install, you just have to use the  "--force-architecture" switch for Dpkg when installing a .deb package.

---

### Post by NightwishFan on 2011-04-15
> **NMFTM said:**
> It'll often still install, you just have to use the  "--force-architecture" switch for Dpkg when installing a .deb package.

I think multi-arch is planned for Debian Wheezy so soon this may not be a problem at all. (As Ubuntu is based on Debian)

---

### Post by K_45 on 2011-04-15
64-bit. RAM is very cheap right now for a new build:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145315](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145315)

This is like the Win 7 discussions you get. If you have a Pentium 4 and 512MB of RAM you want 32-bit. If you have a system that is even moderately modern (5 or 6 years old) you want 64-bit.

---

### Post by zietbukuel on 2011-04-15
Thanks a lot guys :)
I'm downloading the 64 bit version.

---

### Post by Paqman on 2011-04-15
The only reason they "recommend" 32-bit is that it's guaranteed to work on every system. There are still quite a few 32-bit machines out there (earlier Atom chips in netbooks, for example).

---

### Post by disabledaccount on 2011-04-15
64-bit? - most peoples don't know what does it really mean. It's not really faster (in most cases), uses more memory, needs faster RAM - because of improper use of int-type in most programs,  makes most processors slower - because of reducing internal pipelines efficiency. However 64-bit is unavoidable future - because next PC generations will handle 64bit with ease, providing performance boost as programmers would learn how to use "big integers" in structures.
Today, I would say that desktops should stay with 32-bit. Servers can take advantage of faster SSH/PGP/etc.

---

### Post by K_45 on 2011-04-15
> **tomazzi said:**
> 64-bit? - most peoples don't know what does it really mean. It's not really faster (in most cases), uses more memory, needs faster RAM - because of improper use of int-type in most programs,  makes most processors slower - because of reducing internal pipelines efficiency. However 64-bit is unavoidable future - because next PC generations will handle 64bit with ease, providing performance boost as programmers would learn how to use "big integers" in structures.
Today, I would say that desktops should stay with 32-bit. Servers can take advantage of faster SSH/PGP/etc.

Use more memory? Needs faster RAM? And this is based on - ?

---

### Post by disabledaccount on 2011-04-15
It's simple.
Faster RAM: standard Dual Channell reads 4 32-bit integers at once - but only 2 64bit integers
More memory: most compilers implements bool as int - so instead of wasting 31bits they will waste 63. Show me programmer who knows how to avoid this... - most of them just use bool-type. Int: in most operations programs can't efficienly use even 32-bit integers - but writing "int" is much easier than writting "union" :) And pointers are just black magic for most.

---

### Post by K_45 on 2011-04-15
> **tomazzi said:**
> It's simple.
Faster RAM: standard Dual Channell reads 4 32-bit integers at once - but only 2 64bit integers
More memory: most compilers implements bool as int - so instead of wasting 31bits they will waste 63. Show me programmer who knows how to avoid this... - most of them just use bool-type. Int: in most operations programs can't efficienly use even 32-bit integers - but writing "int" is much easier than writting "union" :) And pointers are just black magic for most.

But the difference would be negligible on day to day usage.

---

### Post by disabledaccount on 2011-04-15
Generally I would agree, but for example:
- Latitude E5500: Laptop, 32bit, Ubu10.04: <200MB RAM after booting
- MyDesktop: Ubu10.04 64bit: ~380MB after booting
(both with enabled compiz effects)

---

### Post by Simian Man on 2011-04-15
> **NightwishFan said:**
> I think multi-arch is planned for Debian Wheezy so soon this may not be a problem at all. (As Ubuntu is based on Debian)

> **NMFTM said:**
> It'll often still install, you just have to use the  "--force-architecture" switch for Dpkg when installing a .deb package.

Wow, and people still think RPM is a problem :shock:.  This "just works" with rpm/yum.

---

### Post by NightwishFan on 2011-04-15
> **Simian Man said:**
> Wow, and people still think RPM is a problem :shock:.  This "just works" with rpm/yum.

I am not sure why they would. In fact I really liked that feature when I used OpenSUSE. I still like debian base better though.


As for using more memory, certainly. If you have under 1gb I would not use 64-bit unless you plan on using a lightweight desktop. 64-bit Firefox (even optimised for size) happily takes up around 150-200mb. Opera? 600 or so. :) The rule of thumb is, if you have free RAM you have enough ram though.

---

### Post by handy on 2011-04-15
I didn't bother reading this thread, so sorry if someone has already posted this link on the thread title topic:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by aguafina on 2011-04-15
> **handy said:**
> I didn't bother reading this thread, so sorry if someone has already posted this link on the thread title topic:

[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)


Wow  seems 64b is winner by some distance.

---

### Post by wolfen69 on 2011-04-15
> **K_45 said:**
> Use more memory? Needs faster RAM? And this is based on - ?

Actually it does use a bit more ram than 32. However, I'm in the camp that thinks that memory should be used and not saved for a rainy day. And no, you don't need faster ram.

---

### Post by K_45 on 2011-04-16
> **tomazzi said:**
> Generally I would agree, but for example:
- Latitude E5500: Laptop, 32bit, Ubu10.04: <200MB RAM after booting
- MyDesktop: Ubu10.04 64bit: ~380MB after booting
(both with enabled compiz effects)
 
Ok, but that isn't that much if you have 4GB under 64-bit, which is when you'd be running it. Still pretty negligible.

---

### Post by linuxmaniack on 2011-04-16
Maybe they haven't updated it yet!
But it may be that pc's that are 32 bit, wont run 64, and dummies at computers wont know if there CPU is 32 or 64, so they recommend it so dummies don't start getting confused and they wont ring tech support and start paying money as they got no idea on what is 32 bit and 64 bit!

---

### Post by BlacqWolf on 2011-04-16
I prefer 64-bit. It offers a bit more speed in my opinion, as well as it will offer support for the next-gen software which may be only written in 64-bit (or 64-bit to 128-bit in the future). 

But the reason the Ubuntu website suggests 32-bit is because Linux doesn't have a way to use 32-bit software in 64-bit installations, unless the architecture of the app is actually x86_x64, as well as some people may be unaware of what 32 or 64-bit is and may try the 64-bit edition even though it's not compatible.

(and how about adding a poll to the thread to see which of the Ubuntu Forums users have either a 32- or 64-bit edition?)

---

### Post by Simian Man on 2011-04-16
> **BlacqWolf said:**
> But the reason the Ubuntu website suggests 32-bit is because Linux doesn't have a way to use 32-bit software in 64-bit installations, unless the architecture of the app is actually x86_x64, as well as some people may be unaware of what 32 or 64-bit is and may try the 64-bit edition even though it's not compatible.

That's not true.  On Fedora, if you install a 32-bit package on a 64-bit machine, it will pull in any 32 bit libraries needed and install just fine.  This is just a defficiency in Debian packaging.

---

### Post by NightwishFan on 2011-04-16
> **Simian Man said:**
> That's not true.  On Fedora, if you install a 32-bit package on a 64-bit machine, it will pull in any 32 bit libraries needed and install just fine.  This is just a defficiency in Debian packaging.

As I said, its a big goal for Debian 7 and progress looks optimistic. ;)

---

### Post by oldos2er on 2011-04-16
> **BlacqWolf said:**
> But the reason the Ubuntu website suggests 32-bit is because Linux doesn't have a way to use 32-bit software in 64-bit installations, 

That reason was never given AFAIK, see [https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

Besides, ia32-libs works just fine.

---

