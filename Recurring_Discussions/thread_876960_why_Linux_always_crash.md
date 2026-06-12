---
title: "why Linux always crash"
date: 2008-08-01
forum: Recurring Discussions
---

### Post by rashwan on 2008-08-01
openSuSE , Ubuntu , Mandriva , Fedora ...generally i say LINUX
is always damn slow and and 00000.1% of necessary programs works "well" on it, am not about posting examples and problems but of a 2 yrs experience on Linux i 'ave never worked on stable system that does not crash every week
i dont care that i pay on MS-win but at least i cant find that huge reports of bugs and system crash logs

---

### Post by tuxxy on 2008-08-01
All 4 distros are slow, I find this difficult to beleive.  Maybe you should do some reserarch into your hardware config as this could be the problem not linux.

---

### Post by overdrank on 2008-08-01
thread moved as it is not a support request. I have had nothing but good luck with all the distro's mention and the best of luck to the OP.

---

### Post by tamoneya on 2008-08-01
> **rashwan said:**
> openSuSE , Ubuntu , Mandriva , Fedora ...generally i say LINUX
is always damn slow and and 00000.1% of necessary programs works "well" on it, am not about posting examples and problems but of a 2 yrs experience on Linux i 'ave never worked on stable system that does not crash every week
i dont care that i pay on MS-win but at least i cant find that huge reports of bugs and system crash logs

```
tamoneya@server:~$ uptime
 09:48:49 up 35 days, 48 min,  5 users,  load average: 0.00, 0.00, 0.00
```

My server is pretty stable.  Its a pentium 4 and used to just be a desktop so no fancy hardware.  The only reason why it turned off over a month ago was because i tripped on the power cord.

---

### Post by AutiCoder on 2008-08-01
At this moment i'm using a brand new Laptop ( AMD64 X2 with 3G ram ) and it works a lot faster on Ubuntu as it does on Windows .

On the Laptop i've used b4 this one , a 5 years old one ,
i've been using ubuntu for about 2 years and not a single one crash !

So i cannot understand about what you complain ...

---

### Post by beniwtv on 2008-08-01
```
up 449 days, 24 min,  3 users,  load average: 0.02, 0.03, 0.00
```

hum.... pretty stable here, and no slow downs. This server is bored right now but usually it's hit hard by spam.

I think it has more to do with your hardware configuration than Linux. Maybe if you post your specs we can better determine what's happening.

Cheers,

---

### Post by billgoldberg on 2008-08-01
> **rashwan said:**
> openSuSE , Ubuntu , Mandriva , Fedora ...generally i say LINUX
is always damn slow and and 00000.1% of necessary programs works "well" on it, am not about posting examples and problems but of a 2 yrs experience on Linux i 'ave never worked on stable system that does not crash every week
i dont care that i pay on MS-win but at least i cant find that huge reports of bugs and system crash logs

It took you 2 years to find out your hardware isn't fully compatible?

Or are you just finding out now?

---

### Post by rashwan on 2008-08-01
CPU 3.2/2 mb cache 
nForce 650I ultra mother board
4 GB DDR2
320 G HDD 9000 rpm
8800 GTS DDR3 512

its not about HW compatibility also all devices are well defined by linux and drivers are updated automatically in ubuntu ONLY
but...the system it self i feel it too slow and crashes 
it might because of some programs like AWN and Compiz but other people insist awn and compiz are not the problem

---

### Post by lil_elvis2000 on 2008-08-01
Slow. Don't believe it. CentOS 5.1 on identical hardware to Windows Server 2008 run much much faster. I am a developer on both and can tell you that oracle 11g runs much stabler and faster on CentOS than on Windows.  I'm sure Joomla can run faster on Linux than Sharepoint - but that's not really apples and apples.

---

### Post by Yes on 2008-08-01
Where'd you get a 9000 RPM hard drive?

---

### Post by tamoneya on 2008-08-01
> **rashwan said:**
> CPU 3.2/2 mb cache 
nForce 650I ultra mother board
4 GB DDR2
320 G HDD 9000 rpm
8800 GTS DDR3 512

its not about HW compatibility also all devices are well defined by linux and drivers are updated automatically in ubuntu ONLY
but...the system it self i feel it too slow and crashes 
it might because of some programs like AWN and Compiz but other people insist awn and compiz are not the problem

next time it becomes sluggish can we get the output of ```
top
```

---

### Post by K2712 on 2008-08-01
You obviously have a hardware issue.  I have used all of those distributions, and they are all rock-solid on even mediocre hardware setups.  Maybe you should post some error logs and ask some questions rather than going off on a rant.

---

### Post by rashwan on 2008-08-01
> **tamoneya said:**
> next time it becomes sluggish can we get the output of ```
top
```

```
top - 18:50:12 up  2:08,  2 users,  load average: 0.21, 0.62, 0.77
Tasks: 130 total,   1 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.1%us,  0.5%sy,  0.0%ni, 86.3%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2844688k total,  1409952k used,  1434736k free,    29672k buffers
Swap:  2441840k total,        0k used,  2441840k free,   980360k cached

```

---

### Post by tamoneya on 2008-08-01
is that from when it is sluggish?  It doesnt appear so.  Also it would be nice if we could see some of the lines below that concerning what processes are running.

---

