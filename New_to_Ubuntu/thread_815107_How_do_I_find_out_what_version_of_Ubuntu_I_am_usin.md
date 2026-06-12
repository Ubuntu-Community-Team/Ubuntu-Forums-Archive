---
title: "How do I find out what version of Ubuntu I am using?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by andyanderso on 2008-06-01
I am sure that there is a very easy way to determine what version of Ubuntu I am using.  I know that I am using 8.04 but I thought I was using the 64 bit version until I tried to install picasa 64 bit and got an error message saying that I was using the 32 bit version?  Does anyone know how to check on this?

Andy

---

### Post by overdrank on 2008-06-01
> **andyanderso said:**
> I am sure that there is a very easy way to determine what version of Ubuntu I am using.  I know that I am using 8.04 but I thought I was using the 64 bit version until I tried to install picasa 64 bit and got an error message saying that I was using the 32 bit version?  Does anyone know how to check on this?

Andy

You can use the command ```
uname -a

```
Example
Linux overdrank-desktop 2.6.24-17-generic #1 SMP Thu May 1 13:57:17 UTC 2008 **x86_64** GNU/Linux

---

### Post by spiderbatdad on 2008-06-01
System>>Administration>>System tab.

Or from the terminal ```
cat /etc/lsb-release
```
or 

```
uname -r
``` any of those should say 64bit, if that is installed.

---

### Post by Nepherte on 2008-06-01
uname -r gives you the kernel version. uname -m is the correct command. If you get x86_64, you have the 64 bit edition.

---

### Post by ibutho on 2008-06-01
For checking the version, in addition to "cat /etc/lsb-release", you can also do "cat /etc/issue".

---

### Post by andyanderso on 2008-06-01
Thanks to all of you for replying...I tried all of the commands and here is the output:
[INDENT]andy@hermes:~$ uname -a
Linux hermes 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux
andy@hermes:~$ uname -m
i686
andy@hermes:~$ uname -r
2.6.24-17-generic
andy@hermes:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
andy@hermes:~$ 
[/INDENT]
So I think that the 32bit ubuntu shows up as i386?  mine shows up as i686...does that mean I am using the 64bit hardy?

thanks
andy

---

### Post by Nepherte on 2008-06-01
i686 means 32 bit. x86_64 means 64 bit.
The difference between i686 and i386 are some extensions like sse, mmx, ...

---

### Post by spiderbatdad on 2008-06-01
> **Nepherte said:**
> uname -r gives you the kernel version. uname -m is the correct command. If you get x86_64, you have the 64 bit edition.

According to the man page for uname, uname -m prints the machine hardware, so I don't believe that tells you about the version of ubuntu you are running.

uname -a is really the way to go.

---

### Post by sayakb on 2008-06-01
i386 and i686 both mean that it is a 32-bit version.

---

### Post by SunnyRabbiera on 2008-06-01
or you can do it the graphical way by opening the system monitor located under system>administration>system monitor.
the first tab in that will give you the OS info you need.

---

### Post by mac143_01 on 2008-06-01
try to do the steps that they posted it will be a great help to you..

---

### Post by andyanderso on 2008-06-01
thanks everyone that helps a ton.

---

