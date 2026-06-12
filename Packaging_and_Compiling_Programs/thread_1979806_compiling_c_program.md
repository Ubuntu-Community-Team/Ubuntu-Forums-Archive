---
title: "compiling c program"
date: 2012-05-13
forum: Packaging and Compiling Programs
---

### Post by fredRansom on 2012-05-13
I have also tried to compile a simple program with gcc, but all I get is:

gcc: error trying to exec 'cc1plus': execvp: No such file or directory

no matter what I do. I recieved a suggestion that I install something called build-essential package. Did read somewhere that it was used to recompile ubuntu itself, which is not my interest at all. Basically, ubuntu does not appear to have a basic working c++ compiler with its distribution, so I'm using Windows for development, then running the programs with either wine or mono, depending upon need.

---

### Post by coffeecat on 2012-05-14
Moved to own thread. Please start your own threads.

> **fredRansom said:**
> I recieved a suggestion that I install something called build-essential package. Did read somewhere that it was used to recompile ubuntu itself, which is not my interest at all.

Build-essential is exactly what you need. If you install build-essential, the package manager will install gcc, make, g++, libc6-dev and dpkg-dev for you. These are not included in a default install because the majority of Ubuntu users do not need them. Developers know that they need to install them.

---

### Post by jfransom on 2012-05-20
Besides a c++ compiler, what does build-essential have in it? How big is the download? If it has a lot of stuff specific to ubuntu packages, can I simply not install them and still get a working c++ compiler? How nuch disk space does it need? Does Ada also come with it? Developers need to document adequately so the rest of us know what you've done.

---

### Post by Bachstelze on 2012-05-21
Do you have a 800MB hard drive to be concerned about the size, or are you just picking a fight? The information is there, if you would bother to look for it.

[http://packages.ubuntu.com/precise/build-essential](http://packages.ubuntu.com/precise/build-essential)

---

### Post by jfransom on 2012-05-24
I'm not trying to pick a fight. I hove less that 800 MB left on my little drive. I'm seeking info, but haven't been able to find it. Please either give me the info or point me to it. All I want to do is write, compile and run a few very simple c++ programs just to see what happens. I feel like I'm the one being treated mean.

---

### Post by directhex on 2012-05-25
> **jfransom said:**
> I'm not trying to pick a fight. I hove less that 800 MB left on my little drive. I'm seeking info, but haven't been able to find it. Please either give me the info or point me to it. All I want to do is write, compile and run a few very simple c++ programs just to see what happens. I feel like I'm the one being treated mean.

I have no idea where this 800 meg figure came from, or why you're  refusing to fix your problem.

An absolute bare-minimum Ubuntu install (i.e. a chroot of the base system, without things like a kernel, let alone a GUI) is 192 meg.

Installing build-essential, which brings in stuff like gcc, takes an extra 118 meg, of which 25% is Perl (which you are going to have already).

And hell, even THAT is more than you need. The error you report comes when you don't have a g++-X.Y package installed appropriately, e.g. g++-4.6 contains /usr/lib/gcc/x86_64-linux-gnu/4.6/cc1plus

The bit that just makes you come across as weird is "Ubuntu doesn't come with a C++ compiler so I'm using Windows" - know what? Windows doesn't ship a C++ compiler by default either.

---

### Post by zombifier25 on 2012-05-25
OK people, let's not turn this into a hate argument.
Back to topic... like what the above has posted, install build-essential and you should be compiling programs with g++ in no time. Or you may only need g++ in order to compile simple C++ programs, I can't verify this for you. If installing g++ only do not solve the problem, go for the full thing.

---

### Post by fredRansom on 2012-05-30
OK, I installed build-essential.  It seems to contain a lot. I discovered perl. But, what all does it have? C++ works nicely.
As a matter of fact, I had less than 700 MB left on the hard drive on this aging lap top. It's true that MS Windows doesn't come with C++, but finding MingW, Watcom and C++ Express is simple, easy to download, and install.
Don't get me wrong. I like Ubuntu. It comes up and shuts down quickly, very good for WiFi hot spots. It comes with my favorite office suite, has many nifty attributes and come with a good sudoku puzzle. It's a fast, excellent operating system. But, I stand by my guns: your documentation needs a lot of work. What, for instance, are all the items in build-essential, or where can I find this information?

---

### Post by bruno9779 on 2012-05-30
I think your approach is wrong.

You have all the info you need, you just need to learn how to access them.

example:

```
man apt-get
```

gives you the man pages of apt-get. from there you could have learnt that -s flag simulates install and -V is verbose.

Thus:

```
sudo apt-get install -Vs build-essential
```

Would have given you most of the info you need. That and google.

---

### Post by directhex on 2012-05-30
> **fredRansom said:**
> What, for instance, are all the items in build-essential, or where can I find this information?

```
directhex@dream:~$ apt-cache depends build-essential
build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
  Depends: dpkg-dev
  Conflicts: build-essential:i386
```

---

### Post by zayid on 2012-05-31
I'm also facing a similar problem and i've installed build-essentials to the latest version  but whenever i try to run a program wit gcc it doesn't recognise #include <iostream> or #include <conio> libraries maybe there are more but it's just these two i need ATM. Also, i'm a newbie both to Linux & programming. Attached here is a  code for a calculator that is to divide two numbers & error i get but it isnt working & i don't want to do it on windows, thanks.

---

### Post by gnusci on 2012-05-31
This is a C++ library #include <iostream>, compile with g++

This is a Win2 library #include <conio>.

---

### Post by zayid on 2012-06-01
Thanks!!!! it worked

---

### Post by fredRansom on 2012-06-16
Thanks. I did find the Ubuntu Wiki.

---

