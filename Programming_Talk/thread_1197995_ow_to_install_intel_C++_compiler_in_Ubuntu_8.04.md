---
title: "ow to install intel C++ compiler in Ubuntu 8.04"
date: 2009-06-26
forum: Programming Talk
---

### Post by lidengdeng on 2009-06-26
Hi guys:

How to install intel C++ compiler in Ubuntu 8.04?

Some documents are found online but not in details. So could you please kindly describe it step by step. I am newbie to programming in Linux. Thanks

---

### Post by Mirge on 2009-06-26
[http://ubuntuforums.org/showthread.php?p=5405429](http://ubuntuforums.org/showthread.php?p=5405429)

---

### Post by kjohansen on 2009-06-26
> **Mirge said:**
> [http://ubuntuforums.org/showthread.php?p=5405429](http://ubuntuforums.org/showthread.php?p=5405429)

That is for g++ the poster wants icc

[http://crazyprogrammerblog.blogspot.com/2008/11/install-intel-compilericc-in-ubuntu-810.html](http://crazyprogrammerblog.blogspot.com/2008/11/install-intel-compilericc-in-ubuntu-810.html)

---

### Post by Mirge on 2009-06-26
Ahh sorry, tylenol PM Kickin in :)

---

### Post by kixome on 2009-06-26
sudo apt-get install g++

---

### Post by kixome on 2009-06-26
you can also google code blocks if you want a nice GUI compiler, its in the jaunty repos but not hardy

In terminal, you may want to type man g++ to learn how to use, it is actually very easy just sudo g++ <source file> to compile

---

### Post by jespdj on 2009-06-27
> **kixome said:**
> sudo apt-get install g++
Again, that is to install GCC, not the Intel C++ compiler... :rolleyes:

---

### Post by monkeyking on 2009-06-27
Just get the the installer from the intel webpage,
you need to sign up to get a license key.

Its free so no problem,

then  run the installer as sudo, its much less hassle to setup.

Then depending on where you have installed it,
you need to source iccvars.sh with an argument telling you which platform you want to compiler for

like

source iccvars.sh ia64

But there  some dragons,
you need to export LANG=C before it will  work.


post again if you have problems.

```

#i've installed the intel compiler suite to /opt/intel
cd /opt/intel/Compiler/11.0/074/bin
export LANG=C
source ./iccvars.sh ia32

```

now you kan use icc and icpc

good luck

---

### Post by Krupski on 2009-06-27
> **lidengdeng said:**
> Hi guys:

How to install intel C++ compiler in Ubuntu 8.04?

Some documents are found online but not in details. So could you please kindly describe it step by step. I am newbie to programming in Linux. Thanks

Not questioning your choice... just curious... why do you specifically want the Intel compiler over GCC?

---

### Post by monkeyking on 2009-06-27
> **Krupski said:**
> Not questioning your choice... just curious... why do you specifically want the Intel compiler over GCC?

I cant speak for the op,
but I've installed intel toolchain on all our computers,
depending on the program of cause,
we have experienced a cut of between 5-70%.

I normally just use gcc for everything, but once I'm done,
I check how fast the intel is.


But its very program specific the speedups,
the extreme case of 70% was on a c/c++ with a huge optimization library imported by f2c.
The cpu was a xeon 5450, and I mainly think the speedups was due to the intel loop vectorization beeing much more mature.

But who knows.

On a sidenote I've also installed the sun compiler suite,
the errors are much more elaborate, but it has been somewhat slower than gcc and intel.

---

### Post by lidengdeng on 2009-06-30
Thanks for all your help.
And the icc is installed and works well.

The reason I wanna install Intel compiler is that it is needed by an open source. Otherwise the open source couldn't be compiled.

---

