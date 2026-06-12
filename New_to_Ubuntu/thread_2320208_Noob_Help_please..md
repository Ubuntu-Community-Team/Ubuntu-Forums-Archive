---
title: "Noob Help please."
date: 2016-04-11
forum: New to Ubuntu
---

### Post by hedg70 on 2016-04-11
Hello, as you can guess I am new to ubuntu, I have a few questions and hopefuly you guys can help me fix them.

Current Version 16.04 TLS

1. what is this I get when booting up from selecting Ubuntu from the grub selection.
[ATTACH=CONFIG]268309[/ATTACH]

2. How do I get ubuntu to load strait into user selection screen rather than having the option of choosing ubuntu and some other options from the grub menu?

3. I cannot install Xchat it gives me some errors, 
4. I cant load some default programs because they crash and then cannot send error reports.. (What am i doing wrong?)

5. I got loads more but could do with some friendly person to give me a noobs guide to ubuntu, i have looked around google on how to do stuff but half the time it wont work.

any ways that will do for now. hopefuly i can catch someone on irc chat rooms


thanks 

carl

---

### Post by grahammechanical on 2016-04-11
1) I see that as well. It is  a Linux system message reporting that the partition has been file error checked and there is nothing wrong with it. You are using a proprietary video driver. And for some reason when we use a proprietary video drive it blocks the loading of a Ubuntu splash screen that would normally hide a message like that. 

You may also see a message that says Welcome to Xenial Xerus and it comes with an offer to enter a username & password. That is Linux inviting Ubuntu to log in using your user name and password. This message does not stay so long on the screen. So, you may miss seeing it.

2) The boot menu (Grub - GRand Unified Bootloader) has a default delay of 10 seconds to allow us to choose an option. It is possible to reduce that delay to as low as 1 second (and all seconds in between) but with another OS on the machine that would not be advisable. If Ubuntu is the only OS on the machine then we would not be seeing a Grub boot menu at all.

3) We cannot help with the Xchat problem without being told what the errors are. Error messages are useful for diagnosing problems. 

It is unusual for default applications to crash even on a pre-release version of Ubuntu. And that is what 16.04 still is at least for the next couple of weeks. I have been running 16.04 (xenial xerus) since the first day of it 26 week development period and while I have not tested everyone of the default installed applications the only application that I have noticed as crashing as it loads is Ubuntu Web Browser. But then it was doing that all the way through the development version of Ubuntu 15.10 as well.

Again without specifics we cannot offer advice. We would also find the hardware specification useful in regard to some problems. For all we know you might be running Ubuntu on a machine that does not have the hardware capabilities to run Ubuntu.

A lot of people are finally making the switch from XP and they want to continue using the same machines. And why not? Those machines are still working. So, why not continue to used them? But with a secure OS. Which may be Ubuntu or another flavour of Ubuntu depending on the hardware specification.

Regards

---

### Post by him610 on 2016-04-11
Ref 1.  That same message appears on one of my machine with 16.04 also, but I just wait patiently for a couple of minutes. Mine does boot though. It is actually my preference to see the messages scrolling up the screen rather than be hidden behind a non-informative splash screen.

---

### Post by Geoffrey_Arndt on 2016-04-11
Also, regarding program crashes etc. , , , besides your hardware, a lot depends on "how" the program is installed.   From the official sources (aka repos or repositories), or from 3rd party PPA's (personal package archives) that may or may not achieve the same end result as installing the program thru the Synaptic Package Manager or whatever the new official package manager is called in 16.04.   Remember, . . . . . 95%+ of all software installs should come from the official repos . . . Linux users don't cruise to various web sites to download and install programs.

---

### Post by hedg70 on 2016-04-12
Ok, thank you for your reply's so far, when I get a few min's I'll try and upload some info / screen shot's,

Thank you so far for even replying to my message.

Carl

---

### Post by buzzingrobot on 2016-04-12
The disk checking program producing the "clean..." message is roughly analogous to Window's chkdsk. It's intended to run.  Nothing to worry about.

