---
title: "New to ubuntu, failing to update system software"
date: 2018-11-03
forum: New to Ubuntu
---

### Post by pschwa363 on 2018-11-03
I was trying to update from ubuntu 16.04 lts and while running the software updater, it got partway through the update process before telling me i didn't have enough disk space. it prompted me to run the command "sudo apt autoremove" in order to make more space and i did, however i still don't have enough and (not being knowledgeable in the way of computers) am struggling to figure out how i can make enough space to run the update. looking for anyone who may be able to tell me how to accomplish this

---

### Post by Bashing-om on 2018-11-03
pschwa363; Hello - Welcome to the forum :)

Wonder why "autoremove" was unable to get the required space back .

Let's begin the investigation process by looking at the disk file usage.
Post back - between code tags - the outputs of terminal commands:
```

df -h
df -i

```
where we can then focus on (d)isk (u)sage.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]longest journey starts with that 1st step
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-03
alright, thanks for stopping by to help me out. for the first fucntion

```
Filesystem                   Size  Used Avail Use% Mounted on
udev                         920M     0  920M   0% /dev
tmpfs                        191M  8.6M  182M   5% /run
/dev/mapper/ubuntu--vg-root   26G  8.7G   16G  36% /
tmpfs                        951M  256K  950M   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        951M     0  951M   0% /sys/fs/cgroup
/dev/loop0                    88M   88M     0 100% /snap/core/5742
/dev/loop2                   102M  102M     0 100% /snap/ubuntu-social-kit/3
/dev/loop1                    83M   83M     0 100% /snap/ubuntu-social-kit/2
/dev/loop3                    88M   88M     0 100% /snap/core/5662
/dev/loop4                    76M   76M     0 100% /snap/hexchat/42
/dev/loop5                    88M   88M     0 100% /snap/core/5328
/dev/mmcblk0p2               473M  214M  235M  48% /boot
/dev/mmcblk0p1               511M  3.5M  508M   1% /boot/efi
tmpfs                        191M  4.0K  191M   1% /run/user/108
tmpfs                        191M   76K  190M   1% /run/user/1000
/home/preston/.Private        26G  8.7G   16G  36% /home/preston
/dev/mmcblk1p1               118G  352K  118G   1% /media/preston/My SD Files
/dev/mmcblk1p2                14M  132K   13M   2% /media/preston/Linux Memory

```

for the command "df -i"
```
Filesystem                   Inodes  IUsed   IFree IUse% Mounted on
udev                         235520    559  234961    1% /dev
tmpfs                        243258    819  242439    1% /run
/dev/mapper/ubuntu--vg-root 1720320 290497 1429823   17% /
tmpfs                        243258     60  243198    1% /dev/shm
tmpfs                        243258      6  243252    1% /run/lock
tmpfs                        243258     17  243241    1% /sys/fs/cgroup
/dev/loop0                    12783  12783       0  100% /snap/core/5742
/dev/loop2                    23472  23472       0  100% /snap/ubuntu-social-kit/3
/dev/loop1                    22006  22006       0  100% /snap/ubuntu-social-kit/2
/dev/loop3                    12783  12783       0  100% /snap/core/5662
/dev/loop4                    23099  23099       0  100% /snap/hexchat/42
/dev/loop5                    12860  12860       0  100% /snap/core/5328
/dev/mmcblk0p2               124928    306  124622    1% /boot
/dev/mmcblk0p1                    0      0       0     - /boot/efi
tmpfs                        243258     33  243225    1% /run/user/1000
/home/preston/.Private      1720320 290497 1429823   17% /home/preston
/dev/mmcblk1p1                    0      0       0     - /media/preston/My SD Files
/dev/mmcblk1p2                 3840     11    3829    1% /media/preston/Linux Memory

```

---

### Post by Bashing-om on 2018-11-03
pschwa363; Hummmm .........

All I can see here is maybe:
> 
/dev/mmcblk0p2               473M  214M  235M  48% /boot

where 235M might be too small, as I calculate that now it takes 335 MB of disk space for a full kernel install.
What is installed in that /boot partition ?
```

dpkg -l | grep linux-

```

[INDENT]6 pounds of sugar in a 5 pound sack ?
[/INDENT]

---

### Post by pschwa363 on 2018-11-03
i have no idea tbh. are those commands to run in terminal?

---

### Post by Bashing-om on 2018-11-03
pschwa363; Uh huh ..

My apologies for not being clear/
Terminal command:
```

dpkg -l | grep linux-

```
and pass the results back here - between code tags .


[INDENT][INDENT]little things do matter
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-03
you were no more unclear than i am clueless. 


