---
title: "synaptic deleted DO NOT UPDATE"
date: 2011-08-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by joske on 2011-08-08
Hi All,

an experimental version of apt was merged, but seems to be not complete, as a result synaptic got deleted, and can not be installed until the new libraries sync up. Best to refrain from updating now.

---

### Post by paul_in_london on 2011-08-08
Yes, only **apt-get** is usable at the moment (not aptitude or synaptic):

```
paul@oneiric:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apt apt-utils
The following packages will be upgraded:
  xserver-xorg-video-intel
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 429 kB of archives.
After this operation, 496 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ oneiric/main xserver-xorg-video-intel i386 2:2.15.901+git20110808.f4bbbd1d-0ubuntu0sarvatt [429 kB]
Fetched 429 kB in 0s (687 kB/s)                   
(Reading database ... 268856 files and directories currently installed.)
Preparing to replace xserver-xorg-video-intel 2:2.15.901+git20110801.7976f514-0ubuntu0sarvatt (using .../xserver-xorg-video-intel_2%3a2.15.901+git20110808.f4bbbd1d-0ubuntu0sarvatt_i386.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-intel (2:2.15.901+git20110808.f4bbbd1d-0ubuntu0sarvatt) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

paul@oneiric:~$ 
```

```
paul@oneiric:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED
  aptitude ppa-purge synaptic tasksel tasksel-data
The following packages will be upgraded:
  apt apt-utils
2 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 1,241 kB of archives.
After this operation, 13.5 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
paul@oneiric:~$ 
```

---

### Post by joske on 2011-08-08
I've built the latest synaptic from source, have a .deb if anyone needs it. This fixes synaptic, but lots more stuff is broken, as it depends on the new apt (jockey, ...)

jos

---

### Post by paul_in_london on 2011-08-08
> **joske said:**
> I've built the latest synaptic from source, have a .deb if anyone needs it. This fixes synaptic, but lots more stuff is broken, as it depends on the new apt (jockey, ...)

jos

@joske: Thanks mate. I think I'll wait a while...

---

### Post by paul_in_london on 2011-08-08
Partial resolution now:

```
paul@oneiric:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apt
The following packages will be upgraded:
  apt-utils synaptic
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 903 kB of archives.
After this operation, 61.4 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric/main synaptic i386 0.75.2ubuntu2 [713 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ oneiric/main apt-utils i386 0.8.16~exp5ubuntu1 [190 kB]
Fetched 903 kB in 0s (1,003 kB/s)
(Reading database ... 268860 files and directories currently installed.)
Preparing to replace synaptic 0.75.2ubuntu1 (using .../synaptic_0.75.2ubuntu2_i386.deb) ...
Unpacking replacement synaptic ...
Preparing to replace apt-utils 0.8.15.5ubuntu2 (using .../apt-utils_0.8.16~exp5ubuntu1_i386.deb) ...
Unpacking replacement apt-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up synaptic (0.75.2ubuntu2) ...
Setting up apt-utils (0.8.16~exp5ubuntu1) ...
Processing triggers for menu ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 104 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 52 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 156 KiB

paul@oneiric:~$
```

---

### Post by Harry33 on 2011-08-08
I am using the main server, where all the apt and related packages are available in Oneiric repos for 32-bit systems. For 64-bit systems python-apt (0.8.0ubuntu2) is still missing.
So you need all these packages:
- apt, apt-transport-http, apt-utils, libapt-inst1.3, libapt-pkg4.11
   (all v. 0.8.16~exp5ubuntu1)
- libept1 (1.0.5build1)
- python-apt, python-apt-common
   (v. 0.8.0ubuntu2)
- synaptic (0.75.2ubuntu2)

If you want, you can go and get the missing package from "apt oneiric rebuild PPA" (Mathias Klose). You'll find the version 0.8.1~ppa4, but that goes well.
Just remember to downgrade it, when python-apt is available from repos.

---

### Post by linuxman94 on 2011-08-08
> **Harry33 said:**
> I am using the main server, where all the apt and related packages are available in Oneiric repos for 32-bit systems. For 64-bit systems python-apt (0.8.0ubuntu2) is still missing.
So you need all these packages:
- apt, apt-transport-http, apt-utils, libapt-inst1.3, libapt-pkg4.11
   (all v. 0.8.16~exp5ubuntu1)
- libept1 (1.0.5build1)
- python-apt, python-apt-common
   (v. 0.8.0ubuntu2)
- synaptic (0.75.2ubuntu2)

If you want, you can go and get the missing package from "apt oneiric rebuild PPA" (Mathias Klose). You'll find the version 0.8.1~ppa4, but that goes well.
Just remember to downgrade it, when python-apt is available from repos.

I think it's just better to wait this one out, IMO :smile:
Side note, it's sad to see this much of a breakage in alpha 3

---

### Post by Harry33 on 2011-08-08
> **linuxman94 said:**
> I think it's just better to wait this one out, IMO :smile:
Side note, it's sad to see this much of a breakage in alpha 3

Actually this is not a true breakage.
All these apt related packages depend on each other, they just need to be upgraded (API bumb) at the same time.
Accidentally python-apt failed to build on 64-bit arch.
There will soon be the package python-apt 0.8.0ubuntu3 available.

---

### Post by castrojo on 2011-08-08
> **linuxman94 said:**
> I think it's just better to wait this one out, IMO :smile:
Side note, it's sad to see this much of a breakage in alpha 3

It only breaks if you tell it to break, there's a sticky thread about how to deal with partial upgrades.

---