I'll reiterate the advice to avoid installing software from hither and yon.   Your Ubuntu system includes a list of official servers -- repositories -- that contain vetted, supported Ubuntu software. Your system will track all software installed from those repositories, and it will track that software if it is deleted.  Your system includes tools that use and rely on that capability.  In 16.04, the "Software" tool is used for that by default.  Command line tools exist to install and remove software, as well. 

If you use this system, system updates should be routine: Versions of software packages installed on your system are compared with versions on the repositories.  Newer ones are the updates, and they are downloaded and installed.

Installing software from "foreign" source, such as a vendor or a develop site, is not recommended. The software management tools on your system will, in many cases, not be aware of it.  Any other software packages required to allow to execute correctly will not be automatically downloaded and installed.  Nor will it be included in system updates. Instead, you get to worry about all this yourself.  And, of course, you also get to pick up the pieces if things break.

As mentioned, 16.04 is a few weeks from release yet.  It's been a very smooth development cycle, but you never know.  Stuff happens.  You will likely see a large number of updates until the release.  I'd recommend checking daily for those.

The components of 16.04 are not entirely "bleeding edge" but they are, in many cases, very new.   Try to avoid the "must install newest software releases" syndrome. 

The internet is full of advice and how-to's about Linux and Ubuntu.  Some of it is good.  Much of it is bad. Have a look around, but come back here and post questions rather than try something blindly that Google turned up.

---

### Post by hedg70 on 2016-04-12
Hi thanks for the great advice all, I'm taking it all on board.

1. When clicking on Check for updates *for system* I get

"Failed to load the package list
E:Malformed entry 54 in list file /etc/apt/sources.list (URI parse), E:The list of sources could not be read."

This is a list of my PPA's?

[ATTACH=CONFIG]268340[/ATTACH]


2. When I boot up steam client *for games* I get a box saying.

[ATTACH=CONFIG]268341[/ATTACH]

I understand that It's not updating, I have no idea why or how to fix this problem, If you can help again this is going to help me alot!


I also installed Steam on my system but its installed on the system's main drive (let's say C drive)

I have installed the games on another drive thats dedicated to game's (let's say D drive) *for space and speed reasons*
When I load Steam I encounter this

[ATTACH=CONFIG]268342[/ATTACH]

 It cannot find the location of the steam install because its on D drive and not on C drive where it thinks it is, I have to mount the other drive's by manual clicking to access them, This is all good but when I'm away and my little boy wishes to access  the game's they are not tech savy, So I need to set these drives to auto mount "Immediately" on start up! I assume this is possible with Ubuntu right?



3.  I have downloaded Teamspeak 3 from their official website, I installed it with help from a guide I found on the interwebz, It installed it via Terminal and it works, No problems there, Where the problem lies is where I try to run the program I have to launch it via Terminal, I followed a guide on how to make a desktop launcher icon thingy, but it doesn't work, It just loads up a gedit, I have set it to run as a program too!, Any ideas on what I have fluffed up?



4. When sending error report's It always fails and says

E:Malformed entry 54 in list file /etc/apt/sources.list (URI parse), E:The list of sources could not be read.



Thank's again for the help

Carl

---

### Post by yancek on 2016-04-12
> I also installed Steam on my system but its installed on the system's main drive (let's say C drive)

No, let's not.  Call it what it is.  Drive/partition naming conventions are different on Linux and you need to familiarize yourself with them so people understand what you are tallking about.  Very basically, the first physical hard drive is sda, the second physical hard drive is sdb.  Any number after sda, sdb, etc. tells which partition it is referring to on that drive.

With regard to the error you are reporting, /etc/apt/sources.list is a simple text file which is read when updating.  Post it here and someone should be able to point out any problems.  Just open it with a text editor (gedit?) and copy and paste the contents here.

> 
I have installed the games on another drive thats dedicated to game's (let's say D drive) *for space and speed reasons*

When you use the term 'drive' do you simply mean another partition on the same hard drive or are you referring to another actual physical hard drive.  If you can access the game/Steam manually, you should be able to mount the non-system partition on boot by putting an entry in the /etc/fstab file.

---

### Post by hedg70 on 2016-04-12
Hi, Yancek 

