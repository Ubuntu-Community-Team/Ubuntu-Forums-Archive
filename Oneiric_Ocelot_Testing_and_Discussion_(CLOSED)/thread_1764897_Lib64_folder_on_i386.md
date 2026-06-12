---
title: "Lib64 folder on i386"
date: 2011-05-22
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-05-22
i'm surprised to find such folder/files on a clean i386 install, looking at synaptic there is several "64" packages installed like libc6-amd64

wonder which updates/dependencies have installed them

---

### Post by MacUntu on 2011-05-22
I don't see that. What do you mean by fresh install? I'm not seeing any Oneiric images yet.

---

### Post by dino99 on 2011-05-22
well i've made a fresh install of natty i386 from the MiniIso then updated and finally changed the sources.list to Oneiric

---

### Post by SevenMachines on 2011-05-22
$ apt-cache rdepends libc6-amd64
might shed some light

---

### Post by dino99 on 2011-05-22
> **SevenMachines said:**
> $ apt-cache rdepends libc6-amd64
might shed some light

of course but dont says how they came installed; as that seems an error i've removed that folder and all "64" related installed packages (4)

---

### Post by MacUntu on 2011-05-22
--- sorry, wrong tab ---

---

### Post by seeker5528 on 2011-05-23
> **dino99 said:**
> i'm surprised to find such folder/files on a clean i386 install, looking at synaptic there is several "64" packages installed like libc6-amd64

wonder which updates/dependencies have installed them

I don't have these things installed on my system, so I suspect they were pulled in by something you installed. I see fakechroot on the list of dependants for libc6-amd64, did you install that? 

EDIT: Scratch that, everything that shows in the dependants list in Synaptic is either 64 bit or only lists libc6-amd64 as a suggested package, it would be pulled in automatically by something that only suggested it.

If there were other 64 bit things installed, maybe one of those were recommended by something else you installed. By default a recommended package would be treated as a dependency when installing a package that recommends it, but the recommended package could later be uninstalled with no complaints. 

Later, Seeker

---

### Post by mc4man on 2011-05-24
just plain old fakeroot will install a few to /usr/lib64

---

### Post by dino99 on 2011-05-24
that is very suspect & scary to find "64" packages installed on a pure "32" one: i have fakeroot installed but not fakechroot.
The only explanation i can see is: some update(s) was wrongly identified as "32" package(s) (i've found then removed 4 packages, all related to libc6)

---

### Post by MacUntu on 2011-05-24
Instead of removing those packages, you could have used 'aptitude why <package>' to get info on what pulled that package in.

---

### Post by dino99 on 2011-05-24
> **MacUntu said:**
> Instead of removing those packages, you could have used 'aptitude why <package>' to get info on what pulled that package in.

thanks you, good to know :)

---

### Post by MacUntu on 2011-05-24
I'm just doing a 11.04 -> Oneiric VBox install, let's see what happens. :)

---

### Post by MacUntu on 2011-05-24
Natty: only thing in /usr/lib64 comes from fakeroot. After upgrade to Oneiric: no change.

---

### Post by dino99 on 2011-05-24
checked on natty i386:
- no lib64 folder
- fakeroot (1.14.4-1ubuntu1) installed (only libc6 dependency)
- no "64" package installed

on Oneiric, fakeroot has only libc6 dependency

so those "64" packages have been installed while upgrading natty to oneiric

i cant find good reasons to allow "64" packages installation on i386 system

---

### Post by MacUntu on 2011-05-24
Well, do:

```
sudo dpkg -L fakeroot | grep lib
```

On a 64-bit Ubuntu I have files in /usr/lib32, on a 32-bit install I have files in /usr/lib64.

I don't see any problems.

---

### Post by dino99 on 2011-05-24
output:

oem@oem-desktop:~$ sudo dpkg -L fakeroot | grep lib
[sudo] password for oem: 
/usr/lib
/usr/lib/libfakeroot
/usr/lib/libfakeroot/libfakeroot-tcp.so
/usr/lib/libfakeroot/libfakeroot-sysv.so


of course all the "64" are removed

---

### Post by mc4man on 2011-05-24
[http://packages.ubuntu.com/natty/i386/fakeroot/filelist](http://packages.ubuntu.com/natty/i386/fakeroot/filelist)
[http://packages.ubuntu.com/oneiric/i386/fakeroot/filelist](http://packages.ubuntu.com/oneiric/i386/fakeroot/filelist)

The upgrade should remove the dir. unless something else is in there

---

### Post by MacUntu on 2011-05-24
> **mc4man said:**
> [http://packages.ubuntu.com/natty/i386/fakeroot/filelist](http://packages.ubuntu.com/natty/i386/fakeroot/filelist)
[http://packages.ubuntu.com/oneiric/i386/fakeroot/filelist](http://packages.ubuntu.com/oneiric/i386/fakeroot/filelist)

The upgrade should remove the dir. unless something else is in there

Ah, my upgrade didn't finish. After the upgrade from a fresh Natty install I no longer have a /usr/lib64.

---

