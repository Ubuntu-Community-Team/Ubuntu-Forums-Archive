---
title: "gcc or g++ installation based on arm"
date: 2012-07-30
forum: Programming Talk
---

### Post by pellyhawk on 2012-07-30
Hi everybody,

I am building a project which will be run based on arm chip(cross compiling). While running```
make
```, I got these result:```
arm-linux-g++ -O3 -o lcd_display draw.c baseFun.c lcd_display.c /lib/libparashmoper.so \
	 /lib/libtaskdaemon.so /lib/librtcso.so /lib/libshm_real.so /lib/libshm_his.so \
	 /lib/libshm_cmd.so /lib/libshm_event.so /lib/libcommonfunc.so
make: [COLOR="Red"]arm-linux-g++: Command not found[/COLOR]
make: *** [lcd_display] Error 127

```

It seems that arm-linux-g++ is not installed. How to deal with it since I do not know the package name? "sudo apt-intall arm-linux-g++"? And how to set environment variables?

By the way, I know gcc and g++ were both installed on Ubuntu. So perhaps arm-linux-gcc also need to be installed. Is it "sudo apt-install arm-linux-gcc" and how to set environment variables?

PS: While running "which arm-linux-g++" or "which arm-linux-gcc", I got nothing.

Thanks a lot.

---

### Post by spjackson on 2012-07-30
I haven't done this myself, but I have been thinking about it receently, and if I was going to, I think I'd be using qemu. [https://wiki.ubuntu.com/ARM/BuildArmPackages]("https://wiki.ubuntu.com/ARM/BuildArmPackages")

However, if you want to do it as a straight cross-compile, then I think you want either g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf depending on whether you want hard float or not.

You may also need binutils-arm-linux-gnueabi or binutils-arm-linux-gnueabihf, again depending on whether your floats are hard or soft ;-)

Maybe libraries too (libc6, stdc++ etc.), if these don't get installed by the above.

Fire up synaptic and search for arm.

Finally, if you do have the right packages installed, you may still need to set PATH in order for make to find the tools.

---

### Post by pellyhawk on 2012-07-30
> 
Fire up synaptic and search for arm.

Finally, if you do have the right packages installed, you may still need to set PATH in order for make to find the tools.

I fired up synaptic, searched for arm and got nothing about arm-linux-gcc/g++. Clearly, I had not got arm-linux-gcc or arm linux-g++ installed.

> However, if you want to do it as a straight cross-compile, then I think you want either g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf depending on whether you want hard float or not.

You may also need binutils-arm-linux-gnueabi or binutils-arm-linux-gnueabihf, again depending on whether your floats are hard or soft 

Maybe libraries too (libc6, stdc++ etc.), if these don't get installed by the above.From the result I put here before, arm-linux-g++/gcc is needed, why g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf is needed? And what is hard float and binutils-arm-linux-gnueabi or binutils-arm-linux-gnueabihf?

I am totally confused:confused:.

---

### Post by spjackson on 2012-07-31
> **pellyhawk said:**
> From the result I put here before, arm-linux-g++/gcc is needed, why g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf is needed? And what is hard float and binutils-arm-linux-gnueabi or binutils-arm-linux-gnueabihf?

I am totally confused:confused:.

I am sorry, I did not realise that you did not know anything about how Ubuntu/Debian packaging works. Let me explain. Sometimes the name of the package matches precisely the name of a program it provides, and sometimes it does not. For example, the ssh command is provided by the openssh-client package. Similarly, the package required for arm-linux-g++ isn't called arm-linux-g++, but it is one of g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf.

I have checked the dependencies for you [here]("http://packages.ubuntu.com/precise/gcc-4.4-arm-linux-gnueabi") and [here]("http://packages.ubuntu.com/precise/devel/g++-4.4-arm-linux-gnueabi"), and the appropriate binutils will be installed automatically when you install the compiler, so you won't have to worry about that. It includes programs such as the assembler and linker for the target architecture. The compiler package also depends on libc6 but the stdc++ library is only suggested.

As for hard float, it's to do with usage of the FPU (floating point unit) on newer ARM chips. See the section headed [Rationale here]("http://wiki.debian.org/ArmHardFloatPort/#Rationale") for details. Programs compiled for hard float will in general be faster but, as I understand it, will not run on older ARM chips.

I am not an expert in this area, and as I said, I haven't actually done it, so I could be wrong about some of the details, but hopefully this will guide you in the right direction.