I have installed the game's on another drive SDB I think it is. But my main system is on SDA, I also have SDC, These are separate physical hard drives.

As for the sources.list

---------------------------------------------------------------------------------------------


```
# deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Beta amd64 (20160408)]/ xenial main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
deb Source = deb [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
deb-src Source = deb [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
```



-----------------------------------------------------------------------------------------------------------------

Also forgot to add my system spec's 

AMD 9590
Nvidia 660 GTX
12 GB Ram
1x Hyper X SSD 120gb (SDA) *System*
1x OC Agility 4 512gb (SDB) *Games*
1x Seagate 2tb (SBC) *Storage*


Hope that helps.

Carl



Edit .

Not sure if the SD* are correct as I am not sure how to check.   *I assume SD stands for Storage Device right?*

---

### Post by Geoffrey_Arndt on 2016-04-12
Just a few quick notes based on your last couple posts:

>  sda1 = first partition on scsi drive 1
>  You are running the "beta" version of 16.04 LTS? . . . and . . . . you also have Precise Pangolin sources (Ubuntu 12.04).    Never a good sign when sources (repos) are from more than one version of Ubuntu (really can't mix & match those sources & have a stable system (not even taking into account that Xenial is not at final release  - - it does have bugs and issues that will be fixed within the next 2 to 12 weeks or so.

---

### Post by mastablasta on 2016-04-13
this line is wrong in sources list:
```
deb Source = deb [http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/) precise steam
```

delete it or comment it (put # in front of it). then retry.

---

### Post by X-RED_Tech on 2016-04-13
For the non-gamers here: The Steam PPA is "precise", it has always been and there are no plans to change/update that for the near future. It's the same repo for any Ubuntu (or derivatives) 12.04 or newer.

The error message in the tiny dialogue windows start appearing in Ubuntu 16.04 only. It means nothing, ignore it: Just select that window if not in focus already and press Enter. Your Steam client and games are being updated like they always have been.
Also important is the fact that although you can install Steam data in a different path than the default (/home/your_user/.steam) you must have that location available when you start the Steam client. You should make sure it's mounted on boot (suggestions above) and a secondary drive never is by default or at least make sure you mount it (click on it should be enough) **before **starting Steam.

Last but not least make sure you have nvidia proprietary drivers for optimal performance. This is optional most of the times for many uses; NOT optional for Steam.

---

### Post by hedg70 on 2016-04-13
Thanks for the info X-RED_Tech,

I will continue with steam as is, its not too much of a drama, I can live with it.

As for mounting the drives, is there no other way for the system to auto mount them as soon as it logs in?

The drivers I am using are the latest Nvidia ones selected via the software update icon.


Thanks again all

Carl

---

### Post by yancek on 2016-04-13
> As for mounting the drives, is there no other way for the system to auto mount them as soon as it logs in?

Yes, as I mentioned in my earlier post, if you want another partition mounted on boot you will need an entry in the /etc/fstab file which you can open in a text editor as root.

sudo gedit /etc/fstab should open it.  An example entry below to mount a partition with a Linux filesystem on another drive.  You would need to replace "/dev/sdb2" with whichever partition you want mounted or you can use it's UUID instead such as in the second example below. The ext4 of course is the filesystem type and the rest is options.  You can get a lot of details on different options in fstab by doing an online search to get what you want.  You can also mount multiple partitions with separate entries.  In the example below, you would first need to create the 'data' directory in the /mnt directory.

> /dev/sdb2 /mnt/data ext4 auto,user,rw 1 2

> UUID=2ae95530-a3d7-43e7-a160-3ef4da2a5904 /mnt/data ext4 auto,user,rw 1 2

---

### Post by hedg70 on 2016-04-14
yancek I followed your instuctions and added a line to the fstab file, It did not go well I have just reinstalled 16.04 because I could not get it to load up, It kept going in emergency mode.

How do I install Teamspeek 3 and steam via the NEW "software" app in 16.04?

thanks 
carl

Edit -

Managed to install steam, The only way I see to install Teamspeak 3, OBS Studio, and other programs is by terminal, I cannot locate them on the "Software" App.

---

