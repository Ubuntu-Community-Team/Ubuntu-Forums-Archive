---
title: "'E:Malformed line 59 in source list /etc/apt/sources.list (URI parse)"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by Rotary Heart on 2012-12-21
Well I get a update notification and then this error appeared. So I go to the file and this is my 59 line (I think) 

deb index of / lucid partner

But heres my sorce.list file. I have read some threads, but I don't find what they say is the error. 

Ubuntu 12.04 in a Alienware M17 not running in dual boot.

Thanks

```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://pr.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://pr.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://pr.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://pr.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://pr.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://pr.archive.ubuntu.com/ubuntu/ precise universe
deb http://pr.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://pr.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://pr.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://pr.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://pr.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://pr.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://pr.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://pr.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.canonical.com/ precise partner
deb-src http://archive.canonical.com/ precise partner
deb index of / lucid partner
deb-src index of / lucid partner
```

---

### Post by ibjsb4 on 2012-12-21
It would make it easier if you would include line numbers in the future.

```
cat -n /etc/apt/sources.list
```

deb index of / lucid partner 
deb-src index of / lucid partner

Both of these need to be removed.

---

### Post by Rotary Heart on 2012-12-21
> **ibjsb4 said:**
> It would make it easier if you would include line numbers in the future.

```
cat -n /etc/apt/sources.list
```

deb index of / lucid partner 
deb-src index of / lucid partner

Both of these need to be removed.

My bad, I feel kind of noob, I changed permissions to rw and then tried to edit it, but I got a error saying that gedit can't make a backup so I click save anyway, but its not getting saved?? what should I do?

Thanks

---

### Post by Rotary Heart on 2012-12-21
> **ibjsb4 said:**
> It would make it easier if you would include line numbers in the future.

```
cat -n /etc/apt/sources.list
```

deb index of / lucid partner 
deb-src index of / lucid partner

Both of these need to be removed.

Ok fixed. Thanks

---

### Post by BlinkinCat on 2012-12-21
> **Rotary Heart said:**
> Ok fixed. Thanks


What did you do to fix your problem so others can gain knowledge.

Cheers - :)

---

### Post by Rotary Heart on 2012-12-21
oo yea, my bad.

```
$ sudo gedit /etc/apt/sources.list
```

then I deleted the last two sentences:

deb index of / lucid partner 
deb-src index of / lucid partner

save it and reboot, just in case. Now working normally again. :D

---

### Post by BlinkinCat on 2012-12-21
Thanks for that -

You could mark the thread as solved via thread tools at top of page.

Cheers - :p

---

