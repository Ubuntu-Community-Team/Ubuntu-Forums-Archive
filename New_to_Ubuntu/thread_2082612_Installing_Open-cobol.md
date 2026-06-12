---
title: "Installing Open-cobol"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by jcborland on 2012-11-10
Hi Everyone,
I'm very new to Linux and Ubuntu. I have installed the Server version, I do have some SCO Unix experience. What I want to do is install the cobol compiler and try to port some cobol source over from a SCO Unix server.

I've downloaded open-cobol-1.0 and in the README file, it says:

To generate/install OpenCOBOL :

./configure
make

Problem is when I do this I get :

root@ubuntu:/home/jbss/open-cobol-1.0# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
root@ubuntu:/home/jbss/open-cobol-1.0#

So I think I'm missing some required components but I haven't a clue how to go about installing them.

Can anyone offer some guidance?

Thanks,
Jim.

---

### Post by squakie on 2012-11-10
You need to install the build-essential package before you'll be able to compile/make.  It installs quite a few things needed, including the gcc compiler.

---

### Post by jcborland on 2012-11-10
Hi Squakie,
Thanks. Can you give me any pointers as to how I do that?
Jim.

---

### Post by SysBoot on 2012-11-10
```

sudo apt-get install build-essential

```

---

### Post by jcborland on 2012-11-10
Hi Squakie,
Your a star I've googled "install build-essentials" and I've found an instruction from this forum.
Thanks very much it's installing now.
Jim.

---

### Post by jcborland on 2012-11-10
Sysboot,
Yes thanks also that's the instruction I found. This forum is great, as I said I've not done much of this but there is lots of help out there.
Cheers,
Jim.

---

### Post by squakie on 2012-11-10
You can open a terminal window and type:

sudo apt-get install build-essential

or you can use one of the package managers.  If you go through the software center you can install synaptics package manager, which I would highly recommend.

I just downloaded this and got everything to go through the configure, the make and the make install.  It's not quite that simple.

You must install:

- libgmp -> you'll need to search the net for the download site - I just followed links and downloaded, then followed the readme there as well.

- Berkely DB components.  I installed the latest from oracle's site, then via the package manager made sure the dev lib packages were installed and also the db tcl package (it will also install tcl and something else)

You must do these before you can successfully ./configure.  There may be a couple of other things that came up in configuring/making libgmp - I just did it but already I have forgotten! (dang 60's and 70's !).

---

### Post by jcborland on 2012-11-10
Hi,
OK so I've got ./configure to run but the next command in the README is "make"
then "make check".

These produce the following:

root@ubuntu:/home/jbss/open-cobol-1.0# make
make: *** No targets specified and no makefile found. Stop.
root@ubuntu:/home/jbss/open-cobol-1.0# make check
make: *** No rule to make target `check'. Stop.
root@ubuntu:/home/jbss/open-cobol-1.0#

Any advice?

Jim.

---

### Post by jcborland on 2012-11-10
Hi Squakie,
How do I get to the software centre?

I installed libgmp so thanks again.

Jim.

---

### Post by jcborland on 2012-11-10
Hi Again,
Have any of you installed Open cobol ?
Jim.

---

### Post by HiImTye on 2012-11-10
you can install the open-cobol package directly from the repos, no compiling required
> tye@T:~$ aptitude search open-cobol
p   open-cobol                      - COBOL compiler
p   open-cobol:i386                 - COBOL compilerto install it, just do
```
sudo apt-get install open-cobol
```if you are using a server install with no X, I would recommend installing aptitude, so you can search for packages, or use the ncurses front end of it
```
sudo apt-get install aptitude
```
(I use it because I generally hate using the slow GUI managers)

---

### Post by SysBoot on 2012-11-10
> **jcborland said:**
> Hi Squakie,
How do I get to the software centre?

I installed libgmp so thanks again.

Jim.

it's probably listed as: libgmp-dev

Yup install it with 
```

sudo apt-get install libgmp-dev

```

---

### Post by SysBoot on 2012-11-10
> **HiImTye said:**
> you can install the open-cobol package directly from the repos, no compiling required
to install it, just do
```
sudo apt-get install open-cobol
```if you are using a server install with no X, I would recommend installing aptitude, so you can search for packages, or use the ncurses front end of it
```
sudo apt-get install aptitude
```
(I use it because I generally hate using the slow GUI managers)

I forgot about aptitude...Why did they take it out again?

---

### Post by HiImTye on 2012-11-10
I have no idea, it's my favorite app lol

---

### Post by squakie on 2012-11-10
One of those packages, perhaps the cobol package itself, required the curses libs as well (all of the libs need to be both runtime and development).  I should have written each step I did as I encountered it - would have made life much easier!

Indeed, I do see there is a package in the repositories for open-cobol.  If you follow the instructions given by HiImTye - you should just be able to do:

sudo apt-get install open-cobol

Hopefully, being a package and also available via apt, the dependencies (ncurses, Berkely DB stuff, etc.) will all be picked up automatically.  You may want to try that even with parts of it already installed - it may pick up the dependencies for you.

EDIT:  I just tried this and indeed it picks up the dependencies.  It doesn't, however, pick up the curses libs (so you can use Screen Section) or the Berkely DB things (so you can use indexed-sequential access method).  You'll still need to install those on your own.  Been a long, LONG time since I've done anything at all with Cobol - probably the late 70's or early 80's.  This could be something fun to play with.

---

### Post by HiImTye on 2012-11-10
the rule of thumb is to generally always check the repos first, to avoid duplicate library issues

---

### Post by squakie on 2012-11-10
For some reason, when I went looking so I could try this to try to help the OP, I must have mis-typed and didn't realize it, as I didn't find it at that time.  I also don't know - maybe it does find curses and the Berkely DB stuff - since I already had it installed it wouldn't say it needed to install it!

Thanks for the initial heads-up - the package manager always makes things so much easier.

Dave ;)

---

### Post by HiImTye on 2012-11-10
I meant for the OP, since he was trying to compile it and it's in the repos ;)

---

### Post by jcborland on 2012-11-11
Hi,
Thanks for all the help. I think I'm almost there but I'm asked to do "make test" and when I do I get:

Building module NC.../bin/sh: 1: .: Can't open ../atconfig
make: *** [NC] Error 2

Also the compile seems to be running but it won't cleanly compile the first very simple "Hello World!" program I've written, so I don't trust that it's right.

Any ideas?

Thanks,
Jim.

---

