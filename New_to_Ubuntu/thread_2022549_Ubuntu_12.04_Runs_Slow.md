---
title: "Ubuntu 12.04 Runs Slow"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by DoctorVarney on 2012-07-11
A few people have said to me that Ubuntu 12.04 is slow and that 11.10 works faster and is generally better.  Is there any truth to this and if so, how would I go about downgrading to Ubuntu 11.10 ?  I'm currently running 12.04 32bit and to be honest, it isn't even as fast as Windows XP on my AMD Athlon 64 988 Mhz machine with 2GB RAM.

I chose Linux because I wanted to get away from Windows, as it slows down significantly after a few weeks and Ubuntu is just nicer to use and does seem more powerful in essence.  It is, however, not the fastest moving operating system I've ever used and one person I know suggested 11.10 was great and described 12.04 as "A load of rubbish"
( except he used words I'm not allowed to type here ). :)

Basically, it's very difficult to separate first blush user-experience from technical knowledge about the software.  Personally, I have no way of verifying the truth in these matters, after a total of three days experience with Linux.  So I thought I'd put it to the more experienced readers here, to see what you think.

---

### Post by lolpenguin on 2012-07-11
For a new user like you, there is no reason not to use the latest upstream stable, that is, currently Ubuntu 12.04 LTS. This is a Long Term Support release, and is the first desktop version to be supported for 5 years.
Your AMD processor is a major bottleneck for performance. Ubuntu is the most resource-heavy. You could log in the Ubuntu 2D session, which does not require 3D acceleration and uses less resources. (If you don't like Unity, then consider Kubuntu)
If you already are, disregard that and try Xubuntu or Lubuntu, which use even less resources.

---

### Post by black veils on 2012-07-11
like **lolpenguin** said, Xubuntu would be a possibility for you. i recommend trying it, there are plenty of options, and you can use the same applications (but you might need to install them).

alternatively, just open the Terminal and copy-paste the following ```
sudo apt-get install xubuntu-desktop
``` to install the GUI (desktop) Xubuntu uses, it will be added to your current Ubuntu system, as an alternative desktop.

you choose your Xubuntu desktop at the login screen, via the little icon in the username area. it will remember your choice until you change it.

with more than one desktop in an operating system, the menus will show applications from both desktops, it can be a good thing though, because you will for instance get access to Nautilus, the Ubuntu file manager. if you want to hide any items, you can simply edit menu files [by doing this (post 3)]("http://ubuntuforums.org/showthread.php?p=12080322#post12080322")



[]("http://ubuntuforums.org/showthread.php?p=12080322#post12080322")

---

### Post by sanderj on 2012-07-11
> **DoctorVarney said:**
>  I'm currently running 12.04 32bit and to be honest, it isn't even as fast as Windows XP on my AMD Athlon 64 988 Mhz machine with 2GB RAM.



Do you really have a 1000 Mhz Athlon 64? Cool! That must be one of the first Athlon 64's?

According to [http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors](http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors) it must be the Athlon 64 1500+ ... released in 2005. So that is a 7 year old processor. 

So IMHO it's quite logical Windows XP is faster than Ubuntu 12.04: Windows XP was built 10 years ago and thus will run well on a 7 year old processor. Ubuntu 12.04 has more features than Windows XP, and thus requires more processing power. You would not expect that Windows 7 runs fast on this system, or ... ? :P

Your 1000 Mhz processor is the bare minimum Ubuntu 12.04 could run on. See [http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#System_requirements](http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#System_requirements)

With a 1000 Mhz processor, I would not run Ubuntu 12.04, but Lubuntu or Xubuntu (both 12.04) instead.

HTH

---

### Post by DoctorVarney on 2012-07-11
> **sanderj said:**
> Do you really have a 1000 Mhz Athlon 64? Cool! That must be one of the first Athlon 64's?

According to [http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors](http://en.wikipedia.org/wiki/List_of_AMD_Athlon_64_microprocessors) it must be the Athlon 64 1500+ ... released in 2005. So that is a 7 year old processor. 

So IMHO it's quite logical Windows XP is faster than Ubuntu 12.04: Windows XP was built 10 years ago and thus will run well on a 7 year old processor. Ubuntu 12.04 has more features than Windows XP, and thus requires more processing power. You would not expect that Windows 7 runs fast on this system, or ... ? :P

Your 1000 Mhz processor is the bare minimum Ubuntu 12.04 could run on. See [http://en.wikipedia.org/wiki/Ubuntu_(operating_system)#System_requirements]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements")

With a 1000 Mhz processor, I would not run Ubuntu 12.04, but Lubuntu or Xubuntu (both 12.04) instead.

HTH

Thank you!  Your answer clears up the whole question for me.  I thought it was a pretty good processor and didn't make the connection with Ubuntu 12.04 coming out later, which now makes perfect sense.

Ubuntu doesn't run 'stupidly' slow though - as Windows XP did.  Within a few weeks of use, it's pretty blunt - and always looked horrible.  I can't afford to go up to Windows 7 but in any case, I have decided not to throw one more penny at Microsoft.  I don't like their products or their attitude.  I get an altogether better 'vibe' off those I've spoken to so far, in the Open Source community.

Thanks, everyone, for the advice on Xubuntu.  I'll have a look at that.  To be honest, Ubuntu doesn't work THAT badly, though installing this has taken three solid days of head scratching to just get this far.  I'm not sure if I'm ready to go through all that again.  Maybe in a couple of weeks, I'll look into it.  For now, there's stuff to get on with.

Cheers for the excellent answers! :)

---

### Post by mczakk on 2012-07-12
This thread seems to indicate that older processors are not that suited to 12.04, I am currently running 12.04 on a HP dv600 with AMD Turion 64x2 processor and ( i think) 1gb of ram. I'm running Gnome, not unity and on reading this thread am wondering if my machine is suitable? 
Thanks
:)

---

### Post by sanderj on 2012-07-12
> **mczakk said:**
> This thread seems to indicate that older processors are not that suited to 12.04, I am currently running 12.04 on a HP dv600 with AMD Turion 64x2 processor and ( i think) 1gb of ram. I'm running Gnome, not unity and on reading this thread am wondering if my machine is suitable? 
Thanks
:)

Suitable for what, if I may ask? You're already running Gnome not Unity, so what is your experience with that?

With these two commands you can get the CPU resp RAM spec of your system:

```
cat /proc/cpuinfo | head -10
free -m
```

HTH

---

### Post by mczakk on 2012-07-12
> **sanderj said:**
> Suitable for what, if I may ask? You're already running Gnome not Unity, so what is your experience with that?

With these two commands you can get the CPU resp RAM spec of your system:

```
cat /proc/cpuinfo | head -10
free -m
```HTH

this is the result of running that code:
```
mattnia@mattnia-HP-PAVILION-DV6000-RY598EA-ABU:~$ cat /proc/cpuinfo | head -10
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 15
model        : 72
model name    : AMD Turion(tm) 64 X2 Mobile Technology TL-50
stepping    : 2
microcode    : 0x68
cpu MHz        : 800.000
cache size    : 256 KB
physical id    : 0
mattnia@mattnia-HP-PAVILION-DV6000-RY598EA-ABU:~$ free m 
             total       used       free     shared    buffers     cached
Mem:        959480     881160      78320          0      50216     464816
-/+ buffers/cache:     366128     593352
Swap:       980988      13356     967632
mattnia@mattnia-HP-PAVILION-DV6000-RY598EA-ABU:~$ 
```

i meant suitable as in being aware that the laptop is a little old and wanting to make sure that i'm getting the best out of it. As for using gnome, i found unity to be horrendous, being an old school computer user! (yes i remember MSdos) and so had been using mint for a while until mint 12 drove me to distraction with all it's problems, so have returned to the ubuntu fold:)

---

### Post by sanderj on 2012-07-12
The TL-50 is a 1600 Mhz processor.
You indeed have 1GB RAM.
Swap is only a bit in use, which is good.
So, not the fastest machine, but OK for not too heavy usage. And indeed probably too low specced for Unity.

Oh, what I find useful: the last three numbers of the command 'uptime':

```
sander@R540:~$ uptime
 22:36:58 up 1 day,  6:19,  6 users,  load average: 0.82, 0.63, 0.83
sander@R540:~$
```

As long as those three numbers are below 1.00, it's OK. If the numbers get above 2.00, the system becomes less responsive. If so, with "top" you can see what is eating your CPU and memory.

---

### Post by mczakk on 2012-07-12
> **sanderj said:**
> The TL-50 is a 1600 Mhz processor.
You indeed have 1GB RAM.
Swap is only a bit in use, which is good.
So, not the fastest machine, but OK for not too heavy usage. And indeed probably too low specced for Unity.

Oh, what I find useful: the last three numbers of the command 'uptime':

```
sander@R540:~$ uptime
 22:36:58 up 1 day,  6:19,  6 users,  load average: 0.82, 0.63, 0.83
sander@R540:~$
```As long as those three numbers are below 1.00, it's OK. If the numbers get above 2.00, the system becomes less responsive. If so, with "top" you can see what is eating your CPU and memory.

uptime returns the following :

21:42:50 up  2:15,  1 user,  load average: 0.82, 0.47, 0.71

so i guess we're ok :)

thanks for the 'top' command as well, good to be able to see what is running!

i'm guessing that gnome is less demanding than unity?

---

