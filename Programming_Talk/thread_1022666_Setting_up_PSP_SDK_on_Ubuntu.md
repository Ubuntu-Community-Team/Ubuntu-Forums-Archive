---
title: "Setting up PSP SDK on Ubuntu?"
date: 2008-12-27
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-27
I know enough C to make simple games and software.

And I got a PSP with m33-5.00 cfw. But it lacks of great games that has to be done.


There are only Windows tutorials of pspsdk, which all use Linux emulators(wtf?).

So maybe the psp sdk is originally made for Linux? If so, I want it.


Instructions on how to compile it on Ubuntu Hardy? Thanks.

---

### Post by crazyfuturamanoob on 2008-12-28
I found a guide to compile psp toolchain on Ubuntu, and I got it compiled & installed.

But because there's not a single tutorial on how to install psp sdk, I just have to guess what to do.

Here's what I have tried for now:


So I went into pspsdk directory, ran configure as sudo. Then tried to make, but permissions didn't allow.

After correcting permissions with "sudo chmod -R 777 pspsdk_1.0-beta2/", ran "make" in terminal.

But after a while, make reported this error and didn't want to proceed:
> 
stdlib.c:124: error: redefinition of &#8216;atoi&#8217;
./stdlib.h:100: error: previous definition of &#8216;atoi&#8217; was here
Did I accidentally do something wrong or is that just crappy coding?

I looked at the stdlib.h and stdlib.c files but they were so HUGE and messy I got no idea what's the problem there.


I suck at programming, debugging, troubleshooting and doing stuff like this.

