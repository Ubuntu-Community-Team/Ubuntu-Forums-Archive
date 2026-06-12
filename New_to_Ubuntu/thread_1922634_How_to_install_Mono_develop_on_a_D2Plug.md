---
title: "How to install Mono develop on a D2Plug?"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by HaunsTM on 2012-02-09
Hi all!

I'm trying to install Mono develop on my D2Plug (ARMADA 510 processor). Mono is a cross platform .NET development framework and since I need a version > 2.4 (which is the version found in the Synaptics package manager), the only way to do this is to go to get it from the badgerports repository. (This is what I believe)


From badgerports:
[I][COLOR="Navy"]Ubuntu Lucid (10.04 LTS)

Users of Ubuntu 10.04 LTS (Lucid Lynx) can install 2.10.5 by using Synaptic from the badgerports repository. badgerports is an unofficial community project from one of the Debian/Ubuntu Mono developers to ship latest Ubuntu packages for Ubuntu LTS users. Please visit the URL below for full information on enabling these packages:

[http://badgerports.org/](http://badgerports.org/)[/COLOR][/I], [http://mono-project.com/DistroPackages/Ubuntu](http://mono-project.com/DistroPackages/Ubuntu)


Well, to save you the details, this does not work that easy for me. I tried to follow the install instructions found there but run into issues (due to the ARM processor I think).

I mailed the contact person on the site ([http://badgerports.org](http://badgerports.org)) with my problems, and I guess he would give me further answers if i just asked him, but since I think the solution might interest more people than just me, why not ask this question on this public forum?

When I followed the standard instructions I had problems. I mailed the site contact person and this was his answer:
[I]
[COLOR="navy"]I'm afraid I don't publish packages for ARM - I rely on Launchpad's PPA
infrastructure to build my packages, and mere mortals like me aren't
given access to ARM builders.[/COLOR]
[/I]
My next question to the site contact person was if it was impossible to install Monodevelop version > 2.4 on the D2Plug?


[I][COLOR="navy"]It's actually possible, but not so user-friendly.

You're going to need to compile a couple of things yourself, but you can
use the badgerports source packages to do it cleanly-ish.

Install devscripts and wget, make a new folder, and run "dget
https://launchpad.net/~directhex/+archive/ppa/+files/mono_2.10.5-1~dhx1~lucid1.dsc" - this should download the mono source package from badgerports, and extract it to the current folder. Switch into the mono-2.10.5 folder and run dpkg-buildpackage. It'll throw an error about missing build dependencies - install them, and try again. Eventually it'll start compiling Mono (which will take a few hours)

Once it's done, there'll be a bunch of .deb files in the parent folder -
you can install them with "dpkg -i".

Once you have Mono 2.10.5 for ARM installed, you can actually just
download the amd64 MonoDevelop package directly from
[https://launchpad.net/~directhex/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid](https://launchpad.net/~directhex/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid) - you don't need to recompile it, because .NET code is cross-platform, so the package is cross-platform too.

Any other missing dependencies, check my PPA URL above - if the package
is _all.deb, download it and install with "dpkg -i". If there are
_i386.deb or _amd64.deb packages, you'll need to recompile it yourself
by running "dget" on the .dsc file and following the procedure I
outlined above for Mono

Sorry this isn't any easier than it could be, but I did some less-common
architecture builds for badgerports 6.06 - it took about 90% of my
packaging time, and had less than a dozen users.[/COLOR][/I]


Well, I installed the devscripts (via "default" Synaptics package manager on D2Plug, I downloaded the mono source package from badgerports:

[FONT="Courier New"]dget [https://launchpad.net/~directhex/+archive/ppa/+files/mono_2.10.5-1~dhx1~lucid1.dsc](https://launchpad.net/~directhex/+archive/ppa/+files/mono_2.10.5-1~dhx1~lucid1.dsc)[/FONT]

I exctracted the package
[FONT="Courier New"]sudo tar xvjf mono_2.10.5.orig.tar.bz2[/FONT]

I switched to the directory:
[FONT="Courier New"]ubuntu@D2Plug:~$ cd mono-2.10.5
ubuntu@D2Plug:~/mono-2.10.5$[/FONT]


and tried to build:

[FONT="Courier New"]ubuntu@D2Plug:~/mono-2.10.5$ sudo dpkg-buildpackage
[sudo] password for ubuntu:
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
[B]tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1[/B][/FONT]

How should I proceed? What should my next step be? How should I force "dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1"?

---

### Post by directhex on 2012-02-09
> **HaunsTM said:**
> 
I exctracted the package
[FONT="Courier New"]sudo tar xvjf mono_2.10.5.orig.tar.bz2[/FONT]

I switched to the directory:
[FONT="Courier New"]ubuntu@D2Plug:~$ cd mono-2.10.5
ubuntu@D2Plug:~/mono-2.10.5$[/FONT]

This is the step where you went wrong.

Delete that folder with "rm -r mono-2.10.5" and use this command to extract instead:

```
dpkg-source -x mono_2.10.5-1~dhx1~lucid1.dsc
```

This will extract not only the upstream source code, but all of the Debian packaging data and patches too.

---

### Post by HaunsTM on 2012-02-11
Thank you so much! It worked!

I think there is just one more thing that I need help with. I tried to install the .deb-packages but got this:

```
ubuntu@D2Plug:~$ sudo dpkg -i libmono2.0-cil_2.10.5-1~dhx1~lucid1_all.deb
[sudo] password for ubuntu: 
Selecting previously deselected package libmono2.0-cil.
(Reading database ... 155255 files and directories currently installed.)
Unpacking libmono2.0-cil (from libmono2.0-cil_2.10.5-1~dhx1~lucid1_all.deb) ...
dpkg: dependency problems prevent configuration of libmono2.0-cil:
 libmono2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however:
  Version of libmono-corlib2.0-cil on system is 2.4.4~svn151842-1ubuntu4.
 libmono2.0-cil depends on libmono-security2.0-cil (>= 2.6.7); however:
  Version of libmono-security2.0-cil on system is 2.4.4~svn151842-1ubuntu4.
 libmono2.0-cil depends on libmono-system-web2.0-cil (>= 2.10.3); however:
  Package libmono-system-web2.0-cil is not installed.
 libmono2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however:
  Version of libmono-system2.0-cil on system is 2.4.4~svn151842-1ubuntu4.
dpkg: error processing libmono2.0-cil (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmono2.0-cil

```What shall I do in order to get rid of the "dependency problems - leaving unconfigured"?

---

### Post by directhex on 2012-02-11
> **HaunsTM said:**
> Thank you so much! It worked!

I think there is just one more thing that I need help with. I tried to install the .deb-packages but got this:

```
ubuntu@D2Plug:~$ sudo dpkg -i libmono2.0-cil_2.10.5-1~dhx1~lucid1_all.deb
[sudo] password for ubuntu: 
Selecting previously deselected package libmono2.0-cil.
(Reading database ... 155255 files and directories currently installed.)
Unpacking libmono2.0-cil (from libmono2.0-cil_2.10.5-1~dhx1~lucid1_all.deb) ...
dpkg: dependency problems prevent configuration of libmono2.0-cil:
 libmono2.0-cil depends on libmono-corlib2.0-cil (>= 2.6.3); however:
  Version of libmono-corlib2.0-cil on system is 2.4.4~svn151842-1ubuntu4.
 libmono2.0-cil depends on libmono-security2.0-cil (>= 2.6.7); however:
  Version of libmono-security2.0-cil on system is 2.4.4~svn151842-1ubuntu4.
 libmono2.0-cil depends on libmono-system-web2.0-cil (>= 2.10.3); however:
  Package libmono-system-web2.0-cil is not installed.
 libmono2.0-cil depends on libmono-system2.0-cil (>= 2.10.3); however:
  Version of libmono-system2.0-cil on system is 2.4.4~svn151842-1ubuntu4.
dpkg: error processing libmono2.0-cil (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libmono2.0-cil

```What shall I do in order to get rid of the "dependency problems - leaving unconfigured"?

You can specify more than one .deb at once with "dpkg -i" - you should be installing pretty much all of them - i.e. mono-devel and everything it says it needs (maybe even *.deb, but a couple of them will error out like firebirdsql, you'll need to remove those subsequently)

---

### Post by HaunsTM on 2012-02-11
> **directhex said:**
> You can specify more than one .deb at once with "dpkg -i" - you should be installing pretty much all of them - i.e. mono-devel and everything it says it needs (maybe even *.deb, but a couple of them will error out like firebirdsql, you'll need to remove those subsequently)

```
dpkg -i *.deb
```

That also worked! Thank you so much!


From my original post (the mail correspondense with the badgerports contact person) I got this message:
> [I][COLOR=navy]Once you have Mono 2.10.5 for ARM installed, you  can actually just
download the amd64 MonoDevelop package directly from
[https://launchpad.net/~directhex/+ar...s_filter=lucid]("https://launchpad.net/%7Edirecthex/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid")  - you don't need to recompile it, because .NET code is cross-platform,  so the package is cross-platform too.[/COLOR][/I]

If I understand it correctly, I do have Mono.2.10.5 after the ```
dpkg -i *.deb
``` command by now? If so, and anyway, I'm not sure what to download from *[COLOR=navy][https://launchpad.net/~directhex/+ar...s_filter=lucid]("https://launchpad.net/%7Edirecthex/+archive/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=lucid")[/COLOR]*? I can't find a package "amd64 MonoDevelop" from his link?

---

### Post by directhex on 2012-02-12
monodevelop_2.8.5+dfsg-1~dhx1~lucid1_all.deb

---