```
ii  linux-base                                  4.5ubuntu1~16.04.1                           all          Linux image base package
ii  linux-firmware                              1.157.20                                     all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-16.04                     4.15.0.38.61                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-33                     4.15.0-33.36~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic             4.15.0-33.36~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-36                     4.15.0-36.39~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-36-generic             4.15.0-36.39~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-38                     4.15.0-38.41~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-38-generic             4.15.0-38.41~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-16.04             4.15.0.38.61                                 amd64        Generic Linux kernel headers
rc  linux-image-4.10.0-42-generic               4.10.0-42.46~16.04.1                         amd64        Linux kernel image for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-26-generic               4.13.0-26.29~16.04.2                         amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-4.15.0-33-generic               4.15.0-33.36~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-36-generic               4.15.0-36.39~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-38-generic               4.15.0-38.41~16.04.1                         amd64        Signed kernel image generic
rc  linux-image-4.8.0-36-generic                4.8.0-36.36~16.04.1                          amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-39-generic                4.8.0-39.42~16.04.1                          amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-41-generic                4.8.0-41.44~16.04.1                          amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-49-generic                4.8.0-49.52~16.04.1                          amd64        Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.10.0-42-generic         4.10.0-42.46~16.04.1                         amd64        Linux kernel extra modules for version 4.10.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-26-generic         4.13.0-26.29~16.04.2                         amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-36-generic          4.8.0-36.36~16.04.1                          amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-39-generic          4.8.0-39.42~16.04.1                          amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-41-generic          4.8.0-41.44~16.04.1                          amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-49-generic          4.8.0-49.52~16.04.1                          amd64        Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-generic-hwe-16.04               4.15.0.38.61                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        4.4.0-138.164                                amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-33-generic             4.15.0-33.36~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-36-generic             4.15.0-36.39~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-38-generic             4.15.0-38.41~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-33-generic       4.15.0-33.36~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-36-generic       4.15.0-36.39~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-38-generic       4.15.0-38.41~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic-hwe-16.04              4.15.0.38.61                                 amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
rc  linux-signed-image-4.10.0-42-generic        4.10.0-42.46~16.04.1                         amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-26-generic        4.13.0-26.29~16.04.2                         amd64        Signed kernel image generic
rc  linux-signed-image-4.8.0-39-generic         4.8.0-39.42~16.04.1                          amd64        Signed kernel image generic
rc  linux-signed-image-4.8.0-41-generic         4.8.0-41.44~16.04.1                          amd64        Signed kernel image generic
rc  linux-signed-image-4.8.0-49-generic         4.8.0-49.52~16.04.1                          amd64        Signed kernel image generic
ii  linux-signed-image-generic-hwe-16.04        4.15.0.38.61                                 amd64        Signed Generic Linux kernel image (dummy transitional package)
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

---

### Post by Bashing-om on 2018-11-04
pschwa363; Well !

> 
ii  linux-generic-hwe-16.04 
ii  linux-modules-extra-4.15.0-38-generic

begs the question of what you are running.

Show us -
```

lsb_release -a
uname -r

```

we do know we can squeeze a bit more room - but check 1st on how to proceed.

[INDENT]measure twice - cut once
[/INDENT]

---

### Post by pschwa363 on 2018-11-04
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.5 LTS
Release:    16.04
Codename:    xenial

```

```
4.15.0-38-generic

```

---

### Post by Bashing-om on 2018-11-04
pschwa363; Ho kay .

run:
```

sudo apt remove linux-headers-4.15.0-33-generic
sudo apt remove linux-headers-4.15.0-33
sudo apt remove linux-image-4.15.0-33-generic
sudo apt remove linux-image-extra-4.15.0-33-generic

```
to remove that one kernel we can safely do so ..

And run:
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```
While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with that ^^ command.

Now lets see if there is space available:
show us a new:
```

df -h

```

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-04
when i run the first commands, i get the following

```
sudo: unable to resolve host prestons-laptop: Connection timed out
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?


```

nevermind, the updating was still open in the background...

so here is what i'm working with now

```
Filesystem                   Size  Used Avail Use% Mounted on
udev                         920M     0  920M   0% /dev
tmpfs                        191M  8.6M  182M   5% /run
/dev/mapper/ubuntu--vg-root   26G  8.7G   16G  36% /
tmpfs                        951M   62M  889M   7% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        951M     0  951M   0% /sys/fs/cgroup
/dev/loop0                    88M   88M     0 100% /snap/core/5742
/dev/loop2                   102M  102M     0 100% /snap/ubuntu-social-kit/3
/dev/loop1                    83M   83M     0 100% /snap/ubuntu-social-kit/2
/dev/loop3                    88M   88M     0 100% /snap/core/5662
/dev/loop4                    76M   76M     0 100% /snap/hexchat/42
/dev/loop5                    88M   88M     0 100% /snap/core/5328
/dev/mmcblk0p2               473M  215M  234M  48% /boot
/dev/mmcblk0p1               511M  3.5M  508M   1% /boot/efi
tmpfs                        191M   64K  190M   1% /run/user/1000
/home/preston/.Private        26G  8.7G   16G  36% /home/preston
/dev/mmcblk1p1               118G  352K  118G   1% /media/preston/My SD Files
/dev/mmcblk1p2                14M  132K   13M   2% /media/preston/Linux Memory