How am I supposed to compile this without instructions? I need help. :(


Edit: 
Attempt #2:

I found a file called README from the pspsdk directory:
> 
  Installation from source

    PSPSDK uses the GNU autotools (autoconf and automake) for its build
system.  To install PSPSDK from a source distribution, run the following
commands after unpacking it:

    ./configure
    make
    make doxygen-doc
    make install

Deleted whole psp sdk folder, and re-unpacked it from the zip I still have.
I ran "./configure" (without sudo this time). Then make, but make couldn't proceed because of the same error as before.

---

### Post by skullmunky on 2009-01-03
let me know if you get this working, I'd love to try it out too.  I've been having fun with Nintendo DS development, which looks like it's a little easier to get set up.

first answers:

- you don't have to do ./configure as sudo.  the configure and make steps are usually done as the normal user, and only the make install step has to be sudo.  if you sudo ./configure, then the resulting Makefile will be owned by root, which is why make didn't give you permissions.

- where that error comes from: you're compiling the standard library (stdlib) for the PSP.  atoi() is a function that converts a string to an int.  this is such a core part of the system that it's unlikely to be a coding error, so it's more likely something else.

I see that pspsdk relies on the psp toolchain - did you install that?

explanation: a "toolchain" is the compiler and linker that you need in order to build an executable for a particular hardware platform.  on your linux box the different parts of gcc (the C compiler, the linker, the libtool, etc) are already there and it's why you can compile anything at all.  To compile for the PSP you need a whole other toolchain with its own compiler, linker, etc.  Then, on top of that, you have libraries of C functions that make it easier to write useful code.  That's what the pspsdk is.  

probably where that error came from is you didn't have the psp toolchain installed, so when you went to build the pspsdk the stdlib it was trying to make conflicted with the stdlib for your linux box.

Hm, so let's see what this does.  Holy moly, that's a lot of compiling, this'll take a while...

Here's what I did:

0. made a directory to keep all this in: ~/programming/psp

1. downloaded the PSP toolchain: 

[http://ps2dev.org/psp/Tools/Toolchain/]("http://ps2dev.org/psp/Tools/Toolchain/")

2. moved that file into ~/programming/psp, extracted it

3. you have to install some tools first:

```

sudo apt-get install bison flex autoconf

```

4. then you must set up your paths, as it says in the readme:

```

export PSPDEV=~/programming/psp/pspdev
export PATH=$PATH:$PSPDEV/bin

```

5. now run the installer in the psptoolchain directory:
```

./install.sh

```

6. Fail

it should download and compile lots and lots of things.  However, for me it died after a while:

```

psp-ar  rc ./libgcov.a libgcc/./_gcov.o libgcc/./_gcov_merge_add.o libgcc/./_gcov_merge_single.o libgcc/./_gcov_merge_delta.o libgcc/./_gcov_fork.o libgcc/./_gcov_execl.o libgcc/./_gcov_execlp.o libgcc/./_gcov_execle.o libgcc/./_gcov_execv.o libgcc/./_gcov_execvp.o libgcc/./_gcov_execve.o libgcc/./_gcov_interval_profiler.o libgcc/./_gcov_pow2_profiler.o libgcc/./_gcov_one_value_profiler.o 
*** buffer overflow detected ***: psp-ar terminated 

```

That's lame.  ar is the Archive tool, which is used to combine multiple object files into a single library archive.  psp-ar is the special version of ar that the psptoolchain installer made, and it shouldn't have buffer overflows.  The error happens while it's trying to build gcc, the C compiler.

Anyway, try this out yourself, see if you get further than me.  If not, try asking on the ps2dev.org forum.

---

### Post by efexD on 2009-01-04
I didn't know you could make custom applications for 5.0 firmware? How did you manage that?

---

### Post by red_team316 on 2009-01-04
somehow I would lay a bet that the atoi error is crappy programming. Back when I was using Windows, I wrote a game engine. Not too long ago, I decided to try to port it to linux as it was written in SDL. Well, everything was fine except that I had used atoi all over the place. I replaced all occurances of atoi with sprintf and all was good. I did some looking on the net and found out that using atoi isn't a good idea and that it is non-standard and pretty much windows specific.

example of converting atoi to sprintf
```

//itoa(DaysTotal,timepassed,10);
sprintf(timepassed, "%d", DaysTotal);

```

It seems kind of odd that stdlib is throwing the errors. I'm guessing there is an stdlib included with the toolchain? If so, you might try replacing it with the GNU stdlib files. 

I haven't mucked around with the psp toolchain for quite some time. I also always thought it was weird that you had to use cygwin on windows lol. I really hope you get everything squared away as far as the toolchain goes, as I'd like to see a decent how to on it for ubuntu.

---

### Post by skullmunky on 2009-01-04
I think the atoi() error is not coming from using atoi(), but during the process of actually trying to compile it (stdlib.c) while building the toolchain.

Is there a binary installer for the psp toolchain and pspsdk?  maybe that'd be easier.

What's a 5.0 firmware?  :)

---

### Post by efexD on 2009-01-04
> **skullmunky said:**
> I think the atoi() error is not coming from using atoi(), but during the process of actually trying to compile it (stdlib.c) while building the toolchain.

Is there a binary installer for the psp toolchain and pspsdk?  maybe that'd be easier.

What's a 5.0 firmware?  :)

I Don't know. I just wish i didn't have a slim so i could make programs for my PSP >.>

---

### Post by red_team316 on 2009-01-04
efeXor, Look here. It's been awhile because DEVHOOK was being actively developed when I was last on the scene. 1.50 Kernel Addons? I would do some research on what he's done recently before coming to the conclusion that slims are paperweights.

[http://alek.dark-alex.org/filez/dax/](http://alek.dark-alex.org/filez/dax/)

---

### Post by efexD on 2009-01-04
Yeah but they want you to buy/make some pandora battery for the slim so it downgrades...

---

### Post by red_team316 on 2009-01-05
efeXor: no guts, no glory.....and no homebrew :D

I looked at the PSPWiki and the hack itself doesn't really look complicated at all. In fact you have less of a chance of bricking it than I certainly did. There weren't any 'universal unbrickers' when I downgraded ages ago.


crazyfuturamanoob: Most likely you've got the crappy download from the main site, which is really old and must have some bugs in it or something too. I couldn't get it to work even compiling the toolchain from the prepackaged one. So, I grabbed the latest everything from the SVN instead and it compiled just fine.

Try this:
> 
I have a separate partition that I mount at mydata, so my paths are a little different than everyone elses. I just created a psp folder there to keep everything separate from the
libs in ubuntu. I then created an SVN folder for doing all of the checkouts. I also made a pspdev folder so when I start running scripts everything will be in place.


sudo apt-get install build-essential autoconf automake bison flex libncurses5-dev libreadline5-dev libusb-dev texinfo libgmp3-dev libmpfr-dev subversion gcc-4.2

In the SVN folder:
svn co svn://svn.ps2dev.org/psp/trunk/psptoolchain psptoolchain

Copy .bashrc from /etc/skel and drop in in your home directory if you don't have one.

Open your .bashrc up and paste this into the end of the file:

echo "SETTING PSP ENVIRONMENT VARIABLES..."
export PSPDEV="/home/jpg/mydata/psp/pspdev"
export PSPSDK="$PSPDEV/psp/sdk"
export PATH="$PATH:$PSPDEV/bin:$PSPSDK/bin"

save it.

Also open up the toolchain-sudo.sh and make sure the corresponding export lines are there too.

save it.

Open up a terminal in the psptoolchain directory and you should see the echo line. If you didn't open up a new terminal and just cd to there then do:

source ~/.bashrc

Run the toolchain script:

sudo ./toolchain-sudo.sh

If the script didn't exit with any errors, then you've got the toolchain installed now.

On to the goodies/libraries...

chown -R jpg:jpg pspdev (because we ran the toolchain with sudo. If we don't chown now, the rest of the libs wont install unless your sudoing everything or something crazy)

In the SVN folder:
svn co svn://svn.ps2dev.org/psp/trunk/pspsdk pspsdk

./bootstrap
./configure
make
make install

No errors? You got a basic pspsdk now. Why not install SDL and some of the other goodies. You can browse the svn by going here in firefox:
[http://svn.ps2dev.org/listing.php?repname=psp&path=%2Ftrunk%2F&rev=0&sc=0](http://svn.ps2dev.org/listing.php?repname=psp&path=%2Ftrunk%2F&rev=0&sc=0)



I even got it to build on 64-bit(see pic). Hopefully that won't cause any problems when compiling an EBOOT.PBP lol

---

### Post by efexD on 2009-01-05
I guess i'll be buying a universal downgrader.
Hope it's worth it to use homebrew..

---

