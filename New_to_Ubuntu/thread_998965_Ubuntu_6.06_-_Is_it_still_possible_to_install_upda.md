---
title: "Ubuntu: 6.06 - Is it still possible to install updates?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by Jdmisra81 on 2008-12-01
Hello,

I hope this isn't a stupid question, I am new here and tried to find the answer but didn't have much luck.

I just installed Ubuntu 6.06 from a CD . I had used it in the past, then switched over to Mepis. Today I decided I would like to go back to Ubuntu. I figured I could start with the 6.06 and update/upgrade it .

But when I try to use the synaptic package manager or add/remove applications, nothing works !I can't update the file lists (I enabled all the repositories). It won't download the lists of available software.

Is it no longer possible to get updates for 6.06 ? And does that mean I can't use the update functions to upgrade to a more current version?

Thank you in advance!!

John

---

### Post by halitech on 2008-12-01
LTS support is 3 years for the desktop version and 5 years for the server version so you should still be able to get updates. The only version you can update to now would be 8.04 (another LTS version) as 6.10 and 7.04 are not supported anymore.

what happens when you try to update?

---

### Post by tjwoosta on 2008-12-01
your best bet would be to just burn a new 8.04 live cd and install that way, instead of dealing with all of the hastles and flaws of upgrading from 6.04

---

### Post by OrangeCrate on 2008-12-01
Upgrading from 6.06 LTS to 8.04 LTS

1) Make sure the upgrade channel is open. LTS to LTS, Software Sources > Updates

2) Press Alt-F2 and type:

gksu "update-manager"

3) Click the Check button to check for new updates.

(A message should appear informing you of the availability of the new release.)

4) Click Upgrade.

Follow the utility's instructions...

[B]Edit:

The official documentation is here:

[https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)[/B]

---

### Post by tgalati4 on 2008-12-01
Try burning a 6.06.2 disk, that should have the latest repositories.  Although Dapper is long in the tooth, it still works well.

Or check your repositories against my Dapper machine:

>cat /etc/apt/sources.list



deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe



# Gpsdrive Packages
# deb [http://www.ostertag.name/debian](http://www.ostertag.name/debian) etch main
# deb-src [http://www.ostertag.name/debian](http://www.ostertag.name/debian) etch main

# Grass / GIS (for Debian stable,ubuntu)

# Asher 256 repository
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

-------------------------------

You don't need them all, just the main dapper ones.

---

### Post by Jdmisra81 on 2008-12-01
I installed 6.06.2, but am having the same problem. If I try to refresh the synaptic package manager, I get the following

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preference

and

hive.ubuntu.com/ubuntu/dists/edgy/Release.gpg
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_CA.bz2)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_CA.bz2)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_CA.bz2)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_CA.bz2)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_CA.bz2)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_CA.bz2)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_CA.bz2)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_CA.bz2](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_CA.bz2)
etc...

Also, I tried a  sudo apt-get update
I get this
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

and it hangs up and nothing happens....could it be an internet connection problem ? But I have no problem using firefox, I'm stumped so far.



What am I doing wrong here?

Thanks again,

---

### Post by halitech on 2008-12-01
it looks like you are pointing at the edgy repos which are not listed the same as an active repo. can you post your output to```
cat /etc/apt/sources.list
``` so we can take a look at them?

---

### Post by Jdmisra81 on 2008-12-01
Is this what you mean? I entered what you gave me into the terminal window.

oem@jdmisra81:~$ cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy multiverse main universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by halitech on 2008-12-01
ummmmmm you aren't running 6.06, you are running 6.10 which is no longer supported. 7.04 I think is done as well so you are going to have to download a newer version (8.04 or 8.10) and do a clean install.

---

### Post by OrangeCrate on 2008-12-01
<deleted>

Just saw halitech's post ^. I concur with his advice.

Edit:

If you're interested, see post #12 for the content that had been here. It was grabbed before I could delete it.

---

### Post by Jdmisra81 on 2008-12-01
I was on 6.06 this morning, but someone suggested that using a 6.10 disc would work . I don't have enough RAM to run 8.04 or 8.10 it seems...
So basically, I'm out of luck? (Aside from upgrading my memory) - no way I can update Ubuntu in the meantime ? (What I really want is the various multimedia codecs and so on, and things like Mplayer and VLC), the rest can wait.

---

### Post by halitech on 2008-12-01
> **OrangeCrate said:**
> I'm currently using the HP in my signature. The CD/DVD drive won't write a new disk, so when I brought this box up-to-speed, I did a fresh install of 6.06 (which was on here, and the only disk I had), and then upgraded directly to 8.04 without applying any updates whatsoever.

