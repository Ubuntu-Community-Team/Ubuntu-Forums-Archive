---
title: "Ati accelerated graphics driver freezes my computer"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by bralmu on 2008-04-28
Hi,

What I did
----------
I have done a clean install of Ubuntu 8.04.
It works perfect until I activate ATI driver in System/Administration/Hardware drivers
then I restart the computer and the problem starts.

The problem
-----------
The problem is a random freeze. Sometimes it works for 20 minutes in the desktop enviroment and sometimes it get frozen immediately when I start a OpenGL game, screensaver or videoplayer.

I mean, if I do a intensive use of 3D (for example if I activate desktop effects) it crashes earlier but I can't repeat a crash doing something specific because it seems to be random.

The screen is frozen, the sound stops, mouse and keyboards leds don't respond.
No error messages appears in the screen. The computer is full stoped. After some seconds or a minute, the computer resets itself.


The computer
------------
Ubuntu 8.04 32bits
sck939 motheboard with nForce4 4x chipset.
AMD64 3500+
2GB DDR
ATI X1800GTO 256MB
It's not a hardware problem because Windows works fine.


PS: sorry for my English mistakes :( it isn't my native language.

---

### Post by thisismalhotra on 2008-04-28
I would reinstall that driver using ENVY. It is available via synaptic and here is the link

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by martrn on 2008-04-28
what kernel are you using ?

eg what is your kernel ?
type at terminal
```
uname -r
```

you could try
```
sudo apt-get install linux-rt
```
+ reboot
Logon next time using that kernel

see filing a bug report in stickys above.

---

### Post by bralmu on 2008-04-28
thisismalhotra
--------------
I have tried Envy but the problem is exactly the same.

martrn
------
My version is 2.6.24-16-generic

I have installed rt kernel and run it, but the problem persists.
I have also tried Envy + rt kernel.



Any other idea?

---

### Post by mudvayne852 on 2008-09-02
i have the exact same problem wonder why??:confused:

---

### Post by bob74 on 2008-09-02
I posted a similar problem earlier. Whilst it doesn't help I am at least relieved that other people are having the problem when trying to activate accelerated graphics whether nvidia or ati. I'm dual booted and xp is fine so nothing appears to be wrong with hardware. I have tried every suggestion to no avail and it looks like a backup job and reinstall the system. It may be purely coincidence but everything worked ok in the previous version. Is this a bug? I should confirm that everything was ok up to the point of accelerated graphics and when I get back I will leave that function well alone.

---

### Post by timandjulz on 2008-09-16
I am having a similar problem.  Screen display locks but I can ssh and vnc to the machine.  vnc shows my desktop and I can continue to work but the monitor continues to show the screen at the time it locked up.

Just curious if anyone else having the problem tried ssh/vnc to verify the display is locked but the computer is not.
[http://ubuntuforums.org/showthread.php?p=5800761](http://ubuntuforums.org/showthread.php?p=5800761)

---

