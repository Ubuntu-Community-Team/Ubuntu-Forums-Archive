---
title: "Cleaning Boot"
date: 2014-06-21
forum: New to Ubuntu
---

### Post by ButchMel on 2014-06-21
I started to get message that my 200MB boot was 100% full, so searched the forums how to clean it. The process (below) looks like id did not complete, and suggested apt-get install which I tried. Yet, please see below : seems it did not complete. I'm using 12.04 LTS (Server with graphic interface)

Last time I had such a problem I inadvertently wiped wrong thing and scrapped my system - needed to rebuild from scratch.  I'd like to avoid it now. Plus, is there a way to have a boot that is greater than 200 MB ??
```

robert@CrabConnect:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-39-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
robert@CrabConnect:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
robert@CrabConnect:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.8.0-42-generic linux-image-generic-lts-raring
Suggested packages:
  fdutils linux-lts-raring-doc-3.8.0 linux-lts-raring-source-3.8.0
  linux-lts-raring-tools linux-headers-3.8.0-42-generic
The following NEW packages will be installed:
  linux-image-3.8.0-42-generic
The following packages will be upgraded:
  linux-image-generic-lts-raring
1 upgraded, 1 newly installed, 0 to remove and 146 not upgraded.
17 not fully installed or removed.
Need to get 50.3 MB of archives.
After this operation, 137 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.8.0-42-generic i386 3.8.0-42.62~precise1 [50.3 MB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-generic-lts-raring i386 3.8.0.42.42 [2,380 B]
Fetched 50.3 MB in 18s (2,789 kB/s)                                            
Selecting previously unselected package linux-image-3.8.0-42-generic.
(Reading database ... 404096 files and directories currently installed.)
Unpacking linux-image-3.8.0-42-generic (from .../linux-image-3.8.0-42-generic_3.8.0-42.62~precise1_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-42-generic_3.8.0-42.62~precise1_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.8.0-42-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-42-generic /boot/vmlinuz-3.8.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-42-generic /boot/vmlinuz-3.8.0-42-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-42-generic_3.8.0-42.62~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by LastDino on 2014-06-21
First check your kernel version, so you won't delete the in-use kernel image, running:
```
uname -r
```
Now run this command for a list of installed kernels:
```
sudo dpkg --list 'linux-image*'
``` 
and delete the kernels you don't want/need any more by running this:
```
sudo apt-get remove linux-image-version
```
Do not remove current version and if possible keep one immediate older as well.

You can increase boot size by booting into live DVD/USB mode and running gparted, take backup before though.

One question: Is there any particular need that you require /boot to be on separate partition? If not, and you came to stage where you need fresh install, don't bother to make one next time.

---

### Post by Bashing-om on 2014-06-21
ButchMel; Hello;

Hey ! LastDino beat me to it ! still, confirmation is a good thing.

We can get through this.
What release are you running, as the method to remove kernels can be different in the later releases ( and much easier !) ?
Post back the output - between code tags - of terminal commands:
```

lsb_release -a
uname -a

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And then let's look at what we are working on:
```

dpkg -l | grep linux-

```
as it is

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by ButchMel on 2014-06-23
lsb_release -a