It worked fine. Apparently the upgrade process took care of any repository issues. I didn't change anything from the fresh install prior to upgrading. If nothing else works, you might try that. The instructions for the upgrade are in my earlier post. Use the official documentation instructions I edited in at the bottom.

that would work IF he was running 6.06 but he's not, he's running 6.10 which does not allow upgrading directly to 8.04 and since support has stopped for 7.04, fresh install is his only option.

---

### Post by halitech on 2008-12-01
> **Jdmisra81 said:**
> I was on 6.06 this morning, but someone suggested that using a 6.10 disc would work . I don't have enough RAM to run 8.04 or 8.10 it seems...
So basically, I'm out of luck? (Aside from upgrading my memory) - no way I can update Ubuntu in the meantime ? (What I really want is the various multimedia codecs and so on, and things like Mplayer and VLC), the rest can wait.

ok, lets look at basics. How much memory do you have? what speed processor? what type of video card?

---

### Post by Jdmisra81 on 2008-12-01
I know I've got 192 MB of memory..Off the top of my head I can't recall the processor speed - how can I look that up?

I just recall reading that 192 MB is nowhere near enough to run 8.04.

I've got discs now for 6.06 and 6.10, I could do a fresh install of 6.06 if it was going to be helpful.

---

### Post by OrangeCrate on 2008-12-01
> **halitech said:**
> that would work IF he was running 6.06 but he's not, he's running 6.10 which does not allow upgrading directly to 8.04 and since support has stopped for 7.04, fresh install is his only option.

I was apparently editing my previous post at the same time you were posting this.

---

### Post by halitech on 2008-12-01
before we go about reinstalling anything lets see what we have. 192 meg of ram? definately won't run ubuntu/Kubuntu but you can run Xubuntu (albeit slowly). 

from a terminal, run```
lshw -C cpu
``` and ```
lshw -C video
```
this will give us some basic info. post the results

---

### Post by halitech on 2008-12-01
> **OrangeCrate said:**
> I was apparently editing my previous post at the same time you were posting this.

sometimes I run pretty fast on a thread, no offense meant by my post, we're all here to help people :)

---

### Post by OrangeCrate on 2008-12-01
> **halitech said:**
> sometimes I run pretty fast on a thread, no offense meant by my post, we're all here to help people :)

Agreed.

---

### Post by Twitch6000 on 2008-12-01
Humm if you have 192mb ram I think you can install Mandriva on alt install.

OR you could use DSL.

Another thing you could do if you want is try a minimal Ubuntu install.

---

### Post by tgalati4 on 2008-12-01
You could try Linux Mint 4 (Darnya) XFCE.  It tends to run on lighter machines and it's based on gutsy with most of the multimedia working out of the box.

The Dapper repositories are working, I just updated a few apps including libvorbis.

---

### Post by Jdmisra81 on 2008-12-02
> **halitech said:**
> before we go about reinstalling anything lets see what we have. 192 meg of ram? definately won't run ubuntu/Kubuntu but you can run Xubuntu (albeit slowly). 

from a terminal, run```
lshw -C cpu
``` and ```
lshw -C video
```
this will give us some basic info. post the results

Here goes:

oem@jdmisra81:~$ sudo lshw -C cpu
  *-cpu                   
       description: CPU
       product: AMD Duron(tm)
       vendor: Advanced Micro Devices [AMD]
       physical id: 4
       bus info: cpu@0
       version: 6.7.0
       slot: Socket-A
       size: 1GHz
       capacity: 1400MHz
       width: 32 bits
       clock: 100MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow up ts

and
oem@jdmisra81:~$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Radeon RV100 QY [Radeon 7000/VE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 128MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       resources: iomemory:d0000000-d7ffffff ioport:9800-98ff iomemory:dfef0000-dfefffff irq:11



P.s. I just wanted to say I appreciate the help from all of you guys.

---

### Post by halitech on 2008-12-02
looks like other then the ram you are good, Duron 1.0 and a 128meg ATI Radeon video card. I would say at this point you can go a few differnet ways.

Option 1. If you want to stay with Ubuntu, download the Xubuntu Alt install cd 8.04 and install that. It will be slightly sluggish with only 192meg of ram but will run.

Option 2. go for another distro like DSL or Puppy.

Option 3. If you have a wired net connection, download the net install cd from Debian and do a custom install using XFCE as the desktop environment. This will be very similar to Xubuntu but seems to run much faster.

Let us know what you want to do :)

---

### Post by Jdmisra81 on 2008-12-02
> **halitech said:**
> looks like other then the ram you are good, Duron 1.0 and a 128meg ATI Radeon video card. I would say at this point you can go a few differnet ways.

