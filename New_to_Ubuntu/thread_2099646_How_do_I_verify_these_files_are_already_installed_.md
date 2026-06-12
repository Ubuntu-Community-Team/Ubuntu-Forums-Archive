---
title: "How do I verify these files are already installed on Ubuntu 12.10?"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by regency on 2012-12-30
I am new to Linux and Ubuntu; hence detailed instructions on what specific commands to issue are welcome.

I would like to know if the following files/packages/programs are already installed on my Ubuntu 12.10, kernel 3.5.0.21, 64 bit, English:

(1) XOrg 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, 7.5 or 7.6

(2) Linux kernel 2.6 or above

(3) glibc version 2.2 or 2.3

(4) XFree86-Mesa-libGL

(5) libstdc++

(6) libgcc

(7) XFree86-libs

(8) fontconfig

(9) freetype

(10) zlib

(11) gcc

According to AMD, the above files/packages/programs must be installed prior to installing the Catalyst driver for my computer. My computer has a discreet AMD Radeon HD 7730M graphics card.

If any one of the above is NOT installed, please show me from which site(s) and how to download them.

Thanks in advance

PS: I googled for how to list installed packages on my Ubuntu OS, I found and tried the following command:

```
dpkg --get-selections > 1.txt
```After clicking the 1.txt in gedit, I saw a list of files. But it doesn't list whether I have XOrg and its version. I certainly can't find XFree86-Mesa-libGL and XFree86-libs in that list.

---

### Post by 3rdalbum on 2012-12-30
**STOP.**

Before you start downloading drivers from the AMD website and install them manually, you should know that Ubuntu has a way of installing AMD graphics drivers in a safer, better-supported way.

Go to Ubuntu Software Center. Go to the Edit menu and come down to Software Sources. The last tab allows you to easily download and install a set of official AMD graphics drivers, that will keep in sync with your kernel version (the download from the AMD website will NOT).

To answer your actual question, you already have the required software for running the AMD graphics driver. If you were to download and install the driver from the AMD website rather than use the good method I advised you of, then you would need the build-essential package from Ubuntu Software Center. But don't do the manual way - use the method I advised you. It will download and install everything you need anyway.

I hope you've also abandoned the plan to downgrade your kernel so you can run anti-virus. Anti-virus is not necessary for Linux as there are currently no Linux viruses.

It seems like you're having a bit of trouble unlearning your Windows habits; just remember, Linux is incredibly different to Windows, not much of your current knowledge will transfer over. Just pretend to be a computer newbie when using Linux and you'll do fine.

---

### Post by Zill on 2012-12-30
> **3rdalbum said:**
> ...It seems like you're having a bit of trouble unlearning your Windows habits; just remember, Linux is incredibly different to Windows, not much of your current knowledge will transfer over. Just pretend to be a computer newbie when using Linux and you'll do fine.
+1 - Excellent advice!  I also suggest the OP reads the following link:
[LIST]
[*][Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")
[/LIST]

---

### Post by Elfy on 2012-12-30
all of which is going to be completely moot if you do as you want in your other thread - [http://ubuntuforums.org/showthread.php?t=2098811](http://ubuntuforums.org/showthread.php?t=2098811)

---

### Post by Chogan on 2012-12-30
i think you can use _synaptic package manager_ and search given package name to see if it is installed before or no.

---

### Post by audiomick on 2012-12-30
> **Chogan said:**
> i think you can use _synaptic package manager_ and search given package name to see if it is installed before or no.

Yes, you can. The software centre is not quite as intuitive for me, but it will show you whether a package is installed too.


While we are at the software center, I would add my voice to those here and in the other thread regarding antivirus.

Whilst it is not true that there are no viruses for linux, the number is indeed very small (I think it is something under 50 total known viruses) and your chances of being infected are indeed very close to 100% that you wont.

If you are worried about picking up something and passing it along to a Windows machine, well, that is another thing. Having said that, I don't have any anti-virus on any of my installs, and I don't believe I have ever got a virus on my Vista which dual boots with ubuntu.

Anyway, there is antivirus stuff in the software centre. Search for "anti virus" in there. I would suggest using that and being careful where you click in the internet.

---

### Post by 3rdalbum on 2012-12-30
> **audiomick said:**
> 
Whilst it is not true that there are no viruses for linux, the number is indeed very small (I think it is something under 50 total known viruses) and your chances of being infected are indeed very close to 100% that you wont.

Not meaning to derail the thread, but we talk about Smallpox being "eradicated" in the developed world, even though it still exists in laboratories. It poses no threat (even if it got out, most people are vaccinated against it or have had chicken pox), so we say it is eradicated.

The same for Linux viruses. Most, if not all, will no longer work on today's Linux distros. None are in the wild, only at anti-virus labs.

So what I said was true.

---

### Post by regency on 2012-12-30
Hi guys,

Thanks for your advice.

I DO know that Linux machines don't need antivirus software.

Nevertheless I wish to install it just so I can learn the basics of issuing Linux commands (to be more exact Debian commands).

I can't learn computing or Linux by picking up and reading a manual. I  have to have a project to work on and as I work on it, I pick up skills  and concepts along the way.

I have installed Symantec Antivirus for Linux successfully on Ubuntu  12.10, kernel 3.5.0.21 and I know how to sudo some commands, change  directories/folders, build some kernel modules using "build-essential"  command within a time period of 3 days. I even helped Symantec update  its technical support documentation about its software compatibility  with the latest version of Ubuntu OS.

---

### Post by audiomick on 2012-12-30
> **regency said:**
> Nevertheless I wish to install it just so I can learn the basics of issuing Linux commands (to be more exact Debian commands).

Fair enough. 

Given that, you might consider a "throw away" install to do things like that in, so you can play around and not worry about it getting broken. A dual boot or multi boot of various Linux installs is not hard to do, and you learn a bit more whilst setting it up. ;)

---

### Post by regency on 2012-12-30
> **audiomick said:**
> Fair enough. 

Given that, you might consider a "throw away" install to do things like that in, so you can play around and not worry about it getting broken. A dual boot or multi boot of various Linux installs is not hard to do, and you learn a bit more whilst setting it up. ;)