---

### Post by pellyhawk on 2012-07-31
> **spjackson said:**
> 
However, if you want to do it as a straight cross-compile, then I think you want either g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf depending on whether you want hard float or not.

Thanks a lot.

sorry, what is hard float? Firstly, I am search for it by google. If you have some information about me, please tell me as well:wink:I found I almost know nothing about gcc related to arm. And gcc+ binutils + glibc + linux-header seems very unfamiliar for me:sad:. Too many things need to know.

---

### Post by spjackson on 2012-07-31
> **pellyhawk said:**
> 
sorry, what is hard float? Firstly, I am search for it by google. If you have some information about me, please tell me as well:wink:I found I almost know nothing about gcc related to arm. And gcc+ binutils + glibc + linux-header seems very unfamiliar for me:sad:. Too many things need to know.

As I wrote earlier:
> 
As for hard float, it's to do with usage of the FPU (floating point unit) on newer ARM chips. See the section headed [Rationale here]("http://wiki.debian.org/ArmHardFloatPort/#Rationale") for details. Programs compiled for hard float will in general be faster but, as I understand it, will not run on older ARM chips.

In the context of compiling for ARM, hard float means to generate machine code that carries out certain floating point operations directly in the hardware. So it depends which ARM chip or chips you want your code to run on. If in doubt, don't choose hard float. If you use the hard float toolset, then for some floating point operations the compiler will generate machine code to carry out the operation on the FPU. If the chip has no FPU, then this won't work. If you use the eabi toolset (not hard float) then for the same source code, different machine code will be generated that does not use the FPU - and this will work whether the chip has one or not.

---

### Post by trent.josephsen on 2012-07-31
Basically, some ARM chips have a built in floating point coprocessor. If the chip you're compiling for has one, then you can take advantage of it to make floating point calculations significantly faster. If the chip doesn't have one, then you have to emulate floating point operations in software, which is slow.

You need to use the hard float version of the compiler to take advantage of the hardware FPU, but if you don't have a hardware FPU then you won't be able to use the hard-float-compiled binaries at all. Probably.

---

### Post by pellyhawk on 2012-08-01
spjackson and trent.josephsen,

Many thanks for your patience. I have known some knowledge for your explanation.

