---
title: "Unabe to find package libesd-alsa0"
date: 2005-02-20
forum: Repositories &amp; Backports
---

### Post by Sam on 2005-02-20
According this [thread](http://ubuntuforums.org/showthread.php?t=8882), I tried to install the package **libesd-alsa0**, but it doesn't exist! I have every repositories checked in Synaptic, and as seen on the above thread, there are several people who installed this package.

What's wrong? I'm using Warty AMD 64.

---

### Post by p!=f on 2005-02-20
[QUOTE=Sam]According this [thread](http://ubuntuforums.org/showthread.php?t=8882), I tried to install the package **libesd-alsa0**, but it doesn't exist! I have every repositories checked in Synaptic, and as seen on the above thread, there are several people who installed this package.

What's wrong? I'm using Warty AMD 64.[/QUOTE]
Hmmm. Ubuntu Hoary here.
```

[~] > wajig policy libesd-alsa0
libesd-alsa0:
  Installed: (none)
  Candidate: 0.2.35-2ubuntu2
  Version Table:
     0.2.35-2ubuntu2 0
        500 http://archive.ubuntu.com hoary/main Packages

```
Could you run 
```

[~] > apt-cache --names-only search libesd
libesd-alsa0 - Enlightened Sound Daemon (ALSA) - Shared libraries
libesd0 - Enlightened Sound Daemon - Shared libraries
libesd0-dev - Enlightened Sound Daemon - Development files

```
or if you use wajig
```

[~] > wajig list-names libesd
libesd-alsa0
libesd-alsa0-dev
libesd-dev
libesd0
libesd0-dev

```
and post the outputs here? Also put your /etc/apt/sources.list here.

---

### Post by Sam on 2005-02-20
Thank you for you reply. Here are the outputs you asked:
```
$ apt-cache --names-only search libesd
libesd0 - Enlightened Sound Daemon - Shared libraries
libesd0-dev - Enlightened Sound Daemon - Development files
```
And my sources.list
```
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview amd64 Binary-1 (20041020)]/ unstable main restricted 
deb http://archive.ubuntu.com/ubuntu/ warty main restricted multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted 
deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe 
deb http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
```

---

### Post by songochain on 2005-02-20
I cant find libesd-alsa0 too!!

---

### Post by kassetra on 2005-02-20
That's because there isn't a package of libesd-alsa0 for amd64.
 
 libesd-alsa0 is only available for i386 & powerpc in warty, and in hoary ia64 is available as well... but no amd64.
 
 Have you ever compiled from source before?

---

### Post by songochain on 2005-02-20
LOL, i've installed esound and i've full duplex but with a daemon  :roll: AMD64 support is very very poor yet

---

### Post by Sam on 2005-02-20
[QUOTE=kassetra]Have you ever compiled from source before?[/QUOTE]
Sorry, I'm new to linux... I compiled some programs before, but only with install instructions...

It seems that I will wait for the official release of Hoary... :?

---

### Post by songochain on 2005-02-20
[QUOTE=kassetra]Have you ever compiled from source before?[/QUOTE] Yeah but i dont find sources for amd64... this the reason because i said poor support for amd64

---

### Post by kassetra on 2005-02-20
I have a semi-answer for you Sam:
 
 For mplayer-amd64 dependencies: you can install libesd0... and that will cure the dependency on libesd-alsa0 ... mostly.  You may also have to install other libraries...

---

### Post by Sam on 2005-02-20
Hmm ok... I will investigate this way...

Thank you for your answer! :wink:

---

### Post by kassetra on 2005-02-20
you're welcome!  I hope it all works nicely for you!  :)

---