[COLOR=#ff0000]Description:	Ubuntu 12.04.3 LTS[/COLOR]
[COLOR=#ff0000]Release:	12.04[/COLOR]
[COLOR=#ff0000]Codename:	precise[/COLOR]

uname -a

[COLOR=#ff0000]3.8.0-36-generic #52~precise1-Ubuntu SMP Mon Feb 3 21:56:56 UTC 2014 i686 i686 i386 GNU/Linux[/COLOR]







code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
And then let's look at what we are working on:
```

dpkg -l | grep linux-

```
as it is
[INDENT][INDENT]all in the process
[/INDENT]
[/INDENT]
[/QUOTE]

---

### Post by ButchMel on 2014-06-23
Here is the ourput... To be frank, not too sure what to do / how to proceed from here... :

_**To uname -r :**_

3.8.0-36-generic

Then, second step: **[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --list 'linux-image*'[/FONT][/COLOR]**

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-3. <none>         (no description available)
ii  linux-image-3. 3.8.0-29.42~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-31.46~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-32.47~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-33.48~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-34.49~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-35.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-36.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-37.53~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-38.56~pr Linux kernel image for version 3.8.0 on 32 b
in  linux-image-3. <none>         (no description available)
in  linux-image-3. <none>         (no description available)
iU  linux-image-ge 3.8.0.39.39    Generic Linux kernel image

---

### Post by oldfred on 2014-06-24
I prefer to use synaptic, but if you do not have it already installed you will not be able to install it now. So command line is only choice.

 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic
#current install:
lsb_release -a
Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

You may need to also empty trash.
      
 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

---

### Post by ButchMel on 2014-06-30
Isn't [COLOR=#000000]command line in post #8[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

also only if I have Synaptic ?

---

### Post by ButchMel on 2014-06-30
Obviously, no Synaptic installed, unfortunately...

uname - a : gives me that :

3.8.0-36-generic #52~precise1-Ubuntu SMP Mon Feb 3 21:56:56 UTC 2014 i686 i686 i386 GNU/Linux



Now, if I open the older ''BOOT'', I see indeed many kernels - but with prefixes (in bold) such as **abi**-3.8.0-34 generic, **config**-3.8.0-34, **initrd.img**-3.8.0-34,** system.map**-3.8.0-34...,, **vmlinuz**-3.9.0-34....

Could I simply delete from there ?? (for all thos abi, config, initrd.img, system.map and vmlinuz for kernels except the one in use (and maybe one behind)?

Then flush the trash bin ?

Afterward, assuming everything is back to normal, maybe I would install Synaptic for the future  ??

---

### Post by sandyd on 2014-06-30
> **ButchMel said:**
> Isn't [COLOR=#000000]command line in post #8[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

also only if I have Synaptic ?

nope, the command line in post #8 uses apt-get which is installed by default.

---

### Post by Bashing-om on 2014-06-30
> **ButchMel said:**
> Here is the ourput... To be frank, not too sure what to do / how to proceed from here... :

_**To uname -r :**_

3.8.0-36-generic

Then, second step: **[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --list 'linux-image*'[/FONT][/COLOR]**

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-3. <none>         (no description available)
ii  linux-image-3. 3.8.0-29.42~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-31.46~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-32.47~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-33.48~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-34.49~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-35.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-36.52~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-37.53~pr Linux kernel image for version 3.8.0 on 32 b
ii  linux-image-3. 3.8.0-38.56~pr Linux kernel image for version 3.8.0 on 32 b
in  linux-image-3. <none>         (no description available)
in  linux-image-3. <none>         (no description available)
iU  linux-image-ge 3.8.0.39.39    Generic Linux kernel image

ButchMel; Hello. 

As you can see you have booted with an real old kernel - 3.8.0-36-generic -. when there are many newer kernels installed. This does cause me concern as to why ?? Did you choose to boot that old kernel ?
Let's check and see what the system is set up to boot.
```

ls -la /

```
looking at these two files in particular, where they point to:
```

lrwxrwxrwx   1 root root    33 Jun 26 11:37 initrd.img -> boot/initrd.img-3.11.0-24-generic
lrwxrwxrwx   1 root root    30 Jun 26 11:37 vmlinuz -> boot/vmlinuz-3.11.0-24-generic

```
Here I am starting the system using the INITial Ram Device IMaGe version 3.11.0-24;
and booting version 3.11.0-24 kernel (vmlinuz).

Then we will use the terminal to interact with the package manager (dpkg) to remove all those old kernels, and files .. the package manager will take care of the details for the abi, config, images. maps, and kernels. We will also remove the old headers files.
At least that is the plan, but we must keep that kernel that you are then presently booting, and 1 other for a backup.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by ButchMel on 2014-07-01
Bashing-Om,

No I have not chosed that kernel... Might be matter of latest that could not install automatically, lack of space ?

To **ls -la/**  I gey the following:

robert@CrabConnect:~$ ls -la /
total 98
drwxr-xr-x  22 root root  4096 Mar 31 07:48 .
drwxr-xr-x  22 root root  4096 Mar 31 07:48 ..
drwxr-xr-x   2 root root  4096 Jan  9 14:14 bin
drwxr-xr-x   4 root root  2048 Jun 21 14:50 boot
drwxr-xr-x  16 root root  4620 Mar 31 07:48 dev
drwxr-xr-x 141 root root 12288 Apr 24 07:46 etc
drwxr-xr-x   4 root root  4096 Oct  6  2013 home
lrwxrwxrwx   1 root root    33 Mar 31 07:48 initrd.img -> /boot/initrd.img-3.8.0-38-generic
lrwxrwxrwx   1 root root    33 Mar  8 13:06 initrd.img.old -> /boot/initrd.img-3.8.0-37-generic
drwxr-xr-x  21 root root  4096 Nov 20  2013 lib
lrwxrwxrwx   1 root root    34 Mar 25 07:54 libnss3.so -> /usr/lib/i386-linux-gnu/libnss3.so
drwx------   2 root root 16384 Oct  5  2013 lost+found
drwxr-xr-x  10 root root  4096 Dec 27  2013 media
drwxr-xr-x   2 root root  4096 Aug 18  2013 mnt
drwxr-xr-x   3 root root  4096 Oct  6  2013 opt
dr-xr-xr-x 216 root root     0 Mar  8 12:48 proc
drwx------   8 root root  4096 Oct  6  2013 root
drwxr-xr-x  26 root root  1060 May 23 13:49 run
drwxr-xr-x   2 root root 12288 Mar 12 07:37 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   3 root root  4096 Oct  9  2013 srv
dr-xr-xr-x  13 root root     0 Mar  8 12:48 sys
drwxrwxrwt  16 root root  4096 Jul  1 13:45 tmp
drwxr-xr-x  10 root root  4096 Oct  5  2013 usr
drwxr-xr-x  13 root root  4096 Feb 19 09:13 var
lrwxrwxrwx   1 root root    29 Mar 31 07:48 vmlinuz -> boot/vmlinuz-3.8.0-38-generic
lrwxrwxrwx   1 root root    29 Mar  8 13:06 vmlinuz.old -> boot/vmlinuz-3.8.0-37-generic

---

### Post by ButchMel on 2014-07-01
**Also, :**

''[B]2 - Go to Synaptic Package Manager via the System > Administration menus ''

How/where do I find ''System'' ?  (I see ''system settings'' on the desktop, but can' t find '' administrative menus'' in there, so I assume I might not be right place...  And I understand this would ease my life if I could use Synaptic, right? ... I might have jumped too quickly on conclusion I do not have it installed...[/B]

---

### Post by oldfred on 2014-07-01
Did you somehow install a gui? Not sure you can use a live installer and add synaptic to un-install from your working system. With new Unity in Ubuntu you do not have the same menus as the old system and some names have changed. But other flavors do still have menus or gnome-panel in Ubuntu has menus.

Did you try the command line suggestions from your terminal on your working system?
Of if you cannot boot into your system you may have to chroot into system to be able to maintain it.

---

### Post by Bashing-om on 2014-07-01
ButchMel; oldfred, Sheessh !

What in the world is going on here ?
You appear to be booting:
> 
To uname -r :

3.8.0-36-generic

BUT BUT ->
> 
lrwxrwxrwx 1 root root 33 Mar 31 07:48 initrd.img -> /boot/initrd.img-3.8.0-38-generic
lrwxrwxrwx 1 root root 29 Mar 31 07:48 vmlinuz -> boot/vmlinuz-3.8.0-38-generic

Is the -38 kernel not present in the /boot directory ? Best check !
```

ls -la /boot

```
To also verify what is to be removed.

(and the  -38 series kernels are installed )
> 
ii linux-image-3. 3.8.0-38.56~pr Linux kernel image for version 3.8.0 on 32 b


Maybe try and purge some of those old kernels - not the one that is currently booting ! - and see if that latest kernel will complete to installation ?

[INDENT][INDENT]worth a shot ?
[/INDENT][/INDENT]

---

### Post by ButchMel on 2014-07-06
> **oldfred said:**
> I prefer to use synaptic, but if you do not have it already installed you will not be able to install it now. So command line is only choice.


Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic
#current install:
lsb_release -a
:

I tried the following : still hetting error messages :

robert@CrabConnect:~$ sudo apt-get purge linux-image-3.8.0-{29,31,32,33,34,35}-generic
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-39-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
robert@CrabConnect:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
robert@CrabConnect:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.8.0-42-generic linux-image-generic-lts-raring
Suggested packages:
  fdutils linux-lts-raring-doc-3.8.0 linux-lts-raring-source-3.8.0
  linux-lts-raring-tools linux-headers-3.8.0-42-generic
The following NEW packages will be installed:
  linux-image-3.8.0-42-generic
The following packages will be upgraded:
  linux-image-generic-lts-raring
1 upgraded, 1 newly installed, 0 to remove and 188 not upgraded.
17 not fully installed or removed.
Need to get 50.3 MB of archives.
After this operation, 137 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-3.8.0-42-generic i386 3.8.0-42.62~precise1 [50.3 MB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise-updates/main linux-image-generic-lts-raring i386 3.8.0.42.42 [2,380 B]
Fetched 50.3 MB in 18s (2,702 kB/s)                                                    
(Reading database ... 404096 files and directories currently installed.)
Unpacking linux-image-3.8.0-42-generic (from .../linux-image-3.8.0-42-generic_3.8.0-42.62~precise1_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.8.0-42-generic_3.8.0-42.62~precise1_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.8.0-42-generic': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-42-generic /boot/vmlinuz-3.8.0-42-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-42-generic /boot/vmlinuz-3.8.0-42-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.8.0-42-generic_3.8.0-42.62~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@CrabConnect:~$ 


It really looks like it wants to install the -42 kernel version but the only thing i can understand in plain English is that the disk is full (boot)

I'm stucked with it. This machine has not been rebooted nor shutted down since I have this problem - I'm afraid it would not boot anymore, am I right ?

---

### Post by ButchMel on 2014-07-06
> **Bashing-om said:**
> ButchMel; oldfred, Sheessh !




Maybe try and purge some of those old kernels - not the one that is currently booting ! - and see if that latest kernel will complete to installation ?
[INDENT][INDENT]worth a shot ?
[/INDENT]
[/INDENT]



No way it sems to work,,,

---

### Post by bobnn on 2014-07-06
ON TOPIC:

You don't need to use dpkg to free up room in /boot.  Just delete the older files you are not using.

This will list the files sorted in time order, oldest on the bottom:

```
ls -lt
```


OFF TOPIC:

> **ButchMel said:**
> lsb_release -a

[COLOR=#ff0000]Description:	Ubuntu 12.04.3 LTS[/COLOR]
[COLOR=#ff0000]Release:	12.04[/COLOR]
[COLOR=#ff0000]Codename:	precise[/COLOR]

uname -a

[COLOR=#ff0000]3.8.0-36-generic #52~precise1-Ubuntu SMP Mon Feb 3 21:56:56 UTC 2014 i686 i686 i386 GNU/Linux[/COLOR]


OK, this is probably off topic but on my 2 12.04 LTS systems:
# lsb_release -a
```
# lsb_release -a

Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

```

```
# uname -a
Linux dell620 3.2.0-65-generic #98-Ubuntu SMP Wed Jun 11 20:27:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

**Can somebody explain how the kernels are so wildly different between mine and the OP?**

---

### Post by ButchMel on 2014-07-06
''[COLOR=#000000]You don't need to use dpkg to free up room in /boot. Just delete the older files you are not using.''

bobnn,

If only I could have an idea how to go there/do this....

As you will see from my previous posts, all commands I'm trying are failing to do the trick.  I wonder about just wiping my entire install which was fine for nearly a year, but I can't believe there no way to arrange this. I'm desperate about this. Plus the 14.04 LTS for Server is 64bit only - it won't work on this Pentium 4 ....  

And: yes I do have a GUI even if this is server.  I am not litterate enough to go with the no-GUI interface.
[/COLOR]

---

### Post by Bashing-om on 2014-07-06
ButchMel; Hey !

I am still on this.... And still things I can not comprehend as to what has happened.
> 
lrwxrwxrwx 1 root root 33 Mar 31 07:48 initrd.img -> /boot/initrd.img-3.8.0-38-generic

when the -38 kernel IS NOT installed !

However, the 1st order of business is to get some operating head room in the /boot directory. I have a thought and a plan in mind.
Show us the output of terminal command:
```

dpkg -l | grep linux-

```

And I will craft up a command to remove some of those old images and headers files, then see what we can do about that mis-directed symlink for the booting kernel.

1st time for everything and I am
[INDENT][INDENT][INDENT]in a learning mode
[/INDENT][/INDENT][/INDENT]

---

### Post by bobnn on 2014-07-06
> **ButchMel said:**
> 
bobnn,

If only I could have an idea how to go there/do this....


So, I see that nobody actually suggested simply deleting the files, without using the package manager.

I mean literally remove the files using rm.

Open a terminal window in the GUI.

In that Window:

```
cd /boot
ls -lt
...
sudo rm <filename> <filename> <filename>
```

Where each <filename> is copy-pasted from the bottom of the list produced by 
```
ls -lt
```

In the terminal window (that is run in GUI), drag across the name to highlight the name - which copies into a buffer, then center-click to paste the name from the buffer into the command-line.

Avoid deleting symlinks, the things that look like:

```
**l**rwxrwxrwx 1 root root 33 Mar 31 07:48 initrd.img **->** /boot/initrd.img-3.8.0-38-generic
```
Where the leading "l" means a link.

---

### Post by Bashing-om on 2014-07-07
@ bobnn,

As to your advisement:
Not a good course of action in that the package manager becomes broken, and that "might" be a real pain to fix after removing the images manually.

A lower lever tool is available to do the removal in a much cleaner fashion. 

When the requested output is provided I will craft up the sequence to cleanly remove the images and headers files.

But, I do agree
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by bobnn on 2014-07-07
> **Bashing-om said:**
> @ bobnn,

As to your advisement:
Not a good course of action in that the package manager becomes broken, and that "might" be a real pain to fix after removing the images manually.


Hmmm  - well you know more aboutit than I do.  

I will say that I've been doing what I advised for years, but I don't typically do a lot of dpkg stuff - unless I get it from someone like you.  I do get that it doesn't remove headers and other stuff.


Separately, I figured out why my kernel is so much lower level than some others, or at least part of it - I had no idea, until I searched this forum, that i could choose 3.2, 3.5 or 3.8 kernels that were all "official" for 12.04.

---

### Post by ButchMel on 2014-07-07
> **Bashing-om said:**
> ButchMel; Hey !


However, the 1st order of business is to get some operating head room in the /boot directory. I have a thought and a plan in mind.
Show us the output of terminal command:
```

dpkg -l | grep linux-

```

And I will craft up a command to remove some of those old images and headers files, then see what we can do about that mis-directed symlink for the booting kernel.

1st time for everything and I am[INDENT][INDENT][INDENT]in a learning mode
[/INDENT]
[/INDENT]
[/INDENT]



Thanks again to you. Here's the output:

robert@CrabConnect:~$ dpkg -l | grep linux-
ii  linux-firmware                         1.79.12                                 Firmware for Linux kernel drivers
iU  linux-generic-lts-raring               3.8.0.39.39                             Generic Linux kernel image and headers
ii  linux-headers-3.8.0-29                 3.8.0-29.42~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-29-generic         3.8.0-29.42~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-31                 3.8.0-31.46~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-31-generic         3.8.0-31.46~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                 3.8.0-32.47~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-32-generic         3.8.0-32.47~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-33                 3.8.0-33.48~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-33-generic         3.8.0-33.48~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-34                 3.8.0-34.49~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-34-generic         3.8.0-34.49~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-35                 3.8.0-35.52~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-35-generic         3.8.0-35.52~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-36                 3.8.0-36.52~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-36-generic         3.8.0-36.52~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-37                 3.8.0-37.53~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-37-generic         3.8.0-37.53~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-38                 3.8.0-38.56~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-38-generic         3.8.0-38.56~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-39                 3.8.0-39.57~precise1                    Header files related to Linux kernel version 3.8.0
ii  linux-headers-3.8.0-39-generic         3.8.0-39.57~precise1                    Linux kernel headers for version 3.8.0 on 32 bit x86 SMP
ii  linux-headers-generic-lts-raring       3.8.0.39.39                             Generic Linux kernel headers
ii  linux-image-3.8.0-29-generic           3.8.0-29.42~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-31-generic           3.8.0-31.46~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-32-generic           3.8.0-32.47~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-33-generic           3.8.0-33.48~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-34-generic           3.8.0-34.49~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-35-generic           3.8.0-35.52~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-36-generic           3.8.0-36.52~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-37-generic           3.8.0-37.53~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-38-generic           3.8.0-38.56~precise1                    Linux kernel image for version 3.8.0 on 32 bit x86 SMP
iU  linux-image-generic-lts-raring         3.8.0.39.39                             Generic Linux kernel image
ii  linux-libc-dev                         3.2.0-60.91                             Linux Kernel Headers for development
ii  linux-sound-base                       1.0.25+dfsg-0ubuntu1.1                  base package for ALSA and OSS sound systems
ii  syslinux-common                        2:4.05+dfsg-2                           collection of boot loaders (common files)
ii  syslinux-legacy                        2:3.63+dfsg-2ubuntu5                    Bootloader for Linux/i386 using MS-DOS floppies




I don't know if this may help, but here is a note I have (since many weeks - and no way to get rid of) in the circled ''-'' on top right of screen:

[COLOR=#0000ff]*'' An error occured. Please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The Error message was 'Error: BrokenCount >0'. This usually means that your installed packages have unmet dependencies''*[/COLOR]

Guess this around what many of you asked me to do, which turned to no result....

---

### Post by ButchMel on 2014-07-07
Thanks very much bobnn.

Ok I will wait then for Bashing-om reply.

---

### Post by Bashing-om on 2014-07-07
@ bobnn; Hey, 
No biigy, we are trying to do this right, and not make the situation worse than it is.
//
One may choose to use the kernels from later releases, see:
[http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement](http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

-------------------------
@ ButchMel; Well Well;

I am much relieved to see that the -38 image is in fact installed:
> 
ii linux-image-3.8.0-38-generic 3.8.0-38.56~precise1 Linux kernel image for version 3.8.0 on 32 bit x86 SMP


Roll our sleeves up and get some operating head room, get ready to go to work.
```

sudo dpkg -P linux-image-3.8.0-{29,31,32,33,34,35}-generic
sudo dpkg -P linux-headers-3.8.0-{29,31,32,33,34,35}-generic
sudo dpkg -P linux-headers-3.8.0-{29,31,32,33,34,35}

```

Now let's see what the package manager advises:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade ##to get and install the later kernel versions##

```
depending on that outcome is what we do next.

could be
[INDENT][INDENT][INDENT]all rosy at this point
[/INDENT][/INDENT][/INDENT]

---

### Post by bobnn on 2014-07-08
> **Bashing-om said:**
> @ bobnn; Hey, 
No biigy, we are trying to do this right, and not make the situation worse than it is.
//
One may choose to use the kernels from later releases, see:
[http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement](http://askubuntu.com/questions/248914/what-is-hwe-hardware-enablement)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)



Bashing-om:  Thanks for those links clarifying the Kernel situation - that secodn link in particular made every thing clear.

Awesome that I'll be able to try newer kernels when/if I buy newer H/W!

---

### Post by Bashing-om on 2014-07-08
Off topic, while awaiting the OP !
@ bobnn; Hey, Like this

This is open source at it's best - share and share alike . I have been around more years than I care to think about and This, our operating system of choice, in my opinion, is the greatest thing we have ever known in this context of a realm of computers.

We have the technology,
[INDENT][INDENT][INDENT]we have the tools
[INDENT][INDENT][INDENT][INDENT]look what we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ButchMel on 2014-07-10
Hi Bashing-Om,

Thanks again.

Output to firts 3  codes appeared to go through. However, please see output to 3 following codes:

```
robert@CrabConnect:~$ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release.gpg                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [106 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.7 kB]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,795 B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [433 kB]  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex             
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Sources [473 kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [99.1 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,650 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Sources [8,056 B]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Sources [108 kB]  
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Sources [8,905 B]
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages [846 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.7 kB]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages [250 kB]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Sources  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,514 kB in 3s (647 kB/s)
Reading package lists... Done
robert@CrabConnect:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-39-generic but it is not installed
E: Unmet dependencies. Try using -f.
robert@CrabConnect:~$ sudo apt-get dist-upgrade ##to get and install the later kernel versions##
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-39-generic but it is not installed
E: Unmet dependencies. Try using -f.
robert@CrabConnect:~$ 
```


What should I understand here ?

Thanks again for your precious time.

---

### Post by ButchMel on 2014-07-10
If output to first 3 codes can also be useful, before I close terminal, here they are :

```
robert@CrabConnect:~$ sudo dpkg -P linux-image-3.8.0-{29,31,32,33,34,35}-generic[sudo] password for robert: 
(Reading database ... 404095 files and directories currently installed.)
Removing linux-image-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found linux image: /boot/vmlinuz-3.8.0-31-generic
Found initrd image: /boot/initrd.img-3.8.0-31-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-29-generic /boot/vmlinuz-3.8.0-29-generic
Removing linux-image-3.8.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found linux image: /boot/vmlinuz-3.8.0-32-generic
Found initrd image: /boot/initrd.img-3.8.0-32-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-31-generic /boot/vmlinuz-3.8.0-31-generic
Removing linux-image-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found linux image: /boot/vmlinuz-3.8.0-33-generic
Found initrd image: /boot/initrd.img-3.8.0-33-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-32-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-32-generic /boot/vmlinuz-3.8.0-32-generic
Removing linux-image-3.8.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-34-generic
Found initrd image: /boot/initrd.img-3.8.0-34-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-33-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-33-generic /boot/vmlinuz-3.8.0-33-generic
Removing linux-image-3.8.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-34-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-34-generic /boot/vmlinuz-3.8.0-34-generic
Removing linux-image-3.8.0-35-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
update-initramfs: Deleting /boot/initrd.img-3.8.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-38-generic
Found initrd image: /boot/initrd.img-3.8.0-38-generic
Found linux image: /boot/vmlinuz-3.8.0-37-generic
Found initrd image: /boot/initrd.img-3.8.0-37-generic
Found linux image: /boot/vmlinuz-3.8.0-36-generic
Found initrd image: /boot/initrd.img-3.8.0-36-generic
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-3.8.0-35-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.8.0-35-generic /boot/vmlinuz-3.8.0-35-generic
robert@CrabConnect:~$ sudo dpkg -P linux-headers-3.8.0-{29,31,32,33,34,35}-generic
(Reading database ... 375190 files and directories currently installed.)
Removing linux-headers-3.8.0-29-generic ...
Removing linux-headers-3.8.0-31-generic ...
Removing linux-headers-3.8.0-32-generic ...
Removing linux-headers-3.8.0-33-generic ...
Removing linux-headers-3.8.0-34-generic ...
Removing linux-headers-3.8.0-35-generic ...
robert@CrabConnect:~$ sudo dpkg -P linux-headers-3.8.0-{29,31,32,33,34,35}
(Reading database ... 320457 files and directories currently installed.)
Removing linux-headers-3.8.0-29 ...
Removing linux-headers-3.8.0-31 ...
Removing linux-headers-3.8.0-32 ...
Removing linux-headers-3.8.0-33 ...
Removing linux-headers-3.8.0-34 ...
Removing linux-headers-3.8.0-35 ...
robert@CrabConnect:~$ sudo apt-get update
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release.gpg                           
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release.gpg                 
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise Release                               
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [106 kB]        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_CA                         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Sources                          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Sources             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe i386 Packages       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse i386 Packages     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main TranslationIndex        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse TranslationIndex  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [30.7 kB]   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,795 B] 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [433 kB]  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe TranslationIndex             
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Sources [473 kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [99.1 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,650 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [72 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:18 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Sources [8,056 B]
Get:19 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Sources [108 kB]  
Get:20 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Sources [8,905 B]
Get:21 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main i386 Packages [846 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_CA                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:22 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted i386 Packages [13.7 kB]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe i386 Packages [250 kB]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse i386 Packages [15.5 kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Sources  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe TranslationIndex
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) precise-backports/universe Translation-en
Fetched 2,514 kB in 3s (647 kB/s)
Reading package lists... Done
```


My assessment is that the final ''done'' sounds good :)

---

### Post by deadflowr on 2014-07-10
> **bobnn said:**
> So, I see that nobody actually suggested simply deleting the files, without using the package manager.

I mean literally remove the files using rm.
<snip>

The reason would be that, after doing so, those packages will still be listed in the software database, if later on you needed to do something, chances are high that problems will occur.
On top of the fact that the linux-image packages include parts which are not installed in the boot folder.
It just causes trouble, all around.
There are a few users who could, unfortunately tell you those troubles.
> **ButchMel said:**
> If output to first 3 codes can also be useful, before I close terminal, here they are :
<snip>

My assessment is that the final ''done'' sounds good :)

Looks good, as far as the linux-image packages go.
what does 
```
ls /boot
```
look like.
as long as one version number is still listed, should be good.
If one is listed or it's files are listed, the only thing to try is a quick reboot to make sure.

Also, when posting  outputs from the terminal, [use code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"), or the thread can get overbearingly long

---

### Post by Bashing-om on 2014-07-10
ButchMel; Looking better !

Should have some operating room now.

I do not see where " sudo apt-get dist-upgrade" was run; and, we still have:
> 
The following packages have unmet dependencies:
 linux-image-generic-lts-raring : Depends: linux-image-3.8.0-39-generic but it is not installed

Take a look at '/boot' as deadflowr advises, and see where we stand. Once we know this we can consider rebooting and see what the system then boots up for the kernel.
Finish the cleanup of older kernels and other obsolete materials.

[INDENT][INDENT]is that light there
[INDENT][INDENT][INDENT]at the end of the tunnel ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ButchMel on 2014-07-12
deadflowr,

ls /boot 

Here is what I get - quite short, but should I understand there are still 3 versions ? (better then the dozen that were there though). I will wait advice prior to reboot - just to make sure lack of space prevent the system from restarting ??  Thanks ! 

robert@CrabConnect:~$ ls /boot
abi-3.8.0-36-generic         lost+found
abi-3.8.0-37-generic         memtest86+.bin
abi-3.8.0-38-generic         memtest86+_multiboot.bin
config-3.8.0-36-generic      System.map-3.8.0-36-generic
config-3.8.0-37-generic      System.map-3.8.0-37-generic
config-3.8.0-38-generic      System.map-3.8.0-38-generic
grub                         vmlinuz-3.8.0-36-generic
initrd.img-3.8.0-36-generic  vmlinuz-3.8.0-37-generic
initrd.img-3.8.0-37-generic  vmlinuz-3.8.0-38-generic
initrd.img-3.8.0-38-generic
robert@CrabConnect:~$

---

### Post by ButchMel on 2014-07-16
Anyone can tell me if I might take a risk to reboot ?

---

### Post by oldfred on 2014-07-16
I often suggest running these commands. This is from a chroot so no sudo reqired on each line, but you can put it in sudo mode if not chrooted. Pr use sudo on each line.

 #Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

If that all runs without error then you should be able to reboot.

---

### Post by ButchMel on 2014-07-19
oldfred,

On the command apt-get dist-upgrade, since I got some broken packages errors, I redid it as is: sudo -i apt-get dist-upgrade -f



Not sure this is what you meant... Just in case, wanted to write it - as it now looks everything is being replaced over last 10 minutes.
 
At the very end (I pass the hundreds of lines that ran):

Setting up libdevmapper-event1.02.1 (2:1.02.48-4ubuntu7.4) ...
Setting up lvm2 (2.02.66-4ubuntu7.4) ...
update-initramfs: deferring update (trigger activated)
Setting up liblvm2app2.2 (2.02.66-4ubuntu7.4) ...
Setting up libreoffice-help-en-us (1:3.5.7-0ubuntu6.1) ...
Processing triggers for libreoffice-common ...
Setting up libreoffice-emailmerge (1:3.5.7-0ubuntu6.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-44-generic
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 linux-image-generic-lts-raring
 linux-generic-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)

I went with the last two lines (in your last reply) anyway 

[COLOR=#000000]apt-get -f install[/COLOR]
[COLOR=#000000]dpkg --configure -a
[/COLOR]


Then got the following:

robert@CrabConnect:~$ sudo -i apt-get -f install
[sudo] password for robert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 libubuntuoneui-3.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-generic-lts-raring
The following packages will be upgraded:
  linux-image-generic-lts-raring
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,382 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-image-generic-lts-raring:
 linux-image-generic-lts-raring depends on linux-image-3.8.0-39-generic; however:
  Package linux-image-3.8.0-39-generic is not installed.
dpkg: error processing linux-image-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-raring:
 linux-generic-lts-raring depends on linux-image-generic-lts-raring; however:
  Package linux-image-generic-lts-raring is not configured yet.
dpkg: error processing linux-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-generic-lts-raring
 linux-generic-lts-raring
E: Sub-process /usr/bin/dpkg returned an error code (1)
robert@CrabConnect:~$ sudo -i dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic-lts-raring:
 linux-image-generic-lts-raring depends on linux-image-3.8.0-39-generic; however:
  Package linux-image-3.8.0-39-generic is not installed.
dpkg: error processing linux-image-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-raring:
 linux-generic-lts-raring depends on linux-image-generic-lts-raring; however:
  Package linux-image-generic-lts-raring is not configured yet.
dpkg: error processing linux-generic-lts-raring (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic-lts-raring
 linux-generic-lts-raring


Anything else I should try before rebooting ?

---

### Post by ButchMel on 2014-07-19
Ok guys: one good and one bad news:

- the good news: after my previous post above and despite the errors messages, I chosed to risk everything and restarted system and.... it restarted.

- the bad new is : I still see under that circled ''-'' on top right that ''an error occured... run package manager from right-click...or apt-get in terminal to see what is wrong... Error BrokenCount >0 - usually means that installed packages have unmet dependencies''....

I feel I'm running the GroundHog Day again :-) 

Any step I should do or redo ?

I sincerely appreciate your help and patience with me.

---

### Post by oldfred on 2014-07-19
If you do sudo -i, then you do not need sudo on every line. But you then have to exit sudo mode.

Are you running an Enablement stack? Or 12.04.2 or later?
It seems they have some things out of sync, see links below.

       Info on updates to LTS Enablement stacks
[http://ubuntuforums.org/showthread.php?t=2234693&p=13074774#post13074774](http://ubuntuforums.org/showthread.php?t=2234693&p=13074774#post13074774)
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by ButchMel on 2014-07-20
Is this basically saying I should upgrade to 14.xx ?

If so, I run this server on an old Pentium IV ... And 14.0x says to run only 64bit... I doubt this hardware is 64bit....

---

### Post by oldfred on 2014-07-20
They still have 14.04 32 bit. 

But if you have a new UEFI system then you have to use 64 bit, old systems should use 32 bit. 

If running desktop then full Ubuntu with Unity is too much for old systems, but server should be fine. Even if you add one of the lightweight window managers.

---

