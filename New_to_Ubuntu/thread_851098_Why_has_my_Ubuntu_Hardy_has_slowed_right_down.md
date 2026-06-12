---
title: "Why has my Ubuntu Hardy has slowed right down?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Mark.H on 2008-07-06
Hey all..

Hi all...

I have used various Ubuntu editions on the very same computer I am using at the moment but have never had it slow down to a painful crawl as it has over the last week..

Admittedly my PC is no powerhouse but it is capable of running Ubuntu at an ecceptable speed so this is why I would like to know if anyone can suggest any tweaks or tips to speed up my system??

Even my Firefox 3 browser takes an age to load a page!!.. and also can anyone suggest how i can speed up my boot time as well??
It actually freezes for about 10 second, about a quarter of the way along the splash screen loading bar..

Cheers for now

mark..

---

### Post by LinuxRocks713 on 2008-07-06
> **Mark.H said:**
> Hey all..

Hi all...

I have used various Ubuntu editions on the very same computer I am using at the moment but have never had it slow down to a painful crawl as it has over the last week..

Admittedly my PC is no powerhouse but it is capable of running Ubuntu at an ecceptable speed so this is why I would like to know if anyone can suggest any tweaks or tips to speed up my system??

Even my Firefox 3 browser takes an age to load a page!!.. and also can anyone suggest how i can speed up my boot time as well??
It actually freezes for about 10 second, about a quarter of the way along the splash screen loading bar..

Cheers for now

mark..

Source: [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

Try:

```

sudo swapoff -a

```

If it gets worse, try:

```

sudo swapon -a

```

hope it helped:-)

---

### Post by Mark.H on 2008-07-06
Thanks for you reply..

i tried the first command: sudo swapoff -a

But I got this error message:

swapoff: /dev/sda5: Cannot allocate memory

can you tell me abit more about these commands as well please?

---

### Post by werries on 2008-07-06
1. those turn off/on the swap partitions you should have had when ubuntu was installed. (if you chose guided it did this automatically)
2. what are your system specs? especially your memory/processing.

---

### Post by AndrewTheArt on 2008-07-06
System -> Administration -> System Monitor

See what's chewing up your RAM or CPU. Excessive disk activity can also slow your computer down to a halt. Try KSysMon to view this kind of data.

---

### Post by Berean on 2008-07-06
The assumption here is that the problem lies in the software.  Go to terminal and type sudo lshw (you'll need to enter your password) and see if the output of your hardware is as you expect.  I had  a similar incident recently and it transpired that one of my RAM modules was damaged so I was only running my system on half RAM, which obviously slowed it down considerably.  The likelihood is that the problems you're encountering are not hardware related, but at least this will rule out hardware problems.  Hope this helps.

---

### Post by AndrewTheArt on 2008-07-07
There is also an interesting program called "preload" - 

> **Preload** is an adaptive read-ahead daemon. It monitors applications that users run, and by analyzing this data, predicts what applications users might run, and fetches those binaries and their dependencies into memory for faster startup times. 

[http://www.debianadmin.com/load-applications-quicker-in-ubuntu-using-preload.html](http://www.debianadmin.com/load-applications-quicker-in-ubuntu-using-preload.html)

```
sudo apt-get install preload
```

---

