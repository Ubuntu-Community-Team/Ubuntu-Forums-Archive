---
title: "stdio.h not found"
date: 2012-12-12
forum: New to Ubuntu
---

### Post by maruf7 on 2012-12-12
Hi,
I'm trying to 'make' a program, but when I type 'make' at terminal after './configure', it says 'Fatal error: stdio.h'not found, no such file or directoiry'.

Do I need build-essential or a compiler? If so, please help how to get one working. Thanks.

---

### Post by squakie on 2012-12-13
What release of ubuntu are you running?

---

### Post by maruf7 on 2012-12-13
Ubuntu 12.04

---

### Post by squakie on 2012-12-13
You may need to install the gcc-multilib package.  Everyone claims now that build-essential is only needed if you are building a deb file.  However, it was previously needed to get the standard libs, etc. - can't hurt to install it.

We should also know a few things more:

- what is the software, and where did you get it?

- did it have a readme that perhaps said to run config?  Sometimes source packages require that so that they can pass to the compiler and linker where libs, standard includes, etc., are located.

- did it have you change your PATH environment variable?

- Are you running 32-bit ubuntu on a 64-bit processor?

---

### Post by maruf7 on 2012-12-13
- the software is hydra-7.3.tar.gz from THC.org

- readme says to run ./configure and I did so.

-I have not changed any Path environment variable manually.

- You're right. I'm running 32bit Ubuntu in 64bit processor.

Thanks.

---

### Post by squakie on 2012-12-13
Yep - from what I've read you need the gcc-multilib package when compiling 32-bit apps in 32-bit ubuntu for 64-bit CPU (*if* I read the information correctly),

---

### Post by Wim Sturkenboom on 2012-12-13
32bit operating systems come with 32bit libraries and 64bit operating systems come with 64bit libraries. Nothing special required. Only time when you need both libraries is when you want to run 32bit applications on a 64bit operating system.

PS
stdio.h is not a library, by the way

---

### Post by COMECON on 2012-12-13
Could you try running this command?
```
 $ ls /usr/include | grep stdio 
```
And what's the output if there's any? You could also try:
```
 $ whereis stdio.h 
```

Catbuntu

PS: I always used 32-bit systems on a 64-bit processor, and I never had to do any "extra step" to compile properly...

---

### Post by squakie on 2012-12-13
> **Wim Sturkenboom said:**
> 32bit operating systems come with 32bit libraries and 64bit operating systems come with 64bit libraries. Nothing special required. Only time when you need both libraries is when you want to run 32bit applications on a 64bit operating system.

PS
stdio.h is not a library, by the way

I think we all know any .h file is a header, not a lib.  However, sometimes when libs are being added header files do come with them - such as when multiple libs are installed in a folder, and one of the folders the subprocess creates is for headers.  Wasn't sure on gcc-multilib - guess I missed the part about a 64-bit OS (and hence why I said "*if* I read the information correctly") - I thought it had said 64-bit CPU.  As far as 32-bit running on either 32-bit or 64-bit systems, I thought that was a given also.  Outside of gcc-multilib, not sure why you posted info that any of us who are programmers already knew.  So, I don't know if this was an attempt at a personal attack on me or not, but *if* it was, it's worthless.

---

### Post by maruf7 on 2012-12-14
Thanks all for your response...
I ran the command:
```
$ ls /usr/include | grep stdio
```

No result.

Also ran the code:
```
$ whereis stdio.h
```

and result is:
```
stdio: /usr/share/man/man3/stdio.3.gz

```

---

### Post by Doug S on 2012-12-14
It is not clear to me why you would have the man page without the actual file.
Do you have build-essential installed? (and if yes, maybe re-install it.)```
sudo apt-get install build-essential
```

---

### Post by maruf7 on 2012-12-14
Is build-essential included in the installation dvd or I need to download?

---

### Post by maruf7 on 2012-12-14
Ok, please tell me one thing: what is the reason of the error "stdio.h not found"? Because I've no compiler or I've no build-essential installed?

---

### Post by steeldriver on 2012-12-14
I don't know what *meta* packages install it, but the actual package is libc6-dev I think - you can confirm that if you have apt-file

```
$ apt-file search '/usr/include/stdio.h'
libc6-dev: /usr/include/stdio.h
```or

```
$ apt-cache show libc6-dev
Package: libc6-dev
Priority: optional
Section: libdevel
Installed-Size: 19611
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>
Architecture: i386
Source: eglibc
Version: 2.15-0ubuntu10.3
Provides: libc-dev
Depends: libc6 (= 2.15-0ubuntu10.3), libc-dev-bin (= 2.15-0ubuntu10.3), linux-libc-dev
Recommends: gcc | c-compiler
Suggests: glibc-doc, manpages-dev
.
.
.
[B] Contains the symlinks, headers, and object files needed to compile
 and link programs which use the standard C library.
[/B]Multi-Arch: same
Homepage: http://www.eglibc.org
.
.
.
```

It shouldn't do any harm to re-install build-essential if you are in any doubt (yes it probably installs other stuff you don't need - but the overhead is not significant afaik)

---

