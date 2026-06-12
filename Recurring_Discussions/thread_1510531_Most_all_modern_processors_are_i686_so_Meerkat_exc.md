---
title: "Most all modern processors are i686 so Meerkat excluding &lt;686 won't matter much"
date: 2010-06-15
forum: Recurring Discussions
---

### Post by NUboon2Age on 2010-06-15
When I saw [this article]("http://www.webupd8.org/2010/06/ubuntu-1010-maverick-meerkat-wont-run.html") I was worried that I wouldn't be able to help my friends w/ older <686 machines run Ubuntu.  

But I ran ```
uname -m
```  and found my 5 year old laptop has a 686 and then read [this article]("http://en.wikipedia.org/wiki/P6_%28microarchitecture%29#P6_based_chips") that made it clear to me that unless you're running a >10 year old machine you'll have nothing to worry about.  Looking at [this chart it looks like Tillamook]("http://www.techarp.com/showarticle.aspx?artno=347&pgno=5") was probably the last popular intel chip that would be impacted by this.  

I guess the Geode low power i586 chip is the only real outstanding question mark with this approach.

---

### Post by Bachstelze on 2010-06-15
Oh well, time to switch my last Ubuntu Geode to OpenBSD, I guess.

*EDIT:* [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/)

Oh, the irony. Will the ISOs be labeled "i386" too? :p

---

### Post by Shining Arcanine on 2010-06-15
> **NUboon2Age said:**
> When I saw [this article]("http://www.webupd8.org/2010/06/ubuntu-1010-maverick-meerkat-wont-run.html") I was worried that I wouldn't be able to help my friends w/ older <686 machines run Ubuntu.  

But I ran ```
uname -m
```  and found my 5 year old laptop has a 686 and then read [this article]("http://en.wikipedia.org/wiki/P6_%28microarchitecture%29#P6_based_chips") that made it clear to me that unless you're running a >10 year old machine you'll have nothing to worry about.  Looking at [this chart it looks like Tillamook]("http://www.techarp.com/showarticle.aspx?artno=347&pgno=5") was probably the last popular intel chip that would be impacted by this.  

I guess the Geode low power i586 chip is the only real outstanding question mark with this approach.
There are other distributions that still support older processors. The main one I know is Gentoo Linux. Perhaps you could help your friends switch to it if it turns out that they are using older processors.

---

### Post by Frogs Hair on 2010-06-15
I saw that article last week and was wondering how long it would take to get here. Thanks for posting it.

---

### Post by WinterRain on 2010-06-15
As far as I know, you can still install it on 586 computers. You just can't do it the other way around. (586 OS on a 686 PC)

---

### Post by -grubby on 2010-06-15
> **WinterRain said:**
> As far as I know, you can still install it on 586 computers. You just can't do it the other way around. (586 OS on a 686 PC)

You have it backwards

---

