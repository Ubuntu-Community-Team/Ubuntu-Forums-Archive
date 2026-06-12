---
title: "Is there any cpu-z for ubuntu"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by shawnansasio on 2008-07-02
Hi I was wondering if there was any program like cpu-z for ubuntu and/or Fedora.

Pretty much I just wanted to know if i have an SSE2 compatable computer , and if the new ram I inserted works.

Thanks.


______________________________________________

If you don't Know what cpu-z is check this out:

[http://fileforum.betanews.com/detail/CPUZ/966149377/1](http://fileforum.betanews.com/detail/CPUZ/966149377/1)

---

### Post by fatality_uk on 2008-07-02
This looks like it may be close to what you need.
[http://www.kde-apps.org/content/show.php?content=42435](http://www.kde-apps.org/content/show.php?content=42435)
Only thing is, I can't find a debian package for it. That means you may have to compile it yourself.

---

### Post by kevdog on 2008-07-02
That app is only for KDE.  Any gnome based app?

---

### Post by Steveway on 2008-07-02
Why not just:> cat /proc/cpuinfo?
And for Ram just use Memtest.

---

### Post by stchman on 2008-07-02
> **Steveway said:**
> Why not just:?
And for Ram just use Memtest.

Only problem is that when you overclock a CPU Ubuntu simply reads the CPU ID string and displays the default clock.

Lets say you overclock a 2.4GHz CPU to 3.0 GHz, Ubuntu will still report 2.4GHz as it is simply reading the CPU ID not ACTUAL CPU frequency.

---

### Post by shawnansasio on 2008-07-02
Thanks everyone.

The only problem is i want to find out if the memory was compatable in fedora not ubuntu and I really don't want to compile any programs form source.

---

### Post by |{urse on 2008-07-02
I thought OSX was the only sse2 incompatible os. Not counting older unmaintained oses.

you can achieve all that information with

cat /proc/cpuinfo

I've seen people suggesting gkrellm, this would be helpful as it shows cpu usage/temp and a few other helpful stats. So far as core voltage and clock speed, idk? 

yum -y install gkrellm
yum -y install lm-sensors (or maybe it's lmsensors, i forget)
gkrellm -demo

the -demo runs gkrellm with all available info.

---

### Post by yowshi on 2008-07-14
i am sick and tired of looking for these cpu-z alternatives threat and seeing crap like "uh just do a cat /proc/cpuinfo"


that command is NOT repeat NOT an alternative to it. there is no tool built into linux which will give you all the info cpu-z can. i mean info about stuff overclockers are interested in. i havent used  cpu-z in a while so i cant remember everything it shows but i damn well know i can seem to find my fsb info in any command i have read in the last 2 dozen cpu-z alternatives thread.

nor can i find my clock speed.

---

### Post by mikebravo on 2009-07-06
yowshi,
On July 14, 2008 you posted about being unable to find a Linux Ubuntu equivalent to the windows utility CPU-Z.  I would like to know if in the intervening time you have found what you wanted because I want it also. I am interested in learning about the RAM in my current computer e.g. voltage, speed, and timing requirements like CAS latency. CPUZ provides this and more in a easy to understand package. Surely there is an equivalent in the Ubuntu community that does not require futzing around with the command line.

---

