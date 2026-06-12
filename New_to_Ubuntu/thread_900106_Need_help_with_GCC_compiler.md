---
title: "Need help with GCC compiler"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by SuperWZ on 2008-08-25
Hi, I'm new to Linux and tried to install both xmms and fceultra nes emulator from a tar.gz With each I encounter a problem at the ./configre step. Every time a run it I get an error with either my c compiler or c++ compiler. I made sure I had the newest version of GCC but the error continues. Does anyone know what I'm doing/not doing that causes this error?

---

### Post by NovaAesa on 2008-08-25
Could you post the terminal output of the error?

EDIT: You might be better of installing the packages from the repositories rather than from source, unless you have a special reason for installing from source. The package name for XMMS is xmms2, and for fceultra it is fceu. You should open up the Synaptic package manager and do a seach. Then mark the packages for install and click apply.

---

### Post by SuperWZ on 2008-08-25
This is what I get. I've only been on Linux a week I'm sure it is a simple fix.

root@ian-desktop:~# cd /usr/local/src/fceu/
root@ian-desktop:/usr/local/src/fceu# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking whether gcc and cc understand -c and -o together... yes
checking for g++... no
checking for c++... no
checking for gpp... no
checking for aCC... no
checking for CC... no
checking for cxx... no
checking for cc++... no
checking for cl... no
checking for FCC... no
checking for KCC... no
checking for RCC... no
checking for xlC_r... no
checking for xlC... no
checking whether we are using the GNU C++ compiler... no
checking whether g++ accepts -g... no
checking dependency style of g++... none
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
root@ian-desktop:/usr/local/src/fceu# 

I know it says it is not using the GNU C++ compiler but I made sure I had GCC so I figured I was covered.

---

### Post by NovaAesa on 2008-08-25
I'm not really sure what's going wrong there. I have never actually had to compile anything like that from source before, I have always used the repositories. My suggestion would be to follow the advice I gave in my first post (sorry, I edited it a bit after posting it, you probably missed that :P). Unless of course you have a special reason from installing from source, it's no a good idea to. It's generally a pain in the butt.

---

### Post by Oldsoldier2003 on 2008-08-25
> **NovaAesa said:**
>  I have never actually had to compile anything like that from source before
If you have never compiled from source you probably need to install build essential. It is not installed by default.

```
sudo apt-get install build-essential
```

---

### Post by SuperWZ on 2008-08-25
Thanks I should look in to using Synaptic for XMMS2. I just already had the tar ball so I thought I would give it a try. As for Fcue when I apt-get it, it only gave me the source unlike Znes or GBA express. It doesn't seem that hard to do a tar install, that is if I weren't getting these errors.

---

### Post by SuperWZ on 2008-08-25
> **Oldsoldier2003 said:**
> If you have never compiled from source you probably need to install build essential. It is not installed by default.

```
sudo apt-get install build-essential
```

Cool I look into that too.

Thanks for the help y'all.

---

### Post by NovaAesa on 2008-08-25
@OldSoldier2003, I think you are getting me and the OP mixed up. I have use g++ and gcc everyday for compiling C and C++, I just haven't had to install an application before from source.

@SuperWZ, yeah, the lack of build-essential could be the problem.

---

### Post by Oldsoldier2003 on 2008-08-25
> **NovaAesa said:**
> @OldSoldier2003, I think you are getting me and the OP mixed up. I have use g++ and gcc everyday for compiling C and C++, I just haven't had to install an application before from source.

Actually I did :) But looking at the output and reading the post led me to believe it was a build essential problem. We didn't get far enough to get dependency problems so we know that the first step would be to make sure the OP has build-essential.

---

### Post by SuperWZ on 2008-08-25
Yes build-essential was the problem, it got me over those humps, however now I am getting new errors during the make install process on both xmms and fcue but I'll worry about those in the morning. I've got to go bed.

Thanks for all the help.

---

### Post by Oldsoldier2003 on 2008-08-25
sleep well and when you're ready to tackle it again post the errors and we'll see if we can get you through it.

---

### Post by physeetcosmo on 2009-01-26
> **Oldsoldier2003 said:**
> If you have never compiled from source you probably need to install build essential. It is not installed by default.

```
sudo apt-get install build-essential
```

Thanks! This is needed for installing Icarus HDL development software.

---