### Post by Wim Sturkenboom on 2012-12-14
> **squakie said:**
> ... (and hence why I said "*if* I read the information correctly")And hence my reply; as far as I was concerned, it needed 'clarification / correction' and my post was the attempt to that.

> **squakie said:**
> So, I don't know if this was an attempt at a personal attack on me or not, but *if* it was, it's worthless.No, it was not a personal attack. I apologize if you interpreted it like that. I call a spade a spade and you would have known if it was a (personal) attack; no 'ifs' or 'buts'.

---

### Post by squakie on 2012-12-14
> **Wim Sturkenboom said:**
> And hence my reply; as far as I was concerned, it needed 'clarification / correction' and my post was the attempt to that.

No, it was not a personal attack. I apologize if you interpreted it like that. I call a spade a spade and you would have known if it was a (personal) attack; no 'ifs' or 'buts'.

Thanks! ;)

---

### Post by squakie on 2012-12-14
steeldriver - that should be the correct package(lib) to install.  I'm a little surprised - most of these things, including the compilers, headers, etc., were part of the build-essential package.  Now, at least for 12.10, the package description makes it sound like it is now only for building deb packages.  I'm a little confused as to why they would do that.  At a minimum now they should have things like "essential c development", "essential java development", "essential python development", etc., so there are meta packages for the type of development the programmer intends to do.  I still installed build-essential before someone pointed this out in another thread, so I don't know what, if any, relation it has to my packages, but the c compilers, headers, etc., where all installed on my 12.10 system (originally 12.04 - upgraded to 12.10 if it might make any difference).

If an admin sees this, perhaps they can give us guidance on the list of development libs and compilers installed by default, and what packages would need to be installed according to development choice.

---

### Post by Doug S on 2012-12-14
The build essential package contains 5 other packages, there hasn't been any changes to that between versions of Ubuntu. Install build-essential, as I mentioned above, and then go ahead and compile stuff. It is not included by default during install.
See [here]("http://packages.ubuntu.com/quantal/build-essential")

---

### Post by squakie on 2012-12-15
> **Doug S said:**
> The build essential package contains 5 other packages, there hasn't been any changes to that between versions of Ubuntu. Install build-essential, as I mentioned above, and then go ahead and compile stuff. It is not included by default during install.
See [here]("http://packages.ubuntu.com/quantal/build-essential")

The description in synaptic  has now changed to indicate it is only needed if you are going to build deb packages. Also, looking at the file list for the package for i386:

This list was generated on Sat Nov 13 16:03:17 CET 2010 for i386
It contains a list of essential packages (which are also build-essential).

base-files
base-passwd
bash
bsdutils
coreutils
dash
debianutils
diffutils
dpkg
e2fsprogs
findutils
grep
gzip
hostname
login
mount
ncurses-base
ncurses-bin
perl-base
python-minimal
sed
tar
util-linux

Nothing there for the standard libs, etc., anymore.

This was only recently mentioned to me in another thread.  Me - I've always installed build-essential in the past, but the description was different then and didn't say you only need it if you are building deb packages.

If you look on the page you linked to you'll see those packages you mentioned are not part of build-essential, but rather packages it depends on.  So, if the package manager is working correctly then yes installing build-essential would install those packages because they are dependancies - they just aren't part of the package itself.

---

### Post by Doug S on 2012-12-15
> If you look on the page you linked to you'll see those packages you mentioned are not part of build-essential, but rather packages it depends onYes, thanks for the clarificaiton.

---

### Post by squakie on 2012-12-15
> **Doug S said:**
> Yes, thanks for the clarificaiton.

This whole dang thing has gotten confusing since they changed the description that shows in the package manager.  I don't know why they don't go back to the way it was so people will still just install it and let the dependencies pull in and get everything as you mentioned.  I liked it better the old way and I think the new description just makes it confusing.  Hope you have a good one! ;)

---

### Post by Doug S on 2012-12-15
> **squakie said:**
> This whole dang thing has gotten confusing since they changed the description that shows in the package manager. I don't know why they don't go back to the way it was so people will still just install it and let the dependencies pull in and get everything as you mentioned. I liked it better the old way and I think the new description just makes it confusing. Hope you have a good one! ;)I agree. I always just install build essential and move on from there.
Now, back to the OP, I still do not understand why the man page is there but the file is not, so I assume something maybe got messed up and a re-install might be required.

---

### Post by maruf7 on 2012-12-16
Installed build-essential, now 'make' is executing succesfully. Thank you all for your help.

---

### Post by squakie on 2012-12-16
And to those who say that based on the description of the package now that you don't need it, this proves it's best just to install build-essential.  You'll get the compilers, libs, headers, etc., as a default via dependencies.   Sorry I didn't have you follow through on my "couldn't hurt" in post #4 - I'm just glad you have it working now.

---

### Post by squakie on 2012-12-16
BTW - I thought Dell had posted the 1501 as dual-core, but the one I have with the Sempron 3500+ is single core - I had to look it up as it had me curious.  DVD-RW, 2gb ram (expandable), 80gb hd, Broadcom wireless.  Keep in mind it's lowly specs when looking at other things - they are probably better than it.

---