### Post by -grubby on 2010-06-15
Somewhat recently, Ubuntu announced that [Maverick is going to be compiled for i686](http://www.webupd8.org/2010/06/ubuntu-1010-maverick-meerkat-wont-run.htm) (previously, it was i386.) What does this mean? Any processor not using the i686 arch or higher is not going to work with Meerkat. How does this affect you? It probably doesn't.

On 15 November 1995, The Pentium Pro was released, the first i686 processor. It became much more common with the Pentium II in 1997. Since then, almost every Intel processor has supported i686. It's been in AMD's offerings since at least the original Athlon in 1999.

So, practically every CPU made in the past 10 years or so supports i686 and shouldn't have problems. However, I've heard concerns that a few netbooks CPUs don't support i686 - I'll gladly add any more information on this into the OP if someone brings up something more specific.

EDIT: Apparently the Geode LX800 is only i586.

---

### Post by RiceMonster on 2010-06-15
Well I thought the major distros should have moved to i686 earlier anyway. So I agree.

---

### Post by cariboo on 2010-06-15
I've got an Atom N270, i686 runs just fine, I've even run X86_64 on an Atom 320.

---

### Post by SunnyRabbiera on 2010-06-15
No issue here, though this may cause issues with apps still coded for i386

---

### Post by cariboo on 2010-06-15
Merged two threads on essentially the same subject.

---

### Post by Bachstelze on 2010-06-15
> **-grubby said:**
> 
EDIT: Apparently the Geode LX800 is only i586.

I even have an i486!

[http://www.amd.com/epd/processors/4.32bitcont/14.lan5xxfam/24.lansc520/](http://www.amd.com/epd/processors/4.32bitcont/14.lan5xxfam/24.lansc520/)

(Yes, despite its name, the AMD 5x86 series of CPUs is actually 486.)

---

### Post by squilookle on 2010-06-15
I believe Arch is aimed at i686, so looking at how Arch users get on would potentially be a good measure of whether the switch would be a problem. 

My 5 year old Toshiba laptop ran Arch absolutely fine. It struggled with the default Ubuntu install for quite some time due to the amount of memory it needed, regardless of the Arch. (When I say struggled: I mean it wasnt the fastest. By many peoples standards it probably would have been fine... but there you go)

---

### Post by Bachstelze on 2010-06-15
```
firas@elise:~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l

firas@elise:~$ cat /proc/cpuinfo 
processor       : 0
vendor_id       : Geode by NSC
cpu family      : 5
model           : 9
model name      : Unknown
stepping        : 1
cpu MHz         : 233.299
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu tsc msr cx8 cmov mmx cxmmx
bogomips        : 466.59
clflush size    : 32

```

Oh, well... Elise will lose her "Powered by Ubuntu" sticker. :p

---

### Post by sidzen on 2010-06-15
Slackware, here I come!

---

### Post by K.Mandla on 2010-06-15
> **NUboon2Age said:**
> When I saw [this article]("http://www.webupd8.org/2010/06/ubuntu-1010-maverick-meerkat-wont-run.html") I was worried that I wouldn't be able to help my friends w/ older <686 machines run Ubuntu.  ...
I was only [the least bit concerned]("http://kmandla.wordpress.com/2010/06/10/not-particularly-worried-2/") when I read that. Anyone who has an original 586 machine, meaning one from 10 years ago, probably doesn't really consider Ubuntu to be a strong solution for using it.

There are other, better ultralight operating systems for hardware of that age. Ubuntu isn't the best thing for everybody or everything.
> **squilookle said:**
> I believe Arch is aimed at i686, so looking at how Arch users get on would potentially be a good measure of whether the switch would be a problem. ...
On the other hand, there is an [Arch project for i586s]("http://archlinux-i586.org/"), which gets some attention. So it may be that ferocious 586-fans take their own approach to the Ubuntu machine. ;)

---

### Post by Dragonbite on 2010-06-15
Hey, as lont as my PIIIs (servers) and up (P4, Centrino, etc.) are supported I won't notice a difference.

Now if they also fix the Intel 855 GPU issue, then I'll be ecstatic!  (the patch is good, but not perfect)

---

### Post by doorknob60 on 2010-06-15
Fine with me. My only i586 PC is a Laptop from 1999 running Debian, barely. Ubuntu would be an awful idea on that old thing, probably wouldn't even fit on the HD. And the CD drive is busted (and I don't think I can boot from USB lol), so I wouldn't be able to install it anyway. I do wish Arch would work though (I know about Arch spinoffs for i586, but it's not worth the trouble, especially without a CD drive. And I got a new laptop too :P)

---

### Post by Shining Arcanine on 2010-06-16
Major distributions can support different versions of x86 as separate platforms like they support different versions of ARM as separate platforms. There is no need to lump the i686 people into the i386 group or eliminate the i386 group for the sake of the i686 group.

---

### Post by Bachstelze on 2010-06-16
> **K.Mandla said:**
> I was only [the least bit concerned]("http://kmandla.wordpress.com/2010/06/10/not-particularly-worried-2/") when I read that. Anyone who has an original 586 machine, meaning one from 10 years ago, probably doesn't really consider Ubuntu to be a strong solution for using it.

1) As said previously, i586 processors are still produced today for embedded devices.

2) Ubuntu is just as good for this as any other distro. I think it's a shame, I like Ubuntu, the machine works perfectly with it, but I'm going to have to switch it eventually. I wonder what benefit they indend to gain from that... i686 "optimizations"? Come on now, the handful of applications that would really benefit from that are those doing some heavy computations, no one probably uses 32-bit machines anymore for that.

---

### Post by Dragonbite on 2010-06-16
> **Bachstelze said:**
> 1) As said previously, i586 processors are still produced today for embedded devices.

2) Ubuntu is just as good for this as any other distro. I think it's a shame, I like Ubuntu, the machine works perfectly with it, but I'm going to have to switch it eventually. I wonder what benefit they indend to gain from that... i686 "optimizations"? Come on now, the handful of applications that would really benefit from that are those doing some heavy computations, no one probably uses 32-bit machines anymore for that.

They could test what "benefits" they could get by using Gentoo and using "use" flags.

---

### Post by Bachstelze on 2010-06-16
> **Dragonbite said:**
> They could test what "benefits" they could get by using Gentoo and using "use" flags.

Eh, no, completely different things. The USE flags in Gentoo are mostly used to control which optional features are compiled in the software, and which aren't. Nothing to do with architecture-dependent optimisations. Those are set, like in any other system, with the CFLAGS environment variable, usually in make.conf.

---

