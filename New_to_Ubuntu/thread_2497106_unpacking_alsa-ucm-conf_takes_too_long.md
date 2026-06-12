---
title: "unpacking alsa-ucm-conf takes too long"
date: 2024-04-23
forum: New to Ubuntu
---

### Post by ramaka78 on 2024-04-23
I found some instructions when researching how to set up Ubuntu OS ubuntu-22.04.4 as NAS server, first step was to install updates and used as suggested
sudo apt update && sudo apt upgrade -y 
[FONT=-apple-system]but the progress got stuck at 31% since an hour..not sure how long it will take :-(


[IMG]file:///C:/UserData/z0045zxd/OneDrive%20-%20Siemens%20AG/Desktop/Ubuntu_package_update.jpg[/IMG]
[/FONT]

---

### Post by TheFu on 2024-04-23
> but the progress got stuck at 31% since an hour..not sure how long it will take

It depends.
Most of the time, upgrades take 5-30 seconds, but there are all sorts of things that can impact it.  How fast is the connection to the internet? How many packages were being updated? What is the total size of the updates?

BTW, you can cntl-c out of the commands, then run them 1 at a time, to split up the 2 tasks.  The update that gets the current list of all packages in your configured repos shouldn't be too long.  The upgrade is where the currently installed versions of software is compared to the list in the updated repos, dependencies are determined, then the required depend packages are downloaded and installed for each of the packages that needs to be updated.

BTW, please don't post images when it isn't needed.  Fortunately, the image you tried to post is still on your local HDD, so we aren't forced to download it and pay to do that (some people pay for every byte downloaded).  Use text whenever possible (which should be ALWAYS if you are doing server work).  When posting terminal stuff here, you'll need to always post it, unmodified, then wrap the commands used AND the output in "forum code tags".  The advanced editor has a '#' button for that. It works just like quote, bold, italics, etc.  There are manual ways to do it too.  I often am not in the Advanced editor when replying here, so I'll use the "forum quote tags", then just change the "quote" --> "code" inside the added brackets.

Here's an example from a Linux Mind desktop for what I mean:
```
$ time sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
Ign:2 [http://packages.linuxmint.com](http://packages.linuxmint.com) victoria InRelease                         
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB]        
Hit:4 [http://packages.linuxmint.com](http://packages.linuxmint.com) victoria Release                           
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]      
Hit:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease               
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main i386 Packages [618 kB]
Hit:9 [https://ppa.launchpadcontent.net/x2go/stable/ubuntu](https://ppa.launchpadcontent.net/x2go/stable/ubuntu) jammy InRelease      
Get:10 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main amd64 Packages [1,608 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main amd64 Packages [1,388 kB]
Get:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/main Translation-en [303 kB]
Get:13 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 Packages [1,826 kB]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/restricted Translation-en [310 kB]
Get:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages [1,070 kB]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates/universe i386 Packages [699 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main i386 Packages [452 kB]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/main Translation-en [243 kB]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/restricted amd64 Packages [1,762 kB]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/restricted Translation-en [299 kB]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security/universe amd64 Packages [848 kB]
Fetched 11.7 MB in 4s (2,994 kB/s)                     
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

real    0m6.691s
user    0m0.003s
sys     0m0.011s
```
The 'time' command says it took less than 7 seconds to get the new repo package lists.
Now I'll do the "upgrade"
```
$ time sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  python3-pil python3-pil.imagetk
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 429 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu jammy-updates/universe amd64 python3-pil.imagetk amd64 9.0.1-1ubuntu0.3 [9,616 B]
Get:2 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 python3-pil amd64 9.0.1-1ubuntu0.3 [419 kB]
Fetched 429 kB in 0s (1,291 kB/s)
(Reading database ... 703173 files and directories currently installed.)
Preparing to unpack .../python3-pil.imagetk_9.0.1-1ubuntu0.3_amd64.deb ...
Unpacking python3-pil.imagetk:amd64 (9.0.1-1ubuntu0.3) over (9.0.1-1ubuntu0.2) ...
Preparing to unpack .../python3-pil_9.0.1-1ubuntu0.3_amd64.deb ...
[B]Unpacking python3-pil:amd64 (9.0.1-1ubuntu0.3) over (9.0.1-1ubuntu0.2) ...
[/B]Setting up python3-pil:amd64 (9.0.1-1ubuntu0.3) ...
Setting up python3-pil.imagetk:amd64 (9.0.1-1ubuntu0.3) ...

real    0m4.616s
user    0m0.004s
sys     0m0.004s
```
So, even though I had to press <enter> when it asked a question, the total time was less than 5 seconds.  My internet connection isn't exactly fast by standards today.  30 Mbps / 6 Mbps.  Pretty much anyone not on dialup or ISDN should be faster.

If a part of the command is taking a long time, the package could be corrupted, but that would be difficult, since all .deb files are crypto graphically signed. Corrupted files would create a different error, much earlier.   My first thought is that the storage for /var/lib/, which is where packages get placed, is full or there's a file system problem (very unusual on a fresh install.  You can check for 99% of space issues with:
**df -Th**
There will probably be a number of "fake" storage areas.  I use an alias with the **df **command so I never need to see the fake storage stuff.
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```
If you add that to the bottom of your user's. ~/.bashrc logout/login or just source the file (or use ~/.bash_aliases, up to you), then you'll be able to use **dft** to see just the good stuff.

If that isn't the issue, I'd look in the _system logs_ for other problems around that time.  Hardware problems happen to everyone.  I self-inflicted a hardware problem over the weekend that took far to long to realize it was trivial a cable inside the case was loose).  I'd been swapping a nearly dead HDD with a replacement one plus replacing a dead case fan, and inadvertently removed some front-panel connections. Most of the time, those front-panel connections aren't important.  This time, I was "lucky" ... and it was the Power LED and Power Switch connections.  Self-inflicted.  

You can google "ubuntu log files" for how to check logs.  I typically start with 
```
sudo egrep -i 'error|warn' /var/log/*log | less 
```

That should get you started.  Depending on the file system you selected at install time, there are other commands to check those for consistency.  I don't know what the defaults are, but I force an **fsck** on file systems if it has been over a month since the last time.  ext4 is pretty hard to force a inconsistency, but sometimes things go badly (usually due to multiple disk block issues) and there's only so much any file system can do to get around HW issues.

---

