---
title: "Ubuntu 12.04 drive partitioning?"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by manatarms on 2012-04-18
Hi, I'm trying to run Ubuntu 12.04 along side Windows, but I'm getting held up when trying to partition the disc.  

[attach]216245[/attach]

---

### Post by oldfred on 2012-04-18
Are you thinking of installing on sda or sdc. It looks like sdb is your flash drive.

With multiple drives it is often better to have systems on different drives.

If you have Windows 7 you should use it to shrink the Windows partition to make unallocated space for Ubuntu. But do not create partitions as it may convert to dynamic which does not work. You can create partitions in advance with gparted or as part of the installer as your screenshot shows. You seem to be in the Something Else or manual partitioning screen not one of the automatic choices. But with multiple drives it is often better to setup & choose you own partitions.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04- side by side auto install
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) 
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by manatarms on 2012-04-18
Thank you, Oldfred, for those help links. I was hoping to install on sda because I don't really have another available drive. I only have Xp (and no windows disc - so I just wanted to be careful not to mess anything up).  thnx again Oldfred

---

### Post by forrestcupp on 2012-04-18
It's probably too late, but if you only have one drive, why didn't you just choose the option to have the Ubuntu installer automatically install it side by side with Windows for you?

---

### Post by manatarms on 2012-04-18
I'm not sure, but I must have overlooked installing it side by side in the Ubuntu installer. I mounted Ubuntu 12.04 iso with Dameon tools, so I guess I'm running it as a live disc right now. When I restarted my system, and it booted from (virtual live disc??) an install icon was on my Ubuntu desktop. The only option it's giving me is to wipe WinXp or partition the drive.

---

### Post by forrestcupp on 2012-04-19
You can't install Ubuntu correctly with a virtual live disc. You need to either use a real LiveCD or LiveUSB so it can cleanly boot directly to the Live Ubuntu environment.

---

### Post by manatarms on 2012-04-19
You're right about that, Forrestcupp, because sometime yesterday evening, when I booted out of the virtual live disc....my Windows was completely gone. I had to install Ubuntu 9.04 because that was all I had. I'm now trying to figure out how to boot and install Ubuntu 12.04 from a flash drive - all doing it from 
Linux, now, rather than Windows.

---

### Post by forrestcupp on 2012-04-19
> **manatarms said:**
> You're right about that, Forrestcupp, because sometime yesterday evening, when I booted out of the virtual live disc....my Windows was completely gone. I had to install Ubuntu 9.04 because that was all I had. I'm now trying to figure out how to boot and install Ubuntu 12.04 from a flash drive - all doing it from 
Linux, now, rather than Windows.

On the download page at ubuntu.com, it explains how to create a LiveUSB from Ubuntu. Just keep in mind that 12.04 is still Beta2 until April 26th. It's pretty stable, though. 

Just don't accept any Partial Upgrades if it offers them to you at any time after you have installed it, or it will bork your system. The only reason I'm telling you that is because I was offered a Partial Upgrade today. If that happens, just wait a day or so, and you should be able to do the full update. Betas have a lot of updates. ;)

---