Option 1. If you want to stay with Ubuntu, download the Xubuntu Alt install cd 8.04 and install that. It will be slightly sluggish with only 192meg of ram but will run.

Option 2. go for another distro like DSL or Puppy.

Option 3. If you have a wired net connection, download the net install cd from Debian and do a custom install using XFCE as the desktop environment. This will be very similar to Xubuntu but seems to run much faster.

Let us know what you want to do :)
Option 3 sounds intriguing....if you wouldn't mind talking me through it, that is .

With the hardware I've got..if I increased the RAM , would I be able to run an up to date Ubuntu ? (8.04, or is it 8.10, I forget)

Again, I really appreciate the help, I am learning things on my own, but it is nice to have some experienced users to talk to as well.

Thanks guys!

---

### Post by w4ett on 2008-12-02
> **Jdmisra81 said:**
> With the hardware I've got..if I increased the RAM , would I be able to run an up to date Ubuntu ? (8.04, or is it 8.10, I forget)
 Considering the current price of Ram (cheap Cheap CHEAP) you can stick 2GB of Sdram or DDR ram in you MOBO for about $40 shipped  (I'd be glad to point you in the right direction for decent suppliers, if asked  :) [http://www.pricewatch.com/system_memory/pc133_1gb.htm](http://www.pricewatch.com/system_memory/pc133_1gb.htm) [http://www.pricewatch.com/system_memory/ddr_pc3200_1gb.htm)](http://www.pricewatch.com/system_memory/ddr_pc3200_1gb.htm)) That old Duron/Socket A Motherboard is fully capable of running the full install of either 8.04 or 8.10.  I still run a couple of socket a motherboards with Athlon XPs and they do well.

---

### Post by halitech on 2008-12-03
> **Jdmisra81 said:**
> Option 3 sounds intriguing....if you wouldn't mind talking me through it, that is .

With the hardware I've got..if I increased the RAM , would I be able to run an up to date Ubuntu ? (8.04, or is it 8.10, I forget)

Again, I really appreciate the help, I am learning things on my own, but it is nice to have some experienced users to talk to as well.

Thanks guys!

I've been installing that way myself on all my machines and with the instructions they have here: [http://forums.debian.net/viewtopic.php?t=26566](http://forums.debian.net/viewtopic.php?t=26566)
it is a breeze and walks you through everything. As w4ett pointed out, ram is cheap (for most kinds) and yeah, if you bump up to at least 512 then you should be able to run 8.04 or 8.10 (I'd probably go 8.04 myself). Ubuntu is based on Debian so everything you've learned with Ubuntu you can take to Debian.

other useful links:
speeding up Debian [http://forums.debian.net/viewtopic.php?t=14129](http://forums.debian.net/viewtopic.php?t=14129)
multimedia [http://forums.debian.net/viewtopic.php?t=6935](http://forums.debian.net/viewtopic.php?t=6935)


> **w4ett said:**
> Considering the current price of Ram (cheap Cheap CHEAP) you can stick 2GB of Sdram or DDR ram in you MOBO for about $40 shipped  (I'd be glad to point you in the right direction for decent suppliers, if asked  :) [http://www.pricewatch.com/system_memory/pc133_1gb.htm](http://www.pricewatch.com/system_memory/pc133_1gb.htm) [http://www.pricewatch.com/system_memory/ddr_pc3200_1gb.htm)](http://www.pricewatch.com/system_memory/ddr_pc3200_1gb.htm)) That old Duron/Socket A Motherboard is fully capable of running the full install of either 8.04 or 8.10.  I still run a couple of socket a motherboards with Athlon XPs and they do well.

depending on if he has PC100/133 ram then it might not be worth investing any money on ram as its pretty old now but judgement call on his part.

---

### Post by w4ett on 2008-12-03
+1 halitech on the 8.04 preference.....it runs really smoothly on my older equipment and the 3 years of support make it a no brainer.

True enough that adding extra ram to older equipment is definatly not an investment :), but it certainly will extend the life of that motherboard.

---

### Post by halitech on 2008-12-03
hopefully he has DDR ram which could be reused in another machine if he decides to upgrade just the board and cpu :)

---

### Post by Keen101 on 2008-12-03
well,  you could try to edit your repositories file (the one you posted earlier). Try changing every word that say's "edgy" to "hardy" then they refreshing and getting updates.. and upgrades..


> **Jdmisra81 said:**
> Is this what you mean? I entered what you gave me into the terminal window.

oem@jdmisra81:~$ cat /etc/apt/sources.list
# 


## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) [COLOR="Red"]hardy[/COLOR] universe
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) [COLOR="Red"]hardy[/COLOR] universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) [COLOR="Red"]hardy[/COLOR]-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) [COLOR="Red"]hardy[/COLOR]-backports main restricted universe multiverse


# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) [COLOR="Red"]hardy[/COLOR]-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) [COLOR="Red"]hardy[/COLOR] multiverse main universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) [COLOR="Red"]hardy[/COLOR]-security universe

Even if this suggestion works, i still think you will need a lot more ram to do anything useful. get some more memory.

---

### Post by tjwoosta on 2008-12-03
8.04 is awesome if you have 512 mb ram but what about those of us who only have 256mb ram 


i have been running ubuntu 7.10 up untill yesterday when i tried upgrading to ubuntu 8.04

8.04 is so, so much slower then 7.10 its not even funny

its so bad that xubuntu 8.04 (xfce) is far slower then ubuntu 7.10 (gnome)


the computer runs ubuntu 7.10 almost perfectly but with xubuntu 8.04 installed i cant even get as far as opening the menu because it is so laggy 

why is there such a difference between the requirements of the two releases?


it just really sucks because this computer is going to have to go from running nice ubuntu with gnome to running something small and ugly and less user friendly like puppy linux or something

---

### Post by halitech on 2008-12-03
why not try Debian with Gnome? alot of the slow down issues with Ubuntu are because of all the things they toss in to try and make it easier. Debian is basically the same but you do have to work a bit to get it working. I changed from Ubuntu 7.04 to Debian Etch on the same hardware and my system responds better and my boot time dropped by over half.

---

### Post by tjwoosta on 2008-12-04
awesome, ill give that a try thanks

---

### Post by Jdmisra81 on 2008-12-04
> **halitech said:**
> looks like other then the ram you are good, Duron 1.0 and a 128meg ATI Radeon video card. I would say at this point you can go a few differnet ways.

Option 1. If you want to stay with Ubuntu, download the Xubuntu Alt install cd 8.04 and install that. It will be slightly sluggish with only 192meg of ram but will run.

Option 2. go for another distro like DSL or Puppy.

Option 3. If you have a wired net connection, download the net install cd from Debian and do a custom install using XFCE as the desktop environment. This will be very similar to Xubuntu but seems to run much faster.

Let us know what you want to do :)
So finally I decided I would try Xubuntu 8.04, I downloaded and burned myself an Alternate Install disk...Installed it...works fine, a tad slow (as was said by some of you guys). But it works...I ordered some RAM which should get things up to speed.

The only thing now is I can't for the life of me get Flash plugin to work for Firefox! It's so frustrating, I thought it would get easier, not harder :p 
When I type into the address bar

about:plugins

it tells me it's there....but when I go to a site that requires it (ie. Youtube) I get the message teling me that I need to install flash....

Argh! 

:(

---

### Post by w4ett on 2008-12-04
Try this:
```

sudo apt-get install ubuntu-restricted-extras
```


ADDED:   This should be:

by halitech:

> actually, since he is running Xubuntu it would be
Code:```


sudo apt-get install xubuntu-restricted-extras
```

As per the post below.....I gotta get new Bifocals and less arthritic fingers :P

---

### Post by halitech on 2008-12-04
> **w4ett said:**
> Try this:
```

sudo apt-get install ubuntu-restricted-extras
```

actually, since he is running Xubuntu it would be
```
sudo apt-get install xubuntu-restricted-extras
```

---

### Post by w4ett on 2008-12-04
> **halitech said:**
> actually, since he is running Xubuntu it would be
```
sudo apt-get install xubuntu-restricted-extras
```

:(  Darn my old fingers...lol

---

### Post by halitech on 2008-12-04
no problem, I'm sure I'll get there some day ;)

---

### Post by Jdmisra81 on 2008-12-04
Well, the sudo apt-get install xubuntu-restricted-extras
mostly worked...I have java...I have fonts...
but
I don't have flash - this is what happened:

Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--22:46:08--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.7.50.70
Connecting to fpdownload.macromedia.com|96.7.50.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:46:08 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.


What can I try next?

---

### Post by Jdmisra81 on 2008-12-04
Oops, never mind! This worked

cd /tmp
wget [http://download.macromedia.com/pub/l..._070208.tar.gz](http://download.macromedia.com/pub/l..._070208.tar.gz) ([http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz))
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer

Success! Now all I need is for my RAM to get here.

Thanks guys!

---

### Post by w4ett on 2008-12-04
I'm glad you got it sorted out.  When you get your new ram installed you will surely notice a world of difference.

Good Luck

---

### Post by Jdmisra81 on 2008-12-04
I'm glad too, and I'm sure it will be great to have the improved performance..I'm just really enjoying this whole learning process...A bit frustrating at times, but I already know more than i did a few months ago..Or even yesterday! It's great that this forum exists! Thanks!

---

