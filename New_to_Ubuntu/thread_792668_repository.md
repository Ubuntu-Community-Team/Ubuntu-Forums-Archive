---
title: "repository"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by vinceUUUU on 2008-05-13
Hello,

can anybody help me.

i need to know the latest list of repositories for ubuntu.

the list of addresses....

can anybody point me to the list on a web page?.....or list them here?

thanks

Vince.

---

### Post by kesman on 2008-05-13
It's in your /etc/apt/sources.list unless you've lost it.

---

### Post by Joeb454 on 2008-05-13
Open up /etc/apt/sources.list and that will give you the web addresses of the repositories your PC is using :)

---

### Post by kesman on 2008-05-13
slooow :P

---

### Post by bluefrog on 2008-05-13
use synaptic, you will be able to check the repositories you want. (menu settings/repositories)

---

### Post by vinceUUUU on 2008-05-13
Hello

uh...i just wanted a list of the repoisitory's ubuntu uses.

if anybody can point me to a web page with the list....or list them here...

my system is not ubuntu here...

thanks

Vince.

---

### Post by Joeb454 on 2008-05-13
I'm from the UK, but here's mine

```
deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse
```

I think you just need to remove "gb." for the US repo's

---

### Post by vinceUUUU on 2008-05-13
Hello

that is great...a printout....thanks very much

Vince

---

### Post by Joeb454 on 2008-05-13
Hope it helps a little, I don't think there's a webpage to look at. Though there is [http://packages.ubuntu.com](http://packages.ubuntu.com) if you want to search for individual packages :)

---

### Post by vinceUUUU on 2008-05-13
Hello 

actually Joe

i need the 7.10 fiesty fawn list of repo's

your system looks like it is a HARDY system.....right?

thanks

Vince.

---

### Post by atomkarinca on 2008-05-13
Just replace "hardy"s with "feisty", you're good to go.

---

### Post by vinceUUUU on 2008-05-13
Hello

Joe, thanks.

basically i use the distro called Antix....it's nice distro and debian....

people have told me that ubuntu packages work correctly in Antix....forum people at Antix...

it's worth giving it a go here Joe....because ubuntu packages are so vast...

it's no trouble for me to try these things out here...Antix only takes about 5 minutes to install from scratch....so it is no trouble experimenting with the distro...

thanks

Vince.

---

### Post by anticapitalista on 2008-05-13
vinceUUUU DON'T!! use Ubuntu repos in antiX. You can get whatever you want using the default Debian repos.

---

