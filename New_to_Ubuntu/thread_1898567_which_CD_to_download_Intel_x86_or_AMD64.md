---
title: "which CD to download Intel x86 or AMD64"
date: 2011-12-21
forum: New to Ubuntu
---

### Post by kaloasd on 2011-12-21
I want to reinstall my Ubuntu 11.04 but am having trouble deciding which CD to choose. 
Can anyone help me find out the architecture of my processor.

I want to download the CD from here:
[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

---

### Post by DogMatix on 2011-12-21
Incorrect info. removed.

**EDIT:** Sorry the command I previously gave will not tell you if your processor is 32 or 64bit. My bad. See satanselbow's post #4 below.

---

### Post by oldos2er on 2011-12-21
```
cat /proc/cpuinfo
``` and look for the 'lm' flag.

---

### Post by satanselbow on 2011-12-21
you can find if your processor is 64bit with:

```
lshw
```

near the top of the output you will find your cpu(s) - if it says "width: 64bit" then go with the amd64 which is the 64 bit version. Otherwise go for the x86. It does not matter whether the actual chip in your machine is Intel or amd - the bit width is what matters.

32bit will run on a 64bit but the reverse is not true ;)

---

### Post by satanselbow on 2011-12-21
> **DogMatix said:**
> Open a terminal window and type

```
 uname -a
```

That will only tell you the bit width of your **currrent** kernel.

---

### Post by satanselbow on 2011-12-21
> **oldos2er said:**
> ```
cat /proc/cpuinfo
``` and look for the 'lm' flag.

couldn't remember that one off the top of my head :popcorn:

---

### Post by DogMatix on 2011-12-21
> **satanselbow said:**
> That will only tell you the bit width of your **currrent** kernel.

Sorry yes you're absolutely correct. I apologise.

---

### Post by kaloasd on 2011-12-22
I used 
```
lshw
```
and it showed the CPU width as 64 bits
but I was wondering tough why does it show
```
 description: Computer
    width: 32 bits

```
above

---

### Post by satanselbow on 2011-12-22
That will be because your **current** ubuntu installation is a 32bit version; you can verify that with the other command previously listed ie:

```
uname -a
```

Which will list details of your current version and kernel as they are now - not the potential capabilities of your hardware (which is why we used lshw or cpuinfo earlier)

---

### Post by kaloasd on 2011-12-22
thank you all

---