Thanks pal for your advice.

I have a number of spare hard disk drives at my disposal. I installed Ubuntu on one of them. If I mess things up on it, I will just have to reformat and reinstall it. Well, to be honest, I have reinstalled it at least 5 times, so I am quite familiar with the instalation routines.

---

### Post by andrew.46 on 2012-12-30
> **regency said:**
> 
I DO know that Linux machines don't need antivirus software.

Nevertheless I wish to install it just so I can learn the basics of issuing Linux commands (to be more exact Debian commands).

I can't learn computing or Linux by picking up and reading a manual. I  have to have a project to work on and as I work on it, I pick up skills  and concepts along the way.

Well, bearing in mind all the excellent advice already given above, you may be interested to know that versions of applications in use, kernel build etc can also be found without necessarily resorting to the Software Centre or dpkg commands. For the kernel in use there is the *uname *command:

```

andrew@skamandros~$ **[COLOR="Red"]uname --help[/COLOR]**
Usage: uname [OPTION]...
Print certain system information.  With no OPTION, same as -s.

  -a, --all                print all information, in the following order,
                             except omit -p and -i if unknown:
  -s, --kernel-name        print the kernel name
  -n, --nodename           print the network node hostname
  -r, --kernel-release     print the kernel release
  -v, --kernel-version     print the kernel version
  -m, --machine            print the machine hardware name
  -p, --processor          print the processor type or "unknown"
  -i, --hardware-platform  print the hardware platform or "unknown"
  -o, --operating-system   print the operating system
      --help     display this help and exit
      --version  output version information and exit

Report uname bugs to bug-coreutils@gnu.org
GNU coreutils home page: <http://www.gnu.org/software/coreutils/>
General help using GNU software: <http://www.gnu.org/gethelp/>
For complete documentation, run: info coreutils 'uname invocation'

```

and many applications will respond to a *--version* command, such as gcc:

```

andrew@skamandros~$**[COLOR="Red"] gcc --version[/COLOR]**
gcc (GCC) 4.7.1
Copyright (C) 2012 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

There have even been times where this wil be a more accurate way of finding version information as for a *very small *number of applications the Debian/Ubuntu package naming has been a little confusing. The example that springs to mind is the [Ubuntu wine package]("http://wiki.winehq.org/FAQ#head-0bae04b4126dffb8a08bf020982badacb6f367ff").

---

### Post by regency on 2013-01-01
@ andrew.46

Thanks pal for your help.

---

### Post by Paqman on 2013-01-01
> **regency said:**
> 
Nevertheless I wish to install it just so I can learn the basics of issuing Linux commands (to be more exact Debian commands).


That's fine, but is there much point in knowing to do things the wrong way? Linux might not be as hard to learn if you do things the right, easy way.

---

### Post by siddharth007 on 2013-01-04
Easiest way...Use **apt-get install **followed by all the packages you mentioned.The ones which are not installed will be installed then.For others you will get the confirmation that the package is installed.Simple enough. :D

---

### Post by coldcritter64 on 2013-01-04
For purely information gathering (no installing) OP, you can also try
```
apt-cache policy <package-name>
```on each of your packages.

for example,
```
apt-cache policy gcc
``` will tell you if it is installed, what version is installed and what versions are available.

---

