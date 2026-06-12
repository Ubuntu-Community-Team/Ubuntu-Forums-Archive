---
title: "Find difficult configuring the kernel"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by OsOsOs on 2011-10-22
I'm new to Ubutu and I wanted to try compiling a simple kernel module to display "Hello World" by referring the book, Linux Device Drivers by Rubini. 

I have already installed Ubutu 8.10.

As the first step I downloaded linux-2.6.39.4 from kernel.org mirror network and extracted it into /usr/src.

As the next step I tried to configure the kernel using, 
/sur/src/linux-2.6.39.4#make menuconfig 

It shows me two errors and says "Unable to find the ncurses libraries or the required header files" and to install ncurses and try again. 

I tried to install by using
/sur/src/linux-2.6.39.4# apt-get install libncurses-dev 

It again shows me an error "Couldn't find package libncurses-dev"

I'm glad if you can help me in finding a solution.

---

### Post by gsmanners on 2011-10-22
Try this:

```
apt-cache -n search libncurses
```

That should tell you what you're missing.

---

### Post by OsOsOs on 2011-10-22
> **gsmanners said:**
> Try this:

```
apt-cache -n search libncurses
```

That should tell you what you're missing.

Thanks for your prompt reply.

I checked it and it gave,
libncurses5 - Shared libraries for terminal handling
libncursesw5 - Shared libraries for terminal handling (wide character support)

Then I checked with
/usr/src/linux-2.6.39.4#apt-get install libncurses5

and it says,
libncurses5 is already the newest vrsion.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Is there any other way of installing libncurses5 ?

---

### Post by gsmanners on 2011-10-22
Err... No, what you want is the -dev package.

---

