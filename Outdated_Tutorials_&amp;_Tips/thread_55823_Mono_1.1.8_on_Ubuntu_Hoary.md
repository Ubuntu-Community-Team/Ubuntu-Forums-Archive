---
title: "Mono 1.1.8 on Ubuntu Hoary"
date: 2005-08-10
forum: Outdated Tutorials &amp; Tips
---

### Post by sebgate20 on 2005-08-10
Right - sorry this has been a long time in coming but get all the packages working together ain't easy. This shows you how to install Mono 1.1.8 (from Debian) on Ubuntu Hoary.

Before we begin, some things to remember: 

[list]
[*]You are mixing Breezy and Hoary packages which is not a good thing but it seems to work alright
[*]You are mixing Debian and Ubuntu packages which is also not a good thing but it seems to work
[*]It has worked for me a on a few machines but it might be different for you
[*]This is NOT recommended if you are unsure of what you are doing
[*]This is NOT recommended if you want to stick to Ubuntu packages only
[*]This will not be recommended by any of the Ubuntu or Debian developers
[*]You can always wait for Breezy :-)
[/list] 

**Section 1 - Removing Old Mono from Backports/Hoary Repos**

You should remove any Mono packages you already have installed. You must have these remove (if you don't have them installed, running this anyway to check won't harm):
[FONT=Courier New]
sudo apt-get remove mono mono-utils monodevelop monodoc mono-devel mono-mcs mono-assemblies-arch [/FONT]

**Section 2 - Getting Breezy Packages**

Some of the Debian packages depend on versions higher than those in Hoary so you need to upgrade to the Breezy ones. You MUST install them in this order for it to work:

[FONT=Courier New]mkdir ~/Mono
cd ~/Mono
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu8_i386.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.5-1ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.5-1ubuntu8_i386.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu8_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu8_i386.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu8_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu8_all.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu10_i386.deb)
sudo dpkg -i linux-kernel-headers_2.6.11.2-0ubuntu10_i386.deb
sudo dpkg -i libc6_2.3.5-1ubuntu8_i386.deb
sudo dpkg -i locales_2.3.5-1ubuntu8_all.deb
sudo dpkg -i libc6-dev_2.3.5-1ubuntu8_i386.deb
sudo dpkg -i libc6-i686_2.3.5-1ubuntu8_i386.deb[/FONT]

**Section 3 - Adding the Repo**

Add these lines to your /etc/apt/sources.list (sudo gedit /etc/apt/sources.list)