```

---

### Post by Bashing-om on 2018-11-04
pschwa363. Huh ?? 

Something screwy here as there is more space used now - after removing that kernel !

what shows:
```

sudo apt autoremove
dpkg -l | grep linux-

```

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-04
autoremove comes up with nothing

```
sudo: unable to resolve host prestons-laptop: Connection timed out
[sudo] password for preston: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1528 not upgraded.


```

```
ii  linux-base                                  4.5ubuntu1~16.04.1                           all          Linux image base package
ii  linux-firmware                              1.157.20                                     all          Firmware for Linux kernel drivers
ii  linux-generic-hwe-16.04                     4.15.0.38.61                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-36                     4.15.0-36.39~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-36-generic             4.15.0-36.39~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-38                     4.15.0-38.41~16.04.1                         all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-38-generic             4.15.0-38.41~16.04.1                         amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic-hwe-16.04             4.15.0.38.61                                 amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-36-generic               4.15.0-36.39~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-4.15.0-38-generic               4.15.0-38.41~16.04.1                         amd64        Signed kernel image generic
ii  linux-image-generic-hwe-16.04               4.15.0.38.61                                 amd64        Generic Linux kernel image
ii  linux-image-unsigned-4.15.0-33-generic      4.15.0-33.36                                 amd64        Linux kernel image for version 4.15.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                        4.4.0-138.164                                amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-33-generic             4.15.0-33.36~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-36-generic             4.15.0-36.39~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-38-generic             4.15.0-38.41~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-33-generic       4.15.0-33.36                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-36-generic       4.15.0-36.39~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-38-generic       4.15.0-38.41~16.04.1                         amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic-hwe-16.04              4.15.0.38.61                                 amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-signed-image-generic-hwe-16.04        4.15.0.38.61                                 amd64        Signed Generic Linux kernel image (dummy transitional package)
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies


```

---

### Post by Bashing-om on 2018-11-04
pschwa363; Whowww ./.

> 
1528 not upgraded
 !!

We got to get this system updated.
```

sudo apt update
sudo apt full-upgrade

```

see where this leads -

---

### Post by pschwa363 on 2018-11-04
ok, so i ran the update through terminal. what info do you need from me now?

---

### Post by Bashing-om on 2018-11-04
pschwa363; Good deal ..

All ran and no errors ?

We need to finish up what I failed to have you remove:
```

sudo apt remove linux-modules-extra-4.15.0-33-generic
sudo apt remove linux-modules-4.15.0-33-generic

```

and now anything adverse:
```

sudo apt update
sudo apt autoremove 

```

[INDENT][INDENT]as we move smartly on along
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-04
so it says all packages are up to date now
ran the autoremove

```
Filesystem                   Size  Used Avail Use% Mounted on
udev                         920M     0  920M   0% /dev
tmpfs                        191M  1.3M  189M   1% /run
/dev/mapper/ubuntu--vg-root   26G  9.2G   16G  38% /
tmpfs                        951M   41M  910M   5% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        951M     0  951M   0% /sys/fs/cgroup
/dev/loop0                    88M   88M     0 100% /snap/core/5742
/dev/loop2                   102M  102M     0 100% /snap/ubuntu-social-kit/3
/dev/loop1                    83M   83M     0 100% /snap/ubuntu-social-kit/2
/dev/loop3                    88M   88M     0 100% /snap/core/5662
/dev/loop4                    76M   76M     0 100% /snap/hexchat/42
/dev/loop5                    88M   88M     0 100% /snap/core/5328
/dev/mmcblk0p2               473M  155M  294M  35% /boot
/dev/mmcblk0p1               511M  6.1M  505M   2% /boot/efi
tmpfs                        191M   64K  190M   1% /run/user/1000
/home/preston/.Private        26G  9.2G   16G  38% /home/preston
/dev/mmcblk1p1               118G  352K  118G   1% /media/preston/My SD Files
/dev/mmcblk1p2                14M  132K   13M   2% /media/preston/Linux Memory

```

---

### Post by Bashing-om on 2018-11-04
pschwa363  outstanding ..

Prep for try again to release-upgrade -

Any 3rd party soft\ware - PPAs ?

```