### Post by paul_in_london on 2011-08-08
```
paul@oneiric:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-glx libglapi-mesa
The following packages will be upgraded:
  apt aptitude
2 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 2,316 kB/3,368 kB of archives.
After this operation, 2,900 kB disk space will be freed.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric/main aptitude i386 0.6.4-1ubuntu2 [2,316 kB]
Fetched 2,316 kB in 1s (1,161 kB/s)   
(Reading database ... 268872 files and directories currently installed.)
Preparing to replace aptitude 0.6.4-1ubuntu1 (using .../aptitude_0.6.4-1ubuntu2_i386.deb) ...
Unpacking replacement aptitude ...
Preparing to replace apt 0.8.15.5ubuntu2 (using .../apt_0.8.16~exp5ubuntu1_i386.deb) ...
Unpacking replacement apt ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up apt (0.8.16~exp5ubuntu1) ...
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
Setting up aptitude (0.6.4-1ubuntu2) ...
Processing triggers for menu ...
localepurge: Disk space freed in /usr/share/locale: 1332 KiB
localepurge: Disk space freed in /usr/share/man: 508 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 1840 KiB

paul@oneiric:~$
```

And then I was able to do:

```
paul@oneiric:~$ sudo aptitude full-upgrade
The following NEW packages will be installed:
  libwayland0{a} 
The following packages will be upgraded:
  libegl1-mesa libegl1-mesa-drivers libgl1-mesa-glx libglapi-mesa 
4 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,080 kB of archives. After unpacking 274 kB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://archive.ubuntu.com/ubuntu/ oneiric/main libwayland0 i386 0.1.0~0.2-0ubuntu2 [35.4 kB]
Get: 2 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ oneiric/main libgl1-mesa-glx i386 7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2 [140 kB]
Get: 3 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ oneiric/main libegl1-mesa-drivers i386 7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2 [1,754 kB]
Get: 4 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ oneiric/main libglapi-mesa i386 7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2 [59.7 kB]
Get: 5 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ oneiric/main libegl1-mesa i386 7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2 [90.8 kB]
Fetched 2,080 kB in 1s (1,331 kB/s)
(Reading database ... 268786 files and directories currently installed.)
Preparing to replace libgl1-mesa-glx 7.12.0~git20110801.5b3c7199-0ubuntu0sarvatt (using .../libgl1-mesa-glx_7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace libegl1-mesa-drivers 7.12.0~git20110801.5b3c7199-0ubuntu0sarvatt (using .../libegl1-mesa-drivers_7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2_i386.deb) ...
Unpacking replacement libegl1-mesa-drivers ...
Preparing to replace libglapi-mesa 7.12.0~git20110801.5b3c7199-0ubuntu0sarvatt (using .../libglapi-mesa_7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2_i386.deb) ...
Unpacking replacement libglapi-mesa ...
Selecting previously deselected package libwayland0.
Unpacking libwayland0 (from .../libwayland0_0.1.0~0.2-0ubuntu2_i386.deb) ...
Preparing to replace libegl1-mesa 7.12.0~git20110801.5b3c7199-0ubuntu0sarvatt (using .../libegl1-mesa_7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2_i386.deb) ...
Unpacking replacement libegl1-mesa ...
Setting up libglapi-mesa (7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2) ...
Setting up libgl1-mesa-glx (7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2) ...
Setting up libwayland0 (0.1.0~0.2-0ubuntu2) ...
Setting up libegl1-mesa (7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2) ...
update-alternatives: using /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode.
Setting up libegl1-mesa-drivers (7.12.0~git20110808.ffb7d021-0ubuntu0sarvatt2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
Current status: 0 updates [-4].
paul@oneiric:~$
```

---

### Post by jerrylamos on 2011-08-08
?  I just installed and did aptitude update of 8 August daily build and there is Synaptic.  Now I fiddled with the repositories like usual and updated Synaptic but didn't do anything to Oneiric with Synaptic.

?

Jerry

---

### Post by Harry33 on 2011-08-09
New apt, python-apt and synaptic all work well now.
There are minor adjustments to python-apt ATM.

---

### Post by fillmont on 2011-08-09
> **Harry33 said:**
> New apt, python-apt and synaptic all work well now.
There are minor adjustments to python-apt ATM.

Also confirming that all seems to be well now.

---

### Post by tghe-retford on 2011-08-09
Aptitude also broke last night, which means that [FONT="Courier New"]aptitude safe-upgrade[/FONT] will not work. Having to use [FONT="Courier New"]apt-get upgrade[/FONT] instead.

---

### Post by paul_in_london on 2011-08-09
> **tghe-retford said:**
> Aptitude also broke last night, which means that [FONT="Courier New"]aptitude safe-upgrade[/FONT] will not work. Having to use [FONT="Courier New"]apt-get upgrade[/FONT] instead.

It's been ok here again since later on last night actually.

---

### Post by sammiev on 2011-08-09
I'm back up and running but I'm missing my update manger button and my software package manager button? Anyone else?

Thanks

---

### Post by cjgrif on 2011-08-09
Would this affect the Update Manager?

My Update Manager broke a few days ago to where it fails if I click on "Check" or "Install Updates" (I get the "Sorry, Update Manager closed unexpectedly" dialog)

I have ended up just doing "apt-get update" on the CLI and then fire up update manager to see what updates are available/recommended and then I install each of them using "apt-get upgrade" (or "apt-get install" if I get the "... package was held back" message).

I just want to make sure I didn't break anything myself and it is just part of the 11.10 alpha process and others have the same problem.

---

### Post by cariboo on 2011-08-09
If you are using Update-manager, during a testing cycle, you are doing it wrong, unless you are willing to read exactly what will be changed, mind you need to do this whether using apt-get, aptitude or synaptic too

---

