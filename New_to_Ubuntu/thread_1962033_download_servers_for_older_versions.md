---
title: "download servers for older versions ?"
date: 2012-04-20
forum: New to Ubuntu
---

### Post by VMwareUser1 on 2012-04-20
Hi Ubuntu fans !  I've been using a prepackaged 'browser appliance' virtual machine (BAVM for short) by VMware, inc., that is based on an admittedly oldie - but goodie - Ubuntu version 5.10 'Breezy Badger', uname -r : 2.6.12-9-686.    Considering the intended use of the VM it absolutely doesn't matter to me that the Ubuntu system and the Firefox browser inside can be considered obsolete.  After a disk crash I had to fetch a fresh copy of the BAVM. I want to redo some customisation, which include downloading and installing national keyboard support packages.  Problem : the Synaptics update server which was built-in to that Ubuntu system does not answer (or even exist) any more :-(  Please tell, what is an working IP or URL for downloading the needed packets thru synaptics ?  Thank you very much in advance.  As should be evident from the above problem description, 'upgrading' the kernel and/or wholly updating the 'buntu is absolutely out of the question. National xxx keyboard support and only it is what is needed here (in addition I /do/ run somewhat more modern ubuntus out of CDs, and also Linux - several flavours- out of my main hard disk. No need to be convinced!)  --  VMwareUser1

---

### Post by Paqman on 2012-04-20
> **VMwareUser1 said:**
>   Problem : the Synaptics update server which was built-in to that Ubuntu system does not answer (or even exist) any more :-(  Please tell, what is an working IP or URL for downloading the needed packets thru synaptics ?


There isn't one. That version is no longer supported, and when support ends the repositories are closed.

If all you want is a VM appliance that you can use to run a browser I'd suggest getting the [Turnkey Core applicance]("http://www.turnkeylinux.org/core") from Trunkey Linux and installing a browser, xorg and ubuntu-desktop into it. This will give you a stable, supported VM based on Ubuntu 10.04. I wouldn't browse the web with an Ubuntu 5.10 machine, as it would not be receiving security updates.

---

### Post by Cheesemill on 2012-04-20
Check out my post in a recent thread here:
[http://ubuntuforums.org/showthread.php?t=1961368#3](http://ubuntuforums.org/showthread.php?t=1961368#3)

Obviously in your case replace intrepid with breezy.

---

### Post by Cheesemill on 2012-04-20
> **Paqman said:**
> There isn't one. That version is no longer supported, and when support ends the repositories are closed.

Actually the repositories aren't closed, they are moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

---

### Post by Paqman on 2012-04-20
Well, they may still be lurking in a dark corner of the internet, but they aren't active. I'd still *strongly* recommend against surfing the web on anything that hadn't seen a security patch in five years.

---

### Post by VMwareUser1 on 2012-04-20
> **Cheesemill said:**
> Check out my post in a recent thread   Obviously in your case replace intrepid with breezy.

Wow, this is exactly what I have asked for. I'll apply your solution and let you all know how it worked.  Thank you  --  VU1

---

### Post by VMwareUser1 on 2012-04-20
> **Paqman said:**
>  If all you want is a VM appliance that you can use to run a browser I'd suggest getting the [Turnkey Core appliance]("http://www.turnkeylinux.org/core") from Trunkey Linux and installing a browser, xorg and ubuntu-desktop into it. This will give you a stable, supported VM based on Ubuntu 10.04. I wouldn't browse the web with an Ubuntu 5.10 machine, as it would not be receiving security updates.

 Not that I don't want a more up to date kernel, but I really want my Firefox version 1 in that VM ! Actually I can't stand any Firefox version after 1.5 [ best ever being Firebird 0.8. ] As for security, no problems since the virtual machine's contents are lost after browsing. On the next session, not only browser data but also the operation system will be reverted to their pristine state. Not that I go to any scary places, either...  Hence I'm going for Cheesemill's solution.  Thanks though.

---

### Post by Paqman on 2012-04-20
> **VMwareUser1 said:**
> Not that I don't want a more up to date kernel, but I really want my Firefox version 1 in that VM ! 

Sounds like overkill to use an outdated OS just because you want a certain version of the browser. Why not use an up-to-date OS and install the old browser in it?

---

### Post by VMwareUser1 on 2012-04-20
> **Paqman said:**
> Sounds like overkill to use an outdated OS just because you want a certain version of the browser. Why not use an up-to-date OS and install the old browser in it?

 Just because there's a ready-made, light weight VM which I'm used to, having used it for years; which I do'nt have to install or customise (safe for these @@@ missing keyboard translation packs).  The way /you/ are suggesting, /that/ would be overkill IMvhO.

---

### Post by mastablasta on 2012-04-20
> **VMwareUser1 said:**
>  Actually I can't stand any Firefox version after 1.5 [ best ever being Firebird 0.8. ] 

ah bu then you miss out on all the features and also support for latest web pages. bu ti guess if it makes you happy....

personally i would use another browser such as Chrome or Midori if you are into light stuff....

---

### Post by VMwareUser1 on 2012-04-20
> **Cheesemill said:**
> Actually the repositories aren't closed, they are moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) 
  Hmmm, I entered the following text as 'sources.list', when I try to connect to the package manager though nothing happens after entering the password ! No GUI windows, nothing. Tried with and without a 'slash' as path ending character. Is there something wrong here, or is the server just non responding, in your opinion please ? _______________________________________________________    #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386  20051012)]/ breezy main restricted  ##1 modified  20 Avril 2012 cf ubuntuforu;s.org threqd.1961368  deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) breezy main restricted universe multiverse  deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) breezy main restricted universe multiverse [/code] ## Uncomment the following two lines to fetch major bug fix updates produced ## after the final release of the distribution.  deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse  deb-src [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) breezy-updates main restricted universe multiverse ________________________________________________________________

---

### Post by Cheesemill on 2012-04-20
Can you post your sources.list file in [noparse]```
 
```[/noparse] tags so I can see what it says please (just highlight the text in your reply and click on the # button).

Also run the following from a terminal to get a more verbose output:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by VMwareUser1 on 2012-04-20
Sorry about the mess, I did try and fail formatting. Let's try again

```
vmware@vmware-bavm:/etc/apt$ cat sources.list
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

##1 modifie' S.R. 20 Avril 2012m cf ubuntuforu;s.org threqd.1961368
 deb http://old-releases.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
 deb-src http://old-releases.ubuntu.com/ubuntu/ breezy main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://old-releases.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
 deb-src http://old-releases.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
vmware@vmware-bavm:/etc/apt$
vmware@vmware-bavm:/etc/apt$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/main Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/main Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/universe Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list http://old-releases.ubuntu.com breezy-updates/multiverse Packages (/var/lib/apt/lists/old-releases.ubuntu.com_ubuntu_dists_breezy-updates_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
vmware@vmware-bavm:/etc/apt$

```

---

### Post by VMwareUser1 on 2012-04-20
> **Cheesemill said:**
> 
```
sudo apt-get update
sudo apt-get upgrade
```

Ah, this one  hax worked !

```
Get:1 http://old-releases.ubuntu.com breezy Release.gpg [189B]
Get:2 http://old-releases.ubuntu.com breezy-updates Release.gpg [191B]
Get:3 http://old-releases.ubuntu.com breezy Release [30.9kB]
Get:4 http://old-releases.ubuntu.com breezy-updates Release [29.6kB]
Get:5 http://old-releases.ubuntu.com breezy/main Packages [585kB]
Get:6 http://old-releases.ubuntu.com breezy/restricted Packages [5061B]
Get:7 http://old-releases.ubuntu.com breezy/universe Packages [2304kB]
Get:8 http://old-releases.ubuntu.com breezy/multiverse Packages [91.6kB]
Get:9 http://old-releases.ubuntu.com breezy/main Sources [232kB]
Get:10 http://old-releases.ubuntu.com breezy/restricted Sources [1454B]
Get:11 http://old-releases.ubuntu.com breezy/universe Sources [915kB]
Get:12 http://old-releases.ubuntu.com breezy/multiverse Sources [46.9kB]
Get:13 http://old-releases.ubuntu.com breezy-updates/main Packages [59.5kB]
Get:14 http://old-releases.ubuntu.com breezy-updates/restricted Packages [14B]
Get:15 http://old-releases.ubuntu.com breezy-updates/universe Packages [16.8kB]
Get:16 http://old-releases.ubuntu.com breezy-updates/multiverse Packages [872B]
Get:17 http://old-releases.ubuntu.com breezy-updates/main Sources [18.8kB]
Get:18 http://old-releases.ubuntu.com breezy-updates/restricted Sources [14B]
Get:19 http://old-releases.ubuntu.com breezy-updates/universe Sources [1343B]
Get:20 http://old-releases.ubuntu.com breezy-updates/multiverse Sources [365B]
Fetched 4340kB in 44s (97.4kB/s)
Reading package lists... Done


```

Yet, the GUI package manager doesn't want to appear anymore. What do I do next ?

From my old notes, I wished it installed the following packages :

\* language-support-fr
\* language-pack-fr
\* language-pack-fr-base
\* language-pack-gnome-fr
\* language-pack-gnome-fr-base

---

### Post by snowpine on 2012-04-20
You should run:

```
sudo apt-get update
sudo apt-get upgrade
```

Of course the "upgrades" you receive will be several years out of date, as you know.

---

### Post by Cheesemill on 2012-04-20
> **VMwareUser1 said:**
> From my old notes, I wished it installed the following packages :

\* language-support-fr
\* language-pack-fr
\* language-pack-fr-base
\* language-pack-gnome-fr
\* language-pack-gnome-fr-base

```
sudo apt-get install language-support-fr language-pack-fr language-pack-fr-base language-pack-gnome-fr language-pack-gnome-fr-base
```

---

### Post by VMwareUser1 on 2012-04-20
```
vmware@vmware-bavm:/etc/apt$ sudo apt-get install language-support-fr language-pack-fr language-pack-fr-base language-pack-gnome-fr language-pack-gnome-fr-base
Password:
sudo: Can't open /var/run/sudo/vmware/0: Read-only file system
vmware@vmware-bavm:/etc/apt$


```

Oooopsie !

---

### Post by jerome1232 on 2012-04-20
> **VMwareUser1 said:**
> ```
vmware@vmware-bavm:/etc/apt$ sudo apt-get install language-support-fr language-pack-fr language-pack-fr-base language-pack-gnome-fr language-pack-gnome-fr-base
Password:
sudo: Can't open /var/run/sudo/vmware/0: Read-only file system
vmware@vmware-bavm:/etc/apt$


```

Oooopsie !

You need to close all other package manger programs (such as synaptic) to run apt-get

---

### Post by VMwareUser1 on 2012-04-20
[COLOR=Blue]Update AKA Happy End (FYI) : A family member was able to find an archived copy of the pristine, customised VM I gave them 6 years ago ! They sent it to me - using GBridge, great free though not open source VPN-like app by the way - 
Original question not really solved, but AFAIAC : All's well that ends well... :p
[/COLOR]
> **jerome1232 said:**
> You need to close all other package manger programs (such as synaptic) to run apt-get

Hiya! Yes, I grasped as much. The file system was corrupted after my earlier failed attempts anyway, so I deleted all and started afresh : such are the benefits of a virtual appliance.

I did (sudo) apt-get update, no upgrade, then apt-get install those language packs.

It looked like it had worked, except... I was unable to switch languages afterwards, and upon rebooting (like a vulgar Windoze) VMware warned the file system was corrupted again.

I think something is out of order, either the update server, or me, or both  ;)

Anyway I quit trying. I'll keep the foreign keyboard as pre-installed. 

I wish to thank you all who tried to help, including those who warned me /against/ my foolish attempts !

---