## Debian Mono
deb [http://debian.meebey.net/](http://debian.meebey.net/) ./

Save and close

Then run

[FONT=Courier New]sudo apt-get update[/FONT]

**Section 4 - Install Mono Basics**

[COLOR=Red]**PLEASE NOTE: DO NOT INSTALL mono-assemblies-arch AS IT WILL BREAK YOU SYSTEM!**[/COLOR]

Just Mono	
[FONT=Courier New]sudo apt-get install mono libmono0[/FONT]

Mono Development	
[FONT=Courier New]sudo apt-get install mono libmono0 libmono-dev mono-mcs mono-devel mono-utils[/FONT]

**Section 5 - Installing Mono Development Suite **

If you want to install MonoDevelop, you need a newer Monodoc (1.0.6) so we need to turn to Debian again:
[FONT=Courier New]
mkdir ~/Mono/MonoDoc
cd ~/Mono/MonoDoc
wget [http://ftp.de.debian.org/debian/pool/main/m/monodoc/monodoc-base_1.0.6-3_all.deb](http://ftp.de.debian.org/debian/pool/main/m/monodoc/monodoc-base_1.0.6-3_all.deb)
wget [http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc_1.0.6-3_all.deb](http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc_1.0.6-3_all.deb)
wget [http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-browser_1.0.6-3_all.deb](http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-browser_1.0.6-3_all.deb)
wget [http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-manual_1.0.6-3_all.deb](http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-manual_1.0.6-3_all.deb)
sudo dpkg -i *.deb[/FONT]

You can now install MonoDevelop with:

[FONT=Courier New]sudo apt-get monodevelop[/FONT]

Let me know if it works. I hope it does! But PLEASE be careful and make sure you know what you are letting yourself in for ;-)

Seb

---

### Post by sebgate20 on 2005-08-10
And for those doubters:

seb@basestation:~/Mono$ mono -V
Mono JIT compiler version 1.1.8.2, (C) 2002-2005 Novell, Inc and Contributors. [www.mono-project.com](www.mono-project.com)
        TLS:           normal
        GC:            Included Boehm (with typed GC)
        SIGSEGV      : normal
        Globalization: normal
seb@basestation:~/Mono$

So it does work.

Seb

---

### Post by sebgate20 on 2005-08-15
Has anyone tried this out?

---

### Post by undy on 2005-08-19
[QUOTE=sebgate20]Has anyone tried this out?[/QUOTE]

Yep, just done it - looking good so far. Thanks for your work.

---

### Post by student on 2005-08-24
maybe a bit offtopic, but is there a way to compile c# code into any linux language ?
I would love to use the mono IDE, but hate the binaries it produces...

---

### Post by spectator on 2005-08-24
The first four links in the second step are outdated - '8' should be changed to '10' before the _i386/all.deb. Also the last command I believe should include 'install'.

It works for me. Thanks a lot.

s.

---

### Post by ghostwind on 2005-09-01
[QUOTE=spectator]The first four links in the second step are outdated - '8' should be changed to '10' before the _i386/all.deb. Also the last command I believe should include 'install'.

It works for me. Thanks a lot.

s.[/QUOTE]
 I got suck on monodevelop

 
tms2db@tms2gc:~/Mono/MonoDoc$ sudo apt-get install monodevelop
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
  monodevelop: Depends: libgconf2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgecko2.0-cil (>= 0.10) but it is not installable
               Depends: libglade2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libglib2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgnome2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgtk2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgtksourceview2.0-cil (>= 0.10) but it is not installable
               Depends: libgtksourceview2.0-cil (< 0.11) but it is not installable
E: Broken packages
Any ideas

---

### Post by ghostwind on 2005-09-01
[QUOTE=ghostwind]I got suck on monodevelop

 
tms2db@tms2gc:~/Mono/MonoDoc$ sudo apt-get install monodevelop
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
  monodevelop: Depends: libgconf2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgecko2.0-cil (>= 0.10) but it is not installable
               Depends: libglade2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libglib2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgnome2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgtk2.0-cil (>= 1.9.5) but 1.9.2-2ubuntu1 is to be installed
               Depends: libgtksourceview2.0-cil (>= 0.10) but it is not installable
               Depends: libgtksourceview2.0-cil (< 0.11) but it is not installable
E: Broken packages
Any ideas[/QUOTE]
 I sorted the problem by adding the following backports to sources.list

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by ghostwind on 2005-09-01
Mono 1.1.8  and Monodevelop on Ubuntu Hoary
This is a revised how to taken from sebgate20 posting

Before we begin, some things to remember:

    * You are mixing Breezy and Hoary packages which is not a good thing but it seems to work alright
    * You are mixing Debian and Ubuntu packages which is also not a good thing but it seems to work
    * It has worked for me a on a few machines but it might be different for you
    * This is NOT recommended if you are unsure of what you are doing
    * This is NOT recommended if you want to stick to Ubuntu packages only
    * This will not be recommended by any of the Ubuntu or Debian developers
    * You can always wait for Breezy


[COLOR=DarkSlateBlue]Section 1 - Removing Old Mono from Backports/Hoary Repos[/COLOR]

You should remove any Mono packages you already have installed. You must have these remove (if you don't have them installed, running this anyway to check won't harm):

sudo apt-get remove mono mono-utils monodevelop monodoc mono-devel mono-mcs mono-assemblies-arch

[COLOR=DarkSlateBlue]Section 2 - Getting Breezy Packages[/COLOR]

Some of the Debian packages depend on versions higher than those in Hoary so you need to upgrade to the Breezy ones. You MUST install them in this order for it to work:

mkdir ~/Mono
cd ~/Mono
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.5-1ubuntu10_i386.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.5-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.3.5-1ubuntu10_i386.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu10_i386.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/locales_2.3.5-1ubuntu10_all.deb)
wget [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-kernel-headers/linux-kernel-headers_2.6.11.2-0ubuntu10_i386.deb)
sudo dpkg -i linux-kernel-headers_2.6.11.2-0ubuntu10_i386.deb
sudo dpkg -i libc6_2.3.5-1ubuntu10_i386.deb
sudo dpkg -i locales_2.3.5-1ubuntu10_all.deb
sudo dpkg -i libc6-dev_2.3.5-1ubuntu10_i386.deb
sudo dpkg -i libc6-i686_2.3.5-1ubuntu10_i386.deb

[COLOR=DarkSlateBlue]Section 3 - Adding the Repo[/COLOR]

Add these lines to your /etc/apt/sources.list (sudo gedit /etc/apt/sources.list)

## Debian Mono
deb [http://debian.meebey.net/](http://debian.meebey.net/) ./

#Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted


Save and close

So source.list should look like this

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Preview i386 Binary-1 (20050330)]/ hoary main restricted


deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Debian Mono
deb [http://debian.meebey.net/](http://debian.meebey.net/) ./

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted



Then run

sudo apt-get update

[COLOR=DarkSlateBlue]Section 4 - Install Mono Basics[/COLOR]
[COLOR=Red]
PLEASE NOTE: DO NOT INSTALL mono-assemblies-arch AS IT WILL BREAK YOU SYSTEM![/COLOR]

Just Mono
sudo apt-get install mono libmono0

Mono Development
sudo apt-get install mono libmono0 libmono-dev mono-mcs mono-devel mono-utils

[COLOR=DarkSlateBlue]Section 5 - Installing Mono Development Suite[/COLOR]

If you want to install MonoDevelop, you need a newer Monodoc (1.0.6) so we need to turn to Debian again:

mkdir ~/Mono/MonoDoc
cd ~/Mono/MonoDoc
wget [http://ftp.de.debian.org/debian/pool/main/m/monodoc/monodoc-base_1.0.6-3_all.deb](http://ftp.de.debian.org/debian/pool/main/m/monodoc/monodoc-base_1.0.6-3_all.deb)
wget [http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc_1.0.6-3_all.deb](http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc_1.0.6-3_all.deb)
wget [http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-browser_1.0.6-3_all.deb](http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-browser_1.0.6-3_all.deb)
wget [http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-manual_1.0.6-3_all.deb](http://ftp.uk.debian.org/debian/pool/main/m/monodoc/monodoc-manual_1.0.6-3_all.deb)
sudo dpkg -i *.deb

You can now install MonoDevelop with:

sudo apt-get install monodevelop

---

