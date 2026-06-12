---
title: "Dual boot Questions"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by Greywolft on 2011-11-01
[FONT="Georgia"][SIZE="3"][COLOR="Purple"][I]Hiya all,

I've been playing with the idea of trying my hand at ubuntu again. My first and last attempt to date was about as far from successful as one can get without it being an utter failure.

This time around I'm thinking of running a dualboot system to avoid many of the hassles and frustrations that hobbled me before.

I have 2 drives. One is an internal 300gb(where windows and it's recovery are) the other is a TB external. Can I install and run ubuntu on the TB external? If I can, is it possible to run ubuntu on whatever computer the drive is attached to(like running it off the CD kind of deal.)

I use Kaspersky Pure and have read that they only have antivirus for linux. Is there an all in one bundle(network, AV, MAlware, anti phishing, etc) for ubuntu?

I also just bought a Gforce 9800 Gt vid card, with more settings than I know what to do with, does linux have it's own set of drivers to support using an HDTV as the monitor?

I've got tons more but that should give a good idea of where I'm at in the planning so any site/guide/forum you care to direct me to would be most helpful and appreciated.

When dealing with the average PC user I consider myself fairly literate and helpful but once I start reading about linux, I'm a complete and utter novice. Might be why I waited 3 years to try again, here's to hoping this time goes much better with planning and preparation.

Thanks in advance for your time,

T[/I][/COLOR][/SIZE][/FONT]

---

### Post by wolfen69 on 2011-11-01
> **Greywolft said:**
> 

I have 2 drives. One is an internal 300gb(where windows and it's recovery are) the other is a TB external. Can I install and run ubuntu on the TB external? If I can, is it possible to run ubuntu on whatever computer the drive is attached to(like running it off the CD kind of deal.)
I would just unplug the windows drive before the install and put ubuntu on the external. And yes, you can use the external to use on any computer.

> I use Kaspersky Pure and have read that they only have antivirus for linux. Is there an all in one bundle(network, AV, MAlware, anti phishing, etc) for ubuntu?
Anti-virus generally isn't needed for a linux install. The only people that might want to consider it are those that download a lot of stuff to share with windows users.
> I also just bought a Gforce 9800 Gt vid card, with more settings than I know what to do with, does linux have it's own set of drivers to support using an HDTV as the monitor?
After install, you will be able to install the official nvidia drivers.

> I've got tons more but that should give a good idea of where I'm at in the planning so any site/guide/forum you care to direct me to would be most helpful and appreciated.
[www.ubuntuguide.org](www.ubuntuguide.org) is one of many helpful sites. Googling will yield many more.

---

### Post by oldfred on 2011-11-01
Unplugging the Windows drive is the absolute safest way. But you can install manually, but have to select where to install the grub2 boot loader. Grub normally installs to sda which is usually the internal drive, you will want it in the external.

If you install the nVidia proprietary driver to improve video performance, you may have issues booting any other system with different video. But there are some work arounds as with just about anything Linux.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

If dual booting with Windows you should also create a shared NTFS partition. Do not directly write (read is ok) into the Windows system partition on a regular basis. Windows seems to have issues with foreign systems writing into its system partition. A shared NTFS partition then works best.

---

### Post by Greywolft on 2011-11-01
[I][COLOR="Purple"]Awesome, thanks. I did google, which is what prompted my post. While there is ton's of info to be found, knowing what's valid and useful is the challenge.

I use my rig to store movies and music that I can pull up on my xbox 360, is this possible with Ubuntu? 

Thanks for the quick reply!
T[/COLOR][/I]

---

### Post by oldfred on 2011-11-01
It is my understanding Xbox only reads FAT partitions.

Large FAT partitions are not recommended as the maximum file size is 4GB and it does not have a journal so file repair/recovery can take forever on a large partition. FAT is ok for small devices like flash cards.

---

### Post by wolfen69 on 2011-11-01
> **Greywolft said:**
> [I][COLOR="Purple"]
I use my rig to store movies and music that I can pull up on my xbox 360, is this possible with Ubuntu? 
[/COLOR][/I]

If you mean is it possible for ubuntu to see the files that are stored in windows, yes. Just open your file manager and click the windows drive and navigate to them.

---

### Post by Greywolft on 2011-11-01
*[COLOR="Purple"]Sorry, my bad. Is it possible for The Xbox 360 to see those same files it sees using Tversity Media Server in Win XP? Guess more to the point is there a version of ubuntu that's geared toward being a Media center? I found some good articles, one in particular says to use "Ubuntu Linux 9.04 Desktop Edition 32-bit" so just wondering since I'd like to use ubuntu as much as possible and only dip into my XP for games and such that HAVE to have it[/COLOR]*.

---

