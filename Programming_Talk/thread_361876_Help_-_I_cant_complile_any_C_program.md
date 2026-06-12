---
title: "Help - I cant complile any C program"
date: 2007-02-14
forum: Programming Talk
---

### Post by sympeltun on 2007-02-14
Hi,

I have c programming this year in university, and i was trying to write a program and compile it using gcc. however it keeps saying that stdio.h(the c version) is not found, and i did install the compiler but i cannot figure out why the standard library is not there.. but this problem is only there for C programs.. but when i converted my code to C++ and compiled it it worked.

Please help, I really need to get the C programs to compile.. I really dont want to boot to windows each time i need to work on my programming labs. 

Thanks a lot

Sai

---

### Post by Mirrorball on 2007-02-14
Install build-essential.

---

### Post by sympeltun on 2007-02-14
i'm having trouble it keeps telling me that i dont have the right dependencies..
i did add extra repositories for dapper. 

is there any other method to install the dependencies?

---

### Post by Mirrorball on 2007-02-14
Did you add them and reload?

---

### Post by sympeltun on 2007-02-14
i am a noobie to linux when it comes to installing packages.. actually this is the message i get when i type the sudo install command:

sudo apt-get install build-essential

Error message - 

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.0) but it is not going to be installed
E: Broken packages
```

I think i screwed up royally because i got the extra repositories, and that installed libc6 2.4.1 version, but build-essential is compatible with the 2.3.6 version

do you see any chance of this working out? :confused: 

thanks again for your help

---

### Post by Mirrorball on 2007-02-14
Maybe you should reinstall libc6-dev.

---

### Post by sympeltun on 2007-02-14
unfortunately synaptic's not letting me do that because in order to have build-essentials, i need g++ and libc6-dev.. they both depend on linux-kernel-header, however this package is only compatible with the libc6 2.3.6.. i have libc6 2.4.1, if i switch back this will cause a few programs in my computer to start crashing..

this problem keeps getting more complicated *cryyy*

---

### Post by Mirrorball on 2007-02-15
This shouldn't have been happening if all of your repositories are official and you only installed packages from them. Why do you need libc6 2.4.1?

---

### Post by sympeltun on 2007-02-15
libc6 2.4.1 is required for azureus, amarok, and some other applications (not absolutely necessary) 

i'll try to switch back and install the build-essential.. a small sacrifice to get the build-essential to get working.

I'll post again if i have trouble.

thanks a lot mirrorball.

---

### Post by lnostdal on 2007-02-15
weird .. what does /etc/apt/sources.list look like?

---

### Post by Mirrorball on 2007-02-15
I've never had to install a different version of libc for Azureus and Amarok...

---

### Post by sympeltun on 2007-02-15
> **lnostdal said:**
> weird .. what does /etc/apt/sources.list look like?

Here you go: 

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ dapper free non-free
deb-src http://medibuntu.sos-sts.com/repo/ dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

PS: I have the original sources.list backed up

The only reason i had to add extra repositories, is because libc6 and it's dependant packages kept giving me trouble everytime i installed any software... but ever since i updated my computer after adding the repositories, no other problems regarding libc6 occured until today..

Also if you're wondering what system i have i'll put the specs below:

Ubuntu Dapper Drake 6.06  LTS
Dell Inspiron 2200 
Kernel - i'm at school right now so i cant find out the kernel version..

---

### Post by studiesrule on 2007-02-15
I don't see anything awkward in the source file. Perhaps, the PLF and the Ubuntu overlap, and are causing some problems. Try and comment out those lines and update. 
If that doesn't work, you could hunt the packages down of debian, and install them. I don't recommend it, I've only done it in non-critical scenarios with cutting-edge packages (for Anjuta 2.x). 
Also, you should try to apt-get it, because that produces a dependency traceback. You would be able to find out which package is causing the breakage (it isn't necessarily libc6, but could be a package further down). 

If your really desperate, you could always upgrade to edgy.

---

### Post by sympeltun on 2007-02-15
Hm.. i decided to get the compiler i got for windows, and use it through wine. my best bet is to upgrade to edgy.. no time now since its during school year, i'll do that over the summer.

thanks a lot for helping me figure out what the problems are.

Sai. :)

---