tail -v -n +1 /etc/apt/sources.list.d/*
grep -i ^prompt /etc/update-manager/release-upgrades

```

[INDENT]ready. set ....
 [/INDENT]

---

### Post by pschwa363 on 2018-11-04
> 

Prep for try again to release-upgrade -

Any 3rd party soft\ware - PPAs ?

forgive my ignorance, but i don't know what PPAs are

> 
tail -v -n +1 /etc/apt/sources.list.d/*


came up with the following error

```
tail: cannot open '/etc/apt/sources.list.d/*' for reading: No such file or directory


```

---

### Post by Bashing-om on 2018-11-04
pschwa363; hey 

That last is a good thing - NO PPAs :)
> 
A Personal Package Archive (PPA) can provide alternate software not normally available in the offical 
               Ubuntu repositories - Looking for a PPA? See [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) - WARNING: PPAs are 
               unsupported third-party packages, and you use them at your own risk.



grep -i ^prompt /etc/update-manager/release-upgrades ??

[INDENT]ready, set[/INDENT]

---

### Post by pschwa363 on 2018-11-04
```

Prompt=lts

```

---

### Post by Bashing-om on 2018-11-04
pschwa363l HO Kay

try again:
```

sudo do-release-upgrade

```

see now if ya get to 18,04 .

[INDENT][INDENT]....Go
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-04
```

no new release found

```

huh?

---

### Post by Bashing-om on 2018-11-04
pschwa363 -  Huh - Yeah !

Well past my bed time ,, and eyes are crossing .

we pick this back up tomorrow .

[INDENT]I hate when this happens
[/INDENT]

---

### Post by pschwa363 on 2018-11-04
Sounds like a plan. Thanks a million times over for all of your help so far!

---

### Post by pschwa363 on 2018-11-04
Quick update: impatience got the better of me last night and I tried using the software update application. It all seemed successful, prompted me to restart the computer, but since then, as it moves from the encryption screen to the user log in, something is wrong with the display. The screen goes black but I know it's still functioning. I'm gonna try a few things and see if I can find out how to get the display back to normal

Second update: time for a game of good news/bad news. Good news is the update went through and I am now running on 18.04.1 lts. The bad news is that now my display has gone haywire. The current issues are as follows:

1) Upon startup the display initially works, then fails when I reach the login screen. The screen goes black. I can get past this by connecting the computer to a second monitor.
2) After using this method to get the display functional again, it displays in portrait mode instead of landscape once it reaches the desktop. I have found no options in the display application to reverse this change. If I turn it sideways so I can actually read, it reverts to landscape until it is flipped upright again.

This laptop is an "all in one" model where the screen can fold back until it touches the bottom of the computer, to act as a tablet. Previously on Ubuntu when I was running 16.04, this feature didn't function at all. Now it just doesn't function properly. I would prefer to have it functional, but if it's much easier to disable this feature and have it act as a standard laptop, I am absolutely ok with it. 

I'm almost beginning to believe that this machine is just an manifestation of chaos itself...

---

### Post by Bashing-om on 2018-11-04
pschwa363' Well ! 

Good progress made .
A quicky here, and then move this new issue to a new thread.

What we might have here now is a graphic's driver issue.

show:
```

sudo lshw -C display
lspci -k|grep -iEA5 'vga|3d'

```

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by pschwa363 on 2018-11-04
Bashing-Om, thanks for coming back to help

so i ran both of those commands through the terminal, but at the moment i am struggling to copy and paste. i can highlight the text, but right clicking doesn't create the drop down menu to copy it

edit: attaching a usb mouse did the trick

```
  *-display                 
       description: VGA compatible controller
       product: Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 21
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:121 memory:80000000-80ffffff memory:90000000-9fffffff ioport:f000(size=64) memory:c0000-dffff


```

```
00:02.0 VGA compatible controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller (rev 21)
    Subsystem: ASUSTeK Computer Inc. Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Integrated Graphics Controller
    Kernel driver in use: i915
    Kernel modules: i915
00:0b.0 Signal processing controller: Intel Corporation Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller (rev 21)
    Subsystem: ASUSTeK Computer Inc. Atom/Celeron/Pentium Processor x5-E8000/J3xxx/N3xxx Series Power Management Controller
preston@prestons-laptop:~$ ^C


```

---

### Post by Bashing-om on 2018-11-04
pschwa363; Ouch - 

Just do not know. Intel graphics are not in my tool box. The driver is loaded and available - with Intel it "just works" .

Let's close this thread as solved as you are now up on 18.04:
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

And open a new thread on this new issue to gain a wider audience - with those who do know,

[INDENT][INDENT]thread - like dead men
[INDENT][INDENT]one to a box
[/INDENT][/INDENT][/INDENT][/INDENT]

---