I also read some other materials, especially "The GNU Toolchain for ARM targets HOWTO"([http://www.aleph1.co.uk/oldsite/armlinux/docs/toolchain/toolchHOWTO.pdf]("http://www.aleph1.co.uk/oldsite/armlinux/docs/toolchain/toolchHOWTO.pdf")). I knew there are some pre-built toolchain. It seems that a toolchain usually include gcc (which includes the C compiler and C++ compiler), binutils and glibc.

Is g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf a pre-built compiler? Is gcc-arm-linux-gnueabihf or gcc-arm-linux-gnueabi needed? (Usually, as for native compilers, gcc and g++ are both installed on Ubuntu)I searched for them and got many links([http://packages.ubuntu.com/search?keywords=gcc-arm-linux-gnueabi]("http://packages.ubuntu.com/search?keywords=gcc-arm-linux-gnueabi") and [http://packages.ubuntu.com/search?keywords=g%2B%2B-arm-linux-gnueabi]("http://packages.ubuntu.com/search?keywords=g%2B%2B-arm-linux-gnueabi")) and do not know which version I should use (natty, oneiric, precise, quantal? so many versions:confused:).

Many thanks.:wink:

---

### Post by spjackson on 2012-08-01
> **pellyhawk said:**
> 
Many thanks for your patience.

That's OK, but it is beginning to run out.
> 
I also read some other materials, especially "The GNU Toolchain for ARM targets HOWTO"([http://www.aleph1.co.uk/oldsite/armlinux/docs/toolchain/toolchHOWTO.pdf]("http://www.aleph1.co.uk/oldsite/armlinux/docs/toolchain/toolchHOWTO.pdf")).

That link gives me an "Object not found!" page.
> 
I knew there are some pre-built toolchain. It seems that a toolchain usually include gcc (which includes the C compiler and C++ compiler), binutils and glibc.

The 2 toolchains (one for eabi and one for hf) are provided by the packages I have already told you about.

> 
Is g++-arm-linux-gnueabi or g++-arm-linux-gnueabihf a pre-built compiler?

These packages both provide a pre-built compiler. They also contain dependencies which will result in the rest of the (pre-built) toolchain being installed, with the caveat that (pre-built) libstdc++ is optional - you may possibly have to install that separately.

> 
 Is gcc-arm-linux-gnueabihf or gcc-arm-linux-gnueabi needed? 

Yes. Which one? I don't know. This is your decision. I have tried to explain what you need to take into consideration when making that decision, I don't know what more you want me to say about that.

Do you have access to a computer on which you are going to run the executable when you have built it? Do you know what operating system it is using?

I have one ARM system available (besides mobile phones). I'll log into it and have a look.
```

pi@raspberrypi ~ $ ldd /bin/ls
        /usr/lib/arm-linux-gnueabihf/libcofi_rpi.so (0x40176000)
        libselinux.so.1 => /lib/arm-linux-gnueabihf/libselinux.so.1 (0x400c0000)
        librt.so.1 => /lib/arm-linux-gnueabihf/librt.so.1 (0x400a5000)
        libacl.so.1 => /lib/arm-linux-gnueabihf/libacl.so.1 (0x400e3000)
        libgcc_s.so.1 => /lib/arm-linux-gnueabihf/libgcc_s.so.1 (0x40007000)
        libc.so.6 => /lib/arm-linux-gnueabihf/libc.so.6 (0x4017f000)
        /lib/arm-linux-gnueabihf/ld-linux.so.3 => /lib/ld-linux-armhf.so.3 (0x4007e000)
        libdl.so.2 => /lib/arm-linux-gnueabihf/libdl.so.2 (0x400f3000)
        libpthread.so.0 => /lib/arm-linux-gnueabihf/libpthread.so.0 (0x40058000)
        libattr.so.1 => /lib/arm-linux-gnueabihf/libattr.so.1 (0x400fe000)

```
/lib/arm-linux-gnueabihf auggests to me that if I was trying to install a cross compiler in the way you are doing, I would choose gnueabihf (hard float). Except I didn't really need to do that because I already know that it's running a hard float build of debian wheezy. But I do not know whether that will be the right decision for you.

> 
and do not know which version I should use (natty, oneiric, precise, quantal? so many versions:confused:).

Do you know which version of Ubuntu you are running? You want the package for that version. "apt-get install..." will get you the right one.

Incidentally, if you ever get a toolchain installed, do you know what all those shared libraries are in your original post? Do you have them? Hopefully they are not in /lib.

---

### Post by pellyhawk on 2012-08-02
> **spjackson said:**
> 
That link gives me an "Object not found!" page.

Yes, I tried it and got the same feedback. Maybe this server has something 
wrong. I will upload it.

> Quote:
Is gcc-arm-linux-gnueabihf or gcc-arm-linux-gnueabi needed?
[COLOR="Red"]Yes[/COLOR]. Which one? I don't know. This is your decision. I 
have tried to explain what you need to take into consideration when making 
that decision, I don't know what more you want me to say about that.

I have read what you have explained and decided to chose [COLOR="Red"]g++[/COLOR]-arm-linux-gnueabi because I cannot confirm my arm chip has FPU. I only do not know whether [COLOR="Red"]gcc[/COLOR]-arm-linux-gnueabi is need as well. You have told me "Yes":)

> Do you have access to a computer on which you are going to run the executable when you have built it? Do you know what operating system it is using?

Yes, I have a PC on which I installed VMWare Ubuntu 10.04 and decide to install GNU toolchain for ARM targets.

I logged into my arm linux and got:

```
~ # [COLOR="Red"]uname -a
Linux (none) 2.6.25 #148 Thu May 5 07:53:58 EDT 2011 armv5tejl unknown[/COLOR]
~ # cd
~ # pwd
/root
~ # ldd /bin/ls
[COLOR="Red"]-ash: ldd: not found[/COLOR]
~ # cd /bin
/bin # ls
ash       date      hostname  kill      more      pwd       touch
busybox   dd        ip        ln        mount     rm        true
cat       df        ipaddr    login     mv        rmdir     umount
chgrp     dmesg     ipcalc    ls        netstat   sh        uname
chmod     echo      iplink    mkdir     pidof     sleep     usleep
chown     false     iproute   mknod     ping      sync      vi
cp        gzip      iptunnel  mktemp    ps        tar
/bin # ls -l
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ash -> busybox
-rwxr-xr-x    1 root     root       389052 Sep 27  2009 busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 cat -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 chgrp -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 chmod -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 chown -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 cp -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 date -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 dd -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 df -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 dmesg -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 echo -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 false -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 gzip -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 hostname -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ip -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ipaddr -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ipcalc -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 iplink -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 iproute -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 iptunnel -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 kill -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ln -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 login -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ls -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 mkdir -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 mknod -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 mktemp -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 more -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 mount -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 mv -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 netstat -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 pidof -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ping -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 ps -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 pwd -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 rm -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 rmdir -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 sh -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 sleep -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 sync -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 tar -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 touch -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 true -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 umount -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 uname -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 usleep -> busybox
lrwxrwxrwx    1 root     root            7 Sep 27  2009 vi -> busybox
```

It seems that command "ldd" is not supported.:(

> /lib/arm-linux-gnueabihf auggests to me that if I was trying to install a cross compiler in the way you are doing, I would choose gnueabihf (hard float). Except I didn't really need to do that because I already know that it's running a hard float build of debian wheezy. But I do not know whether that will be the right decision for you.

Quote:
and do not know which version I should use (natty, oneiric, precise, quantal? so many versions). Do you know which version of Ubuntu you are running? You want the package for that version. "apt-get install..." will get you the right one.

Since command "ldd" is not supported, I will choose gnueabi.

I am running Ubuntu 10.04 and I wonder whether you advise me to type:
```
sudo apt-get install gcc-arm-linux-gnueabi g++-arm-linux-gnueabi
```

or
```

sudo apt-get install gcc-arm-linux-gnueabi
sudo apt-get install g++-arm-linux-gnueabi

```

And the "apt-get install ..." will get the right one chosen from versions of natty, oneiric, precise, quantal. 
[http://packages.ubuntu.com/search?keywords=gcc-arm-linux-gnueabi]("http://packages.ubuntu.com/search?keywords=gcc-arm-linux-gnueabi") and [http://packages.ubuntu.com/search?keywords=g%2B%2B-arm-linux-gnueabi]("http://packages.ubuntu.com/search?keywords=g%2B%2B-arm-linux-gnueabi")

> Package [COLOR="Red"]gcc-arm-linux-gnueabi[/COLOR]
[COLOR="Red"]natty (devel)[/COLOR]: The GNU C compiler for armel architecture [universe] 
4:4.5.2-8: [COLOR="red"]amd64 i386[/COLOR]
[COLOR="red"]oneiric (devel)[/COLOR]: The GNU C compiler for armel architecture [universe] 
4:4.6.0-8: [COLOR="red"]amd64 i386[/COLOR]
[COLOR="red"]precise (devel)[/COLOR]: The GNU C compiler for armel architecture [universe] 
4:4.6.2-7: [COLOR="red"]amd64 i386[/COLOR]
[COLOR="red"]quantal (devel)[/COLOR]: The GNU C compiler for armel architecture [universe] 
4:4.7.0-7: [COLOR="red"]amd64 i386[/COLOR]

> Package [COLOR="red"]g++-arm-linux-gnueabi[/COLOR]
[COLOR="red"]natty (devel)[/COLOR]: The GNU C++ compiler for armel architecture [universe] 
4:4.5.2-8: [COLOR="red"]amd64 i386[/COLOR]
[COLOR="red"]oneiric (devel)[/COLOR]: The GNU C++ compiler for armel architecture [universe] 
4:4.6.0-8: [COLOR="red"]amd64 i386[/COLOR]
[COLOR="red"]precise (devel)[/COLOR]: The GNU C++ compiler for armel architecture [universe] 
4:4.6.2-7: [COLOR="red"]amd64 i386[/COLOR]
[COLOR="red"]quantal (devel)[/COLOR]: The GNU C++ compiler for armel architecture [universe] 
4:4.7.0-7: [COLOR="red"]amd64 i386[/COLOR] 

(amd64, very strange, while mine is 32-bit. I do not care it, for you told me apt-get will choose the right one for me)

My arm chip is AT91SAM9260B-CU ([URL="http://www.atmel.com/Images/6221s.pdf"]
http://www.atmel.com/Images/6221s.pdf[/URL]), and:
```
uname -a
Linux (none) 2.6.25 #148 Thu May 5 07:53:58 EDT 2011 armv5tejl unknown
```

> Incidentally, if you ever get a toolchain installed, do you know what all those shared libraries are in your original post? Do you have them? Hopefully they are not in /lib.

I have installed gcc & g++ before and built Qt projects. Those shared libraries in my original posted are generated by my project's other modules such as some Lib directories. Before build my current module, I must firstly build other modules thus these shared libraries will be generated and copied to /lib directory.

---

### Post by spjackson on 2012-08-03
> **pellyhawk said:**
> I have read what you have explained and decided to chose [COLOR="Red"]g++[/COLOR]-arm-linux-gnueabi because I cannot confirm my arm chip has FPU. I only do not know whether [COLOR="Red"]gcc[/COLOR]-arm-linux-gnueabi is need as well. You have told me "Yes":)

Sounds reasonable.
> 
I am running Ubuntu 10.04 and I wonder whether you advise me to type:
```
sudo apt-get install gcc-arm-linux-gnueabi g++-arm-linux-gnueabi
```

Well, then you have a problem because these packages we have been talking about were only introduced in 10.10. See [here]("http://askubuntu.com/questions/123835/gcc-arm-linux-gnueabi-package-not-found-on-10-04-lts-lucid").

> 
And the "apt-get install ..." will get the right one chosen from versions of natty, oneiric, precise, quantal.

If you were running one of these Ubuntu versions then indeed it would. However, you are running an older version that did not have the packages, so no it won't.
> 
My arm chip is AT91SAM9260B-CU ([URL="http://www.atmel.com/Images/6221s.pdf"]
http://www.atmel.com/Images/6221s.pdf[/URL]), and:
```
uname -a
Linux (none) 2.6.25 #148 Thu May 5 07:53:58 EDT 2011 armv5tejl unknown
```

That reference doesn't mention an FPU. It says the ARM chip is ARM926EJ-S. According to ARM, there is an "optional" FPU for this chip. So I would assume that you don't have one.

> 
I have installed gcc & g++ before and built Qt projects. Those shared libraries in my original posted are generated by my project's other modules such as some Lib directories. Before build my current module, I must firstly build other modules thus these shared libraries will be generated and copied to /lib directory.

I wouldn't put ARM libraries in /lib on an x86 system. It sounds like a path likely to lead to confusion.

---

### Post by pellyhawk on 2012-08-06
> **spjackson said:**
> Sounds reasonable.

Well, then you have a problem because these packages we have been talking about were only introduced in 10.10. See [here]("http://askubuntu.com/questions/123835/gcc-arm-linux-gnueabi-package-not-found-on-10-04-lts-lucid").


If you were running one of these Ubuntu versions then indeed it would. However, you are running an older version that did not have the packages, so no it won't.

Thanks for you to provide me this link. But how can you found 10.04 cannot support this package?

> I wouldn't put ARM libraries in /lib on an x86 system. It sounds like a path likely to lead to confusion.

Yes, I do not think putting ARM libraries in /lib on an x86 system is a good idea as well. But this project's Makefile is supported by other team and they told me the compiler cannot find these ARM libraries if they are put in other directory. Do you have a better idea? Maybe I can advise them to change it.

I have upload "The GNU Toolchain for ARM targets HOWTO.pdf" mentioned before.

---

### Post by spjackson on 2012-08-06
> **pellyhawk said:**
> Thanks for you to provide me this link. But how can you found 10.04 cannot support this package?

I initially suggested installing the official Ubuntu packages via apt-get, synaptic or whatever. You had not told us at that stage that you were running 10.04. The link I provided is about ["gcc-arm-linux-gnueabi package not found on 10.04 LTS (Lucid)"]("http://askubuntu.com/questions/123835/gcc-arm-linux-gnueabi-package-not-found-on-10-04-lts-lucid")
and the answer there is that the package "is only available in the universe repository since maverick (10.10)"

Also, you listed some versions for which you had found the package: natty, oneiric, precise, quantal. Notice that lucid is not in that list.

It is for these reasons that I wrote "these packages we have been talking about were only introduced in 10.10", i.e. the packages are not in the Ubuntu repositories for 10.04.

There may be binaries somewhere that work on 10.04, I don't know. Your other post suggests that you have found some.

> 
Yes, I do not think putting ARM libraries in /lib on an x86 system is a good idea as well. But this project's Makefile is supported by other team and they told me the compiler cannot find these ARM libraries if they are put in other directory. Do you have a better idea? Maybe I can advise them to change it.

I have upload "The GNU Toolchain for ARM targets HOWTO.pdf" mentioned before.
The linker would find the libraries elsewhere if the Makefile told it to look elsewhere with e.g. "-L/path/to/arm/development/libraries"

---

