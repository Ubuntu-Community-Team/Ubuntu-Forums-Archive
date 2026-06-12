---
title: "Updating to 8.04.4"
date: 2008-07-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Sef on 2008-07-05
1) Hardy Heron Users: If your upgrades are current, then you are running 8.04.3.  If they are not current, then just install all the upgrades.

2) Dapper Drake Users: Automatic Upgrade through the Upgrade Manager.

3) Gutsy Gibbon Users: Upgrade through the Upgrade Manager or [install Hardy Heron]("http://www.ubuntu.com/getubuntu/download") by downloading 8.04.04, burning the iso and installing it.

4) Users of other versions of Ubuntu: Upgrade by [installing Hardy Heron]("http://www.ubuntu.com/getubuntu/download") by downloading 8.04.04, burning the iso and installing it.

5) For more information, read [Ubuntu 8.04.1 LTS released]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html").

6) **Back up** your **data** before upgrading, there are no 100% guarantees that all will go well.

---

### Post by jwaiwit on 2008-07-05
Now i currently run on 8.04 with latest update. 
Got 8.04.1 from /cat/issue , So do i need fresh install from 8.04.1 or not ? (I much concern about performance and stability.)

Thanks

---

### Post by buntunub on 2008-07-05
Type in Terminal

```
lsb_release -a
```

Should show your on 8.04.1 if you've done all updates in Hardy.

---

### Post by confused57 on 2008-07-05
> **jwaiwit said:**
> Now i currently run on 8.04 with latest update. 
Got 8.04.1 from /cat/issue , So do i need fresh install from 8.04.1 or not ? (I much concern about performance and stability.)

Thanks
No, you're up-to-date with 8.04.1.  I installed 8.04 a couple of days ago and had approx. 200 updates to install...just yesterday, I installed 8.04.1 and had no updates that needed installing(used the alternate 8.04.1 install cd).

I've personally had trouble booting the 8.04.1 live cd on 2 different computers, a 2.93 GHz celeron(Intel mobo) and a 3.06 GHz celeron(Abit mobo, sis chipsets)...receiving Buffer I/O errors on sr0, as well as numerous squash_fs errors.  The 8.04 live cd boots with no problem on both computers.

Update:  The Hardy Desktop 8.04.1 x86 cd booted normally on a GA-EP35-DS3L, Allendale E2200 processor.  All 3 pc's have an IDE Lite-On DVD +-RW drive.  I was able to get the cd to boot on the 3.06 GHz by entering all_generic_ide boot parameter, however the desktop was slow & unusable...required approx 15 minutes to boot the cd, couldn't open a terminal, Ctrl+Alt+F1 showed "squash_fs sd_bread" errors scrolling down the page.

Sorry if this isn't intended as a general support thread, but I just wanted to relate my experiences and was wondering if anyone else has encountered the same.  It's not a major problem, since I was able to successfully install with the alternate 8.04.1 cd.

Last & Final Update:  Redownloaded the Desktop 8.04.1 iso in Windows XP on the 2.93 GHz, burned using Nero...works well on all my computers.  The original Desktop 8.04.1 iso was downloaded & burned in Hardy on the Gigabyte pc, which may be why it only worked on it & not the older pc's?  The 8.04.1 alternate iso was also downloaded & burned on the Gigabyte pc, but worked on all of my pc's.

It appears to be a DVD writer/hardware incompatiblity with cd images written on the Gigabyte pc.  Downloaded & burned PCLinuxOS_2007 on the Giga machine, would only boot on the Gigabyte pc.  Please ignore the above rantings, I'll delete if the mods deem necessary.

---

### Post by jwaiwit on 2008-07-05
Hmm. Ok So I no need to re-install again. Thanks for all suggest.
Actually I waiting for new features coming after installation.:)

---

### Post by jenelle on 2008-07-05
i'm still on 7.10 one .
my brother gave me the computer all set up with ubuntu on it and finally i got connected to the net now i have done the up grades of what they send me but not the 8.04 as was not sure if i was meant to or not would the upgraded stuff i did up grade be 7.10 or 8.04 ? all new to me any help will be appreciated  
when i went to up grade it once i found what it was said it would take 2 hrs 20 to down load plus more for the rest so i did not continue cause i wanted to find out more info before i did it

---

### Post by ivra on 2008-07-05
Hi jwaiwit,

it's not nessesery to make clean install to 8.04.1 if you have 8.04. 8.04.1 fix bugs from 8.04. Only is nessery to updates.

---

### Post by jwaiwit on 2008-07-05
> **jenelle said:**
> i'm still on 7.10 one .
my brother gave me the computer all set up with ubuntu on it and finally i got connected to the net now i have done the up grades of what they send me but not the 8.04 as was not sure if i was meant to or not would the upgraded stuff i did up grade be 7.10 or 8.04 ? all new to me any help will be appreciated  
when i went to up grade it once i found what it was said it would take 2 hrs 20 to down load plus more for the rest so i did not continue cause i wanted to find out more info before i did it

Hi jenelle,
  **for my opinion** , If u not familiar with linux much ,you should continue using 7.10. No-need to upgrade coz I found a lot of trouble with 8.04. such as wi-fi connection then it have to config more before it 's work. I saw many user still continue using 7.10 for some reason. 

Thanks for ivra too.

---

### Post by misterbk on 2008-07-05
This may be silly and I don't know if it's related to 8.04.1 or always been like that, but it caused me hesitation during install:

Time zone selection:
Nothing close to my city is in that graphical "click a time zone" map.  (I would be in San Francisco.)  I notice there are dozens of cities all in the same spot in the Midwest but the West coast is barren.  I wouldn't care, but the list of time zones is also by city.  Ask me my time zone and I can easily reply "oh it's GMT - 8:00" and every other time zone picker works this way.  But in Ubuntu, I have to find another city that I know to be in the same time zone as myself, which is kinda backwards, and the time zone isn't listed in the pull-down at all.

Also, this install of Ubuntu is the first time I've ever seen a time zone picker declare "GMT - 7:00" for Pacific time.  Maybe I'm really wrong about this, but I thought my time zone stays "GMT-8:00" even if Daylight Savings is in effect?  (As if Daylight Savings is something that happens "on top" of my time zone, i.e. "GMT - 8:00 + DST", not something that redefines my time zone as GMT - 7:00 during some times of the year.

Another thing - I'm sort of disappointed that the partition tool still doesn't let you choose partition flags.  I can add them to fstab, but the text-mode partition tool let me set noexec and nosuid flags.  (despite its other failings of being too hard to use for many people.)

I'm trying the KDE4 remix package.

---

### Post by bcschmerker on 2008-07-05
Glad to see most prior posts this Thread show success, not so mine, unfortunately.  My Everex gPC has run consistently for the most part with gOS, which is built around the Ubuntu 7.10 core; Update Manager attempted to install 8.04 LTS, unsuccessfully.  What do I need to look for w/r/t failures to install of requisite packages for 8.04?

---

### Post by Sef on 2008-07-05
> Glad to see most prior posts this Thread show success, not so mine, unfortunately. My Everex gPC has run consistently for the most part with gOS, which is built around the Ubuntu 7.10 core; Update Manager attempted to install 8.04 LTS, unsuccessfully. What do I need to look for w/r/t failures to install of requisite packages for 8.04?

Did you try to install Ubuntu 8.04 from gOS?

---

### Post by Franc88 on 2008-07-06
> **jwaiwit said:**
> Hi jenelle,
  **for my opinion** , If u not familiar with linux much ,you should continue using 7.10. No-need to upgrade coz I found a lot of trouble with 8.04. such as wi-fi connection then it have to config more before it 's work. I saw many user still continue using 7.10 for some reason. 

Thanks for ivra too.

That's my problem now with 8.04.1, my freaking wireless is not working.  Got it to work for 8.04 but now its dead.  The hardware driver is installed and enable but status is "not in use".  I've tried re-installing the driver and booting a version prior to the update but no go.  This latest update is a cluster ****.  I should have known to wait before being one of the guinea pigs of this latest update.

I should have learned my lesson with Windows but I really thought that ubuntu would be different.

---

### Post by bcschmerker on 2008-07-08
2 Days Ago 08:39 PM, de Sef:
> Did you try to install Ubuntu 8.04 from gOS?
I did so attempt, unsuccessfully; Distribution Upgrade returned the following error:
>  Can't guess meta-package

Your system does not contain a ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or edubuntu-desktop package and it was not possible to detect which version of Ubuntu you are running.
 Please install one of the packages above first using synaptic or apt-get before proceeding.
Since my system already has X and Enlightenment, which Desktop package would be most appropriate?

---

### Post by Amranu on 2008-07-08
You shouldn't be trying to upgrade to 8.04 from gOS...

---

### Post by Sef on 2008-07-09
> I did so attempt, unsuccessfully; Distribution Upgrade returned the following error:

I would recommend downloading Ubuntu 8.04.1, and installing it from the disk.

---

### Post by bcschmerker on 2008-07-10
de Sef:
> I would recommend downloading Ubuntu 8.04.1, and installing it from the disk.

Looks like the best available option, as Synaptic Package Manager shows all Desktop options for Ubuntu having major Package changeouts prerequisite.  Now, if only I can figure out how to control CDBurn from gOS Desktop for the purpose of what's looking ever more a "clean install"....

---

### Post by peter3 on 2008-07-10
Upgrade Problems
After a few days of seeing the option to upgrade to 8.04.1 when I ran the update manager, I decided to try it.  The upgrade was from 6.06 LTS, and since I've had lots of serious problems with dist-upgrades in years of Debian use, I figured something would go wrong.  Actually, it wasn't too bad.  About 15 config files needed work, but at least most of them worked on first boot.  I have a weather station, the programming for which was started in inittab.  That didn't start, which caused me to learn about upstart.  A file in the /etc/event.d/ directory fixed that.  I use syslog-ng in order to better sort my logs and log some other systems.  The upgrade process simply ignored syslog-ng and returned the system to the standard logging program.  I had to install syslog-ng but it worked perfectly with the old config files.  But there is still one serious problem:  Printing to a USB printer does not work.  CUPS prints just fine to a parallel printer, so it doesn't look like a cups problem.  Error messages in syslog look like this:
Jul 10 10:14:44 zoltec cupsd[28466]: *** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
Jul 10 10:14:44 zoltec cupsd[28466]: *** WARNING *** Please fix your application to use the native API of Avahi!
Jul 10 10:14:44 zoltec cupsd[28466]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>

and the printer icon flashes a warning that it doesn't think the printer is connected.
I have failed to find anything related to this problem with google. 

Any help would be appreciated.
Peter

---

### Post by Sef on 2008-07-10
> But there is still one serious problem: Printing to a USB printer does not work. CUPS prints just fine to a parallel printer, so it doesn't look like a cups problem. Error messages in syslog look like this:
Jul 10 10:14:44 zoltec cupsd[28466]: *** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
Jul 10 10:14:44 zoltec cupsd[28466]: *** WARNING *** Please fix your application to use the native API of Avahi!
Jul 10 10:14:44 zoltec cupsd[28466]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>

and the printer icon flashes a warning that it doesn't think the printer is connected.

What is your make and model of your pinter?

---

### Post by SilentChorus™ on 2008-07-11
I have just received the Ubuntu 8.04 LTS Desktop Edition cd. 

I currently have Ubuntu 6.06 LTS which a freind installed a few years back, and want to upgrade. I know pretty much nothing about commands etc. I tried the alt F2 thing, and it came up with a run application box... but i'm not sure what I am supposed to select...

When I put the cd in the drive, it comes up with a tonne of files... and once again i'm unsure as to which I should choose.

I did try to upgrade though the upgrade manager via the internet, but as I am on dialup with 5 hour log offs... (Due to the kangaroos being a bit slow at the server... ) I am unable to download it.

I would be grateful for any help...

Thankyou,

~Dani~

I posted this in the normal thread as well. Sorry, I was unsure if this was the right place.

---

### Post by Sef on 2008-07-11
> I have just received the Ubuntu 8.04 LTS Desktop Edition cd.

I currently have Ubuntu 6.06 LTS which a freind installed a few years back, and want to upgrade. I know pretty much nothing about commands etc. I tried the alt F2 thing, and it came up with a run application box... but i'm not sure what I am supposed to select...

When I put the cd in the drive, it comes up with a tonne of files... and once again i'm unsure as to which I should choose.

I did try to upgrade though the upgrade manager via the internet, but as I am on dialup with 5 hour log offs... (Due to the kangaroos being a bit slow at the server... ) I am unable to download it.

I would be grateful for any help...

Thankyou,

~Dani~

I posted this in the normal thread as well. Sorry, I was unsure if this was the right place.

1) I replied in your other post.

2) Do not double post.  You can get an infraction for it, which I will not give you this time.  Thank you.

---

### Post by tripwire45 on 2008-07-13
I realize there's no direct path to upgrade from 6.06 to 8.04, so I was planning on backing up my home directory, blowing the installation away, doing a fresh install of 8.04, then restoring my home directory. Maybe I'm being naive. Is there anything else I need to be considering (and it would be nice if somehow, I could save and restore my Firefox bookmarks)?

-Trip

---

### Post by Sef on 2008-07-13
> I realize there's no direct path to upgrade from 6.06 to 8.04

You can upgrade directly from 6.06 to 8.04.  Read post #1.

---

### Post by tripwire45 on 2008-07-13
Oops. My bad. I was under the general impression that you could only automatically update from 7.10. I had to open the Update Manager twice before I could see the button allowing the upgrade (either I'm blind, or there was a slight snafu).

Seems I've got about 92 updates to work my way through first. I'll let you know how it goes. Thanks.

---

### Post by stoneattic on 2008-07-14
I'm sure the answer is NO, but I have to ask. 

Is there any way, (short of wiping and reinstalling) to "downgrade" back to 7.10?  

Since "upgrading" to 8.04 I've had a ton of broken apps, the most bothersome being that HPASM is not controlling the fans in my Proliant server properly anymore and NX server that I wrestled with for a long time to get working on 7.10 is also broken.

---

### Post by Sef on 2008-07-14
> Is there anyway, (short of wiping and reinstalling) to "downgrade" back to 7.10? 

No.  You have to reinstall 7.10.

> I'm sure the answer is NO, but I have to ask. 

There is no harm in asking: Better to ask and be sure.

---

### Post by eranical on 2008-07-19
I first had 6.06 which I upgraded to 7.10 when it came out. In the mean time I gave away my install cds. Now when I try to upgrade to 8.04 through update manager it asks me for the 6.06 cd!I tried the cd for 7.1 but it doesn't accept it. I infact managed to find a cd of 6.06 with a freind but even that doesn't help. 
If I download the install iso & burn a disk will it install as a seperate os choice or rewrite the current version? I am currently dual booting with Vista & the machine is an Acer Extensa 5620-6830.
At the same time it took a lot of fiddling to get wifi working first so wondering whether I should wait a while longer for now.

---

### Post by Sef on 2008-07-19
> If I download the install iso & burn a disk will it install as a seperate os choice or rewrite the current version? I am currently dual booting with Vista & the machine is an Acer Extensa 5620-6830.

You could either set up a separate partition and have 7.10, Vista, and 8.04 installed, or you could overwrite 7.10 and have just 8.04 and Vista installed.  It is up to you and how much space you have on your hard drive.

> At the same time it took a lot of fiddling to get wifi working first so wondering whether I should wait a while longer for now. 

It would depend on your wi-fi card.  I would post that question with your wi-fi card type in Network and Wireless.

---

### Post by IwasAnex on 2008-07-19
Hi everyone,
I have been trying to upgrade from 7.10 to 8.04.1 via the update manager. It appears stuck on the locales. The terminal window states 
```
 
Setting up locales (2.7.9-4) ...
Generating locales...
  en_AU.UTF-8...

```

It was sitting at that for 4 hours and I figured that something must be wrong or something. So I tried to shutdown and reboot in the terminal, but ended up hitting the reset button. After one aborted boot, I got to the recovery menu and set the box to repair packages, at which point it resumed the upgrade. But now it's sitting back at the same spot as before. Is it supposed to take >4 hours to upgrade or is there going wrong? 

Thanks in advance for any help

---

### Post by tripwire45 on 2008-07-20
Just an update on my experience. I did an upgrade from 6.06 to 8.04 via the upgrade manager. It took awhile for everything to download, but the upgrade went rather smoothly. I've compared this to the 7.10 to 8.04 upgrade I did on my virtual Ubuntu machine in VMware and there are some differences in terms of what appears on the panel (my name appears on the panel in the virtual machine but not my desktop, for example), but on the whole, no particular issues. Everything still works, so I'm pleased.

---

### Post by Sef on 2008-07-20
> I have been trying to upgrade from 7.10 to 8.04.1 via the update manager. It appears stuck on the locales. The terminal window states

Here is a way to [remove the locales]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html").  

> Remove unnecessary locale data

For this we need to install localepurge.Automagically remove unnecessary locale data.This is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.

Install localepurge in Ubuntu

sudo apt-get install localepurge

After installing anything with apt-get install, localepurge will remove all translation files and translated man pages in languages you cannot read.

If you want to configure localepurge you need to edit /etc/locale.nopurge

This can save you several megabytes of disk space, depending on the packages you have installed.

Example:-

I am trying to install dicus using apt-get

sudo apt-get install discus

after end of this installation you can see something like below

localepurge: Disk space freed in /usr/share/locale: 41860K

---

### Post by JamesUser on 2008-07-22
Hi,

Is there any list of bugs fixed in 8.04.1 that I can check to see if an update would really be worth it? I have a really slow internet connection. That's why I want to know before I run the update manager.

Thanks.

---

### Post by tripwire45 on 2008-07-22
Have a look at the following:

[http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

[http://fridge.ubuntu.com/node/1582](http://fridge.ubuntu.com/node/1582)

---

### Post by Sef on 2008-07-22
> Is there any list of bugs fixed in 8.04.1 that I can check to see if an update would really be worth it? I have a really slow internet connection. That's why I want to know before I run the update manager.

**Back up** your data before updating.  There is no 100% guarantees that all that there is an undiscovered bug or a glitch just might happen.

---

### Post by lenn-art on 2008-07-24
After upgrading, all my settings for my dualscreen setup are gone ... :-( I have a nvidia with 2 Eizo's on it. The last 2 times i needed to re-configure everything for my screen settings. The system is telling me that 'suddenly' i don't use the nvidia driver anymore (installed with envy). 

Is this a common problem?

---

### Post by gcee on 2008-07-24
just looked at the udate manager and saw there were updates, having updated 2 days ago from 710 to 804, i noticed a bunch of kernel updates, so i (like a dummy) did them, now when the systme boots into the new kernel, it hangs on some security garbage and never moves forward.

only resolution at this time is to boot into the previous kernel .19

can i just modify grub and delete the newer kernels to get rid of that stuff, or maybe i need to wait (maybe for hours) to let it decide for itself?

any suggestions?

---

### Post by silvanus2005 on 2008-07-24
In Synaptic you can search for linuxversion. It will show you a list of kernels that are in your computer, and you can select the unwanted ones and delete them, the same way as you delete any other packages you don`t want to keep anymore.

---

### Post by darkzeus85 on 2008-07-24
I am in the process of upgrading from an up to date 7.10 to 8.04.1 LTS. Everything has went well up until about 7 minuets to completion
 
terminal says

```
Installing new version of config file /etc/belocs/iso-639.def ...
Generating locales...
  en AU.UTF-8...
```

an it has been there for sometime (around 30 mins) is this normal or what can I do?

Any info needed for me to provide just ask and I will do my best

---

### Post by gcee on 2008-07-24
look here last couple of posts

[http://ubuntuforums.org/showthread.php?t=868771&page=2](http://ubuntuforums.org/showthread.php?t=868771&page=2)

---

### Post by darkzeus85 on 2008-07-24
had to sudo the commands but everything is at least moving thanks I will keep posted if everything works

---

### Post by darkzeus85 on 2008-07-24
well here's the problem I updated and the moniter I am using is not displaying the GNOME when booted normally (another moniter displays everything fine but i can not use other moniters for too long as they do not belong to me) but if I boot into recovery mode and tell it to fix X and the run dpkg using the graphical interface and then boot normally form there I get to the login screen and if I login to a normal session I get a white screen where the desktop should be and I am able to ctrl+alt+bkspace back to the login screen and I go to options and change session to GNOME Failsafe and I get a usable desktop with an error about not being able to start or use nautilus because of whatever. 

If I go to hardware drivers there is a driver for my ATI (I know the history of ubuntu and ATI) that I used with out many problems on 7.10 that is not enabled. If I enable it and restart I get the same problem and have to start in GNOME Failsafe to get a usable desktop and the driver is disabled again. 

What can I do to fix this short of replacing the graphics card (which is needed due to a pinkish hue that can not be fixed no matter what I try even in XP which is where is started long befor I installed any linux distro(I belive it ran too hot and burned out playing FPS's or maybe a power surge or failure not sure what caused it)).

---

### Post by zipperback on 2008-07-25
> **jwaiwit said:**
> Hmm. Ok So I no need to re-install again. Thanks for all suggest.
Actually I waiting for new features coming after installation.:)

If your system has 8.04.1 then you don't need to update. That means its the current version.

```

sudo apt-get update && sudo apt-get upgrade

```

That should bring you fully up to date though from 8.04 to 8.04.1

- zipperback
:popcorn:

---

### Post by Sef on 2008-07-25
> well here's the problem I updated and the moniter I am using is not displaying the GNOME when booted normally (another moniter displays everything fine but i can not use other moniters for too long as they do not belong to me) but if I boot into recovery mode and tell it to fix X and the run dpkg using the graphical interface and then boot normally form there I get to the login screen and if I login to a normal session I get a white screen where the desktop should be and I am able to ctrl+alt+bkspace back to the login screen and I go to options and change session to GNOME Failsafe and I get a usable desktop with an error about not being able to start or use nautilus because of whatever.

If I go to hardware drivers there is a driver for my ATI (I know the history of ubuntu and ATI) that I used with out many problems on 7.10 that is not enabled. If I enable it and restart I get the same problem and have to start in GNOME Failsafe to get a usable desktop and the driver is disabled again.

What can I do to fix this short of replacing the graphics card (which is needed due to a pinkish hue that can not be fixed no matter what I try even in XP which is where is started long befor I installed any linux distro(I belive it ran too hot and burned out playing FPS's or maybe a power surge or failure not sure what caused it)).

Since it works ok with the other monitor, the problem could be with your monitor and not your graphics card.

---

### Post by schiffsratte on 2008-07-26
yes sounds def like the mon.
Look if there is a reset/recall button.
If that doesnt work you'll have to replace it .

Ati drivers have to be reinstalled after every Kernel version change - they need to recompile their modules etc; that's not an Ubuntu issue - same on every distro

---

### Post by Tomy on 2008-07-26
I have three computers at the sales counter that have been upgraded from 7.04 to 7.10. Now I want to upgrade to 8.04.1.

The gui update-manager does not offer "Distribution upgrade to 8.04 available" -- it just reports "up to date" or some such thing.

$ sudo apt-get dist-upgrade 
also reports "up to date"

Can I just goto /etc/apt/sources.list and change 'gutsy' to 'hardy' and do a
$ sudo apt-get dist-upgrade

Thanks
Tomy

---

### Post by Sef on 2008-07-26
> The gui update-manager does not offer "Distribution upgrade to 8.04 available" -- it just reports "up to date" or some such thing.

Did you follow these [instructions]("https://help.ubuntu.com/community/HardyUpgrades")?

> Can I just goto /etc/apt/sources.list and change 'gutsy' to 'hardy' and do a
$ sudo apt-get dist-upgrade

1) Yes.  

2) **Back up** your data first.

---

### Post by leew on 2008-07-27
Hi Everyone.

I hope this query hasn't been posted anywhere else-I've looked but can't find anything similar anywhere.

I've installed 6.06.2 LTS and would like to upgrage to 8.04.1, or ubuntustudio.

I've run the software update manager and installed all updates, I've enabled all the repositories I can find, but I still don't get the "New Distribution Release available" screen prompting me to upgrade.

I can't find any reason why.

Can anyone help?

---

### Post by Sef on 2008-07-27
> I've run the software update manager and installed all updates, I've enabled all the repositories I can find, but I still don't get the "New Distribution Release available" screen prompting me to upgrade.


Clink on the link in post #45.

---

### Post by leew on 2008-07-27
Followed the link and followed all the intructions. Still nothing happens.

It says "Downloading package information" and then once that has completed examines system and build dependancy tree, but nothing more than that.

---

### Post by Sef on 2008-07-27
From post #44, you can upgrade this way:

> Can I just goto /etc/apt/sources.list and change 'gutsy' to 'hardy' and do a
$ sudo apt-get dist-upgrade


gksudo gedit /etc/apt/sources.list

then 

sudo apt-get update && sudo apt-get dist-upgrade

(you can copy and paste those codes.)

The other option is a clean install.

---

### Post by philven on 2008-07-27
> **misterbk said:**
> This may be silly and I don't know if it's related to 8.04.1 or always been like that, but it caused me hesitation during install:

 
Time zone selection:
Nothing close to my city is in that graphical "click a time zone" map.  (I would be in San Francisco.)  I notice there are dozens of cities all in the same spot in the Midwest but the West coast is barren.  I wouldn't care, but the list of time zones is also by city.  Ask me my time zone and I can easily reply "oh it's GMT - 8:00" and every other time zone picker works this way.  But in Ubuntu, I have to find another city that I know to be in the same time zone as myself, which is kinda backwards, and the time zone isn't listed in the pull-down at all.

Also, this install of Ubuntu is the first time I've ever seen a time zone picker declare "GMT - 7:00" for Pacific time.  Maybe I'm really wrong about this, but I thought my time zone stays "GMT-8:00" even if Daylight Savings is in effect?  (As if Daylight Savings is something that happens "on top" of my time zone, i.e. "GMT - 8:00 + DST", not something that redefines my time zone as GMT - 7:00 during some times of the year.

Another thing - I'm sort of disappointed that the partition tool still doesn't let you choose partition flags.  I can add them to fstab, but the text-mode partition tool let me set noexec and nosuid flags.  (despite its other failings of being too hard to use for many people.)

I'm trying the KDE4 remix package.

Just click on Los Angeles. It's in the same time zone as San Francisco.  So is Tijuana.

---

### Post by AliG on 2008-07-28
after running the update manager it is now showing another kernel in the startup menu.

it defaults to the new kernel "2.6.24.20" on startup  but hang at "Starting Up"

if i chose kernel 2.6.24.19 it works fine and the log doesn't contain any startup info on the frozen startup.


i am complete noob so will appreciate any help.

---

### Post by Sef on 2008-07-28
> after running the update manager it is now showing another kernel in the startup menu.

it defaults to the new kernel "2.6.24.20" on startup but hang at "Starting Up"

if i chose kernel 2.6.24.19 it works fine and the log doesn't contain any startup info on the frozen startup.


i am complete noob so will appreciate any help. 

There is a way to set the kernel, so .19 will start.  I will post it as soon as I find it.

---

### Post by silvanus2005 on 2008-07-29
There is an application, startup-manager. You can install it using synaptic and let you choose which kernel will be the default at start-up. It`is very easy to use it, it has a graphic interface.

---

### Post by Sef on 2008-07-29
> There is an application, startup-manager. You can install it using synaptic and let you choose which kernel will be the default at start-up. It`is very easy to use it, it has a graphic interface.

Thank you for that.

To download it the easy way:

Applications > Add/Remove > Show: 'All Available Applications' > Search: Startup > Click on top box next to Startup-Manager > click apply changes > click apply > close

---

### Post by ubuntal on 2008-07-29
> **AliG said:**
> after running the update manager it is now showing another kernel in the startup menu.

it defaults to the new kernel "2.6.24.20" on startup  but hang at "Starting Up"

if i chose kernel 2.6.24.19 it works fine and the log doesn't contain any startup info on the frozen startup.

You can edit the menu (provided you're using GRUB)

```
sudo gedit /boot/grub/menu.lst
```

Just change the number next to "default", save, and reboot.

---

### Post by tripwire45 on 2008-07-30
Just to add to that piece of advice, once the list opens in gedit, you'll need to scroll down to the bottom of the document to see the kernel list.

---

### Post by AliG on 2008-07-31
Thanks all for the above answers. :)

---

### Post by TrashmanL on 2008-07-31
I am currently using a Sempron (AMD64) laptop with 8.04. I usually run a Kubuntu session on my account, but I have both KDE and GNOME installed. 

I haven't installed all upgrades yet, because next to ubuntu-desktop in Adept Updater, instead of saying "upgrade" it says "remove" This concerns me some, so I haven't yet applied all updates. Is this normal, or am I going to have to work around this by using apt-get?

Additionally, I find that if I cancel that change, but attept to upgrade Firefox 3, GIMP, transmission, or xulrunner on the list it tries to force me to remove ubuntu-desktop. (These upgrades are only for 8.04.1, I guess?)

It also wants to remove startupmanager, yelp, and strangely GIMP. That's right, if I select to upgrade GIMP, it selects upgrade for "gimp-data" but tries to remove everything else GIMP related.

---

### Post by TrashmanL on 2008-07-31
OK, I logged in with a GNOME session and ran the update manager, and I now know I definitely have a problem. The GNOME update manager is a bit more verbose about the problem than adept.

When I start it, it says:

Not all updates can be installed
Run a partial upgrade, to install as many updates as possible
This can be caused by:
   A previous upgrade which didn't complete
   Problems with some of the installed software
   Unofficial software packages not provided by Ubuntu
   Normal changes of a pre-release version of Ubuntu

But then when I select "Partial Upgrade", a box with "Distribution upgrade" on top pops up. It says "Running partial upgrade" and it gets to the first line "Preparing to upgrade" then I get this error:

Could not calculate the upgrade
A unresolveable problem occured while calculating the upgrade
This can be caused by:
  Upgrading to a pre-release version of Ubuntu
  Running the current pre-release version of Ubuntu
  Unofficial software packages not provided by Ubuntu
This is most likely a transient problem, please try again later.

If I cancel instead of selecting partial upgrade, all the upgrades in the list are grayed out.

The only "unofficial software packages" I have are from medibuntu, which have never given me problems before. Am I going to have to uninstall these to upgrade?

---

### Post by Sef on 2008-08-01
What errors do you get when you run these codes from the terminal (Applications > Accessories > Terminal):

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

---

### Post by TrashmanL on 2008-08-01
sudo apt-get update

no errors

sudo apt-get upgrade

does not generate any actual errors, but does say:

The following packages have been kept back:
  firefox-3.0 gimp gimp-data gimp-gnomevfs gimp-python libgimp2.0
  transmission-common transmission-gtk xulrunner-1.9
  xulrunner-1.9-gnome-support

all of the other packages up for upgrade installed without a problem.

---

### Post by Sef on 2008-08-02
> The only "unofficial software packages" I have are from medibuntu, which have never given me problems before. Am I going to have to uninstall these to upgrade?

Applications > Accessories > Terminal

copy or type in the this code and post your sources list:

```
cat /etc/apt/sources.list
```

---

### Post by TrashmanL on 2008-08-02
here is my /etc/apt/sources.list file:

> deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2)]/ hardy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse



and here is my /etc/apt/sources.list.d/medibuntu.list file

> ## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

### Post by marufsiddiqui on 2008-08-03
hi i need to know something.

1. i've kubuntu 7.10 installed. i'm willing to upgrade to 8.04. so what i have to do for this? do i have to reinstall like formatting the drive again or can i just upgrade it over 7.10, 

also if i want to install ubuntu 8.04 do i have to fully reinstall it over kubuntu 7.10? BTW i've only the live cds, i'm not sure if i make myself clear

---

### Post by Sef on 2008-08-03
> and here is my /etc/apt/sources.list.d/medibuntu.list file

Quote:
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 

Comment out this line:  > deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

To comment it out, just put a # before deb, so it should look like this: > #deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

The other option would be to uncomment out the deb-src line.
It would look like this:  > deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free 

---

### Post by Sef on 2008-08-03
> 1. i've kubuntu 7.10 installed. i'm willing to upgrade to 8.04. so what i have to do for this? do i have to reinstall like formatting the drive again or can i just upgrade it over 7.10,

also if i want to install ubuntu 8.04 do i have to fully reinstall it over kubuntu 7.10? BTW i've only the live cds, i'm not sure if i make myself clear

1) You can do either option.  The best way is to reinstall, but you lose all your settings.  Upgrading keeps your settings, but it has a higher failure rate than a clean install.

2) If you reinstall, then install Ubuntu.  If you upgrade Kubuntu to 8.04, then read '[Install Gnome on Kubuntu]("http://www.psychocats.net/ubuntu/gnome")'.

---

### Post by TrashmanL on 2008-08-04
Well, after doing that, it allowed me to upgrade Firefox, but the GIMP and Transmission updates are still held back, and it still hasn't done the version update. Is this even making any sense??

I'm trying to think of possible causes for this error...

I did have to install some 32-bit apps (Java, Swiftweasel) because the 64-bit versions weren't working. I did it using scripts found on these forums. Could that cause these errors? Though I'd expect more people to be posting with the same issue if that was the case.

I also installed some 32-bit libs using getlibs to solve some dependencies.
But all of these things were official Ubuntu Hardy packages... just for a different architecture, installed to my lib32 directory.

I noticed these packages do not show up in Synaptic, so if I did have to remove them, how would I remove them? I guess apt-get remove would be the obvious answer, but I don't know the exact package names for these, which is why Synaptic is nice, it shows a list of names to choose from.

---

### Post by Sef on 2008-08-05
> Well, after doing that, it allowed me to upgrade Firefox, but the GIMP and Transmission updates are still held back, and it still hasn't done the version update. Is this even making any sense??

Either type or copy this code:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you get any errors, please paste them.

---

### Post by TrashmanL on 2008-08-05
There were no errors. I did not continue with the installation however, because this is what it said:

> Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080422.2) hardy/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Get:2 [http://archive.canonical.com](http://archive.canonical.com) hardy Release [6998B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Sources
Fetched 7187B in 1s (5504B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  gimp gimp-gnomevfs gimp-python transmission-gtk ubuntu-desktop
The following packages have been kept back:
  libgimp2.0
The following packages will be upgraded:
  gimp-data transmission-common
2 upgraded, 0 newly installed, 5 to remove and 1 not upgraded.
Need to get 9751kB of archives.
After this operation, 13.1MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

I posted the whole thing, because I've been noting that the list it searches is much bigger than what's in my sources.list file. I probably should've included this earlier.

The information basically reflects what Adept Updater said. I didn't go forward, because I don't think removing ubuntu-desktop would be a step in the right direction. (Though I would still have a GUI because kubuntu-desktop is also installed on my machine)

---

### Post by TrashmanL on 2008-08-05
I tried to manually remove transmission and gimp, thinking they might have something to do with the problem.

transmission was removed with no issues (I have other BitTorrent clients installed, anyway)

when I tried apt-get remove gimp, however, it once again insisted I must remove ubuntu-desktop in order to do so

another observation, when I open up Update Manager, GIMP is listed under "backports" for some strange reason.

---

### Post by Sef on 2008-08-06
> I posted the whole thing, because I've been noting that the list it searches is much bigger than what's in my sources.list file. I probably should've included this earlier.


Do you want all of them sources open?  If not, then uncheck them.

---

### Post by Poppyelvin on 2008-08-06
After upgrading to 8.04 from the disc that came with the Linuxpro magazine. I opened the update manager. It gave me this message:
 "Software index is broken
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

So I tried Synaptic. It gave me this message:
 "Please insert the disk labeled:
Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)in drive /cdrom/"

So I tried the terminal, it gave me a similar message:

 "Media change: please insert the disc labeled 'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)'in the drive '/cdrom/' and press enter"

No matter what I do it can't seem to find my disc. Any help out there?

Thank You: Poppyelvin

---

### Post by trhebig on 2008-08-06
> **Sef said:**
> Here is a way to [remove the locales]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html").

I have this problem as well.  I tried to upgrade from 7.10 to 8.04.1 via the update manager. It got stuck on the locales. The terminal window stated:

Setting up locales (2.7.9-4) ...
Generating locales...
  en_AU.UTF-8...

I let it sit overnight and it was still stuck, so I shut down the machine.

Where do I go from here?  I see that there is a way to remove unnecessary locles, but I'm not sure that the upgrade is complete.

Am I left with a partial upgrade that might be broken in some way?  Do I need to try do the upgrade again somehow?  
What do I need to do to get a good 8.04 installation?

Thanks.

---

### Post by TrashmanL on 2008-08-06
> So I tried Synaptic. It gave me this message:
"Please insert the disk labeled:
Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)in drive /cdrom/"

When I first got my laptop with 8.04 installed on it, I found that anytime it asked for the CD-ROM, I had to mount it manually to the /media/cdrom folder in order for installations to find it.

You will need to figure out what device the cdrom is on your system.

This is the command I have to use on my machine:

```
sudo mount /dev/cdrom1 /media/cdrom
```

/dev/cdrom1 is a symbolic link to /dev/hda on my machine, which is the actual device. so

```
sudo mount /dev/hda /media/cdrom
```

also works. But, hda is usually the first harddrive on most systems, your CDROM might be hdb, hdc, or hdd depending on how many drives you have on your machine. On some it could even be sda, sdb, etc. There's no harm in trying each of these devices until you figure out the right one.

---

### Post by TrashmanL on 2008-08-06
> Do you want all of them sources open? If not, then uncheck them.

No, I don't. The question is, WHERE do I uncheck them? (Boy, I feel like a n00b now). They aren't in my sources.list, where else would they be listed?

---

### Post by TrashmanL on 2008-08-06
OK, found it! "Software Sources" Now I feel like an idiot. I found out I had a couple problems. I disabled the "backports" for now, and I enabled hardy-updates. I don't know how it got disabled to begin with! But anyway, I now have a list of 260 some updates, with nothing "BROKE" and nothing requiring removal, so this should work. Thanks for the help.

---

### Post by Markus72 on 2008-08-06
Hi,

and another one from Gutsy: few weeks ago update manager told me that a new distro was available. I decided to not install it that time and I skipped some kernel update, too.

Now when I tried to update, the update manager crashed with an error (a distro update never was mentioned anymore).
I had a backup, restored it and tried it by command line.

This time I made a dist-upgrade right from the start without preceding update.
It worked. There was no error. No further upgrade was needed (according to apt).

But: when I started Synaptic and started an source update, it crashed again.

So its again broken.

By the way: lsb_release still tells me Im on 7.10 Gutsy.

What is wrong? Is there a chance to have 8.04 without a fresh install? Is the option of a CD install in post #1 one without data/config loss?

Thanks
Markus

---

### Post by s3a on 2008-08-08
> **Franc88 said:**
> That's my problem now with 8.04.1, my freaking wireless is not working.  Got it to work for 8.04 but now its dead.  The hardware driver is installed and enable but status is "not in use".  I've tried re-installing the driver and booting a version prior to the update but no go.  This latest update is a cluster ****.  I should have known to wait before being one of the guinea pigs of this latest update.

I should have learned my lesson with Windows but I really thought that ubuntu would be different.

Well you should know to actually test those kind of things with the Live CD of the version you want to install before actually going ahead with the installation process. Before installing, check things in the future.

---

### Post by ejs7597 on 2008-08-09
when I run apt-get install localepurge I get the following error.
dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
If I run that it is back to being stuck at Generating locales...
en_AU.UTF-8...

---

### Post by TrashmanL on 2008-08-09
ejs & Markus,

try running 

```
sudo apt-get install -f
```

Then try doing what you were doing again. That command attempts to automatically fix broken packages. It's worth a shot. I had my upgrade interrupted and that worked for me to get it going again.

---

### Post by jcsaintpo on 2008-08-10
I have this problem as well.  I tried to upgrade from 7.10 to 8.04.1 via the update manager. It got stuck on the locales. The terminal window stated:

Generating locales...
  en_AU.UTF-8...
then get pages full ^CCB^CCB

I let it sit overnight and it was still stuck!

Do i still keep it running or what?
I started upgrading yesterday, and its now 24h upgrading and apparently stuck on this stage!

---

### Post by newbee8 on 2008-08-11
Hello everyone!  I'm using a Dell factory installed 7.04 which last week was upgraded to 7.10 (sucessfully) followed by an upgrade to 8.04 which was not so sucessful.  I'm clueless to this OS.  At startup, my login brings up only a blank screen.  I can login through "options" in safe mode but can not use the web browser to update.  An error message says to manually run "pbkg -configure -a".  How do I do that?  Or is there a better way to correct this problem?  I have a CD with 8.04.1-desktop-i386.iso on it but can not do anything with it. :(

---

### Post by TrashmanL on 2008-08-11
**jcsaintpo,** >>> you need to stop your installation and try the locale fix mentioned earlier in this thread.



**newbee,** >> If you can remember, if you could tell us what the error message was when your 8.04 upgrade failed, that would be useful.

You shouldn't need a web browser to update Ubuntu. When you login, what do you get? Does the desktop appear? Do you have access to your menus? If you have access to your menus, go to your Applications menu and find "Terminal" (this is kind of like command prompt if you've ever used that in Windows). I don't remember the default location for this, as my menus have been customized. 

After you click on Terminal, it should pop up a black window with something like "user@ubuntu~$" and a blinking box (cursor). This is where you can type in the manual commands. I would suggest typing

```
sudo apt-get install -f
```

(hit enter to run the command) then doing

```
sudo dpkg --configure -a
```

Notice both of these start with "sudo" this is the administrator command in Ubuntu. It will ask for your password after the first command. If you don't include it, it won't let you run the command. I assume "pbkg" is a typo, there is no such thing to my knowledge. Also, notice there are two dashes before configure, not just one. Typing the code exactly as above is VERY IMPORTANT.

---

### Post by TrashmanL on 2008-08-11
**newbee** >>> a separate issue. Your iso of Hardy Heron. You can't just burn an iso file to the CD, it won't work. You need to use the "burn CD from image" option in your CD Burner, then select the iso file.

---

### Post by jcsaintpo on 2008-08-12
I can't restart Ubuntu normaly, only in recovery mode!

When in recovery-mode i open a terminal mode and do this?

> Remove unnecessary locale data
For this we need to install localepurge.Automagically remove unnecessary locale data.This is just a simple script to recover diskspace wasted for unneeded locale files and localized man pages. It will automagically be invoked upon completion of any apt installation run.
Install localepurge in Ubuntu
sudo apt-get install localepurge
After installing anything with apt-get install, localepurge will remove all translation files and translated man pages in languages you cannot read.
If you want to configure localepurge you need to edit /etc/locale.nopurge
This can save you several megabytes of disk space, depending on the packages you have installed.



Code:
sudo apt-get install -f



And then restart the upgrade?

---

### Post by jcsaintpo on 2008-08-12
> **jcsaintpo said:**
> I can't restart Ubuntu normaly, only in recovery mode!

When in recovery-mode i open a terminal mode and do this?



And then restart the upgrade?

I restarted in recovery!
Wanted to install localepurge

It said
dkpg was interrupted , you must normally run "dpkg --configure -a"

I tried typing this code
it restarted loading the locales and blocked at the same point

en_AU..UTF-8

---

### Post by TrashmanL on 2008-08-12
I'm running out of ideas. Hopefully someone else can help you if this doesn't work.

try apt-get install -f first, then run apt-get update, then try installing localepurge

or, in one line

```
sudo apt-get install -f && sudo apt-get update && sudo apt-get install localepurge
```

---

### Post by jcsaintpo on 2008-08-12
> **TrashmanL said:**
> I'm running out of ideas. Hopefully someone else can help you if this doesn't work.

try apt-get install -f first, then run apt-get update, then try installing localepurge

or, in one line

```
sudo apt-get install -f && sudo apt-get update && sudo apt-get install localepurge
```

It did not succeed!
I got the same warning 
dkpg was interrupted , you must normally run "dpkg --configure -a"

In another post i found this code might help

```
chmod 644 /usr/bin/localedef
killall locale-gen
```

After that i wrote

```
dpkg --configure -a
```

Then the locales where overruled and installing continued!
(it's happening now)

Apparently after updating is done i have to type
```
chmod 755 /usr/bin/localedef
```

[solution found here]("http://ubuntuforums.org/showthread.php?t=868771&page=2")

---

### Post by jcsaintpo on 2008-08-12
> **jcsaintpo said:**
> It did not succeed!
I got the same warning 
dkpg was interrupted , you must normally run "dpkg --configure -a"

In another post i found this code might help

```
chmod 644 /usr/bin/localedef
killall locale-gen
```

After that i wrote

```
dpkg --configure -a
```

Then the locales where overruled and installing continued!
(it's happening now)
i got manny error messages "no depencies"

Apparently after updating is done i have to type
```
chmod 755 /usr/bin/localedef
```

[solution found here]("http://ubuntuforums.org/showthread.php?t=868771&page=2")

After this i rebooted!
Ubuntu 8.04.1 was installed!  but unfortunately it got stuck after i entering the login page

So i rebooted into the recovery mode
then pushing the button "dpkg (repairing pachages)"
Then the locales started installing!
I had to do this 2 times

But now i get error-message "could not resolve be.archive.ubuntu.com"
I have also several depency problems now!

---

### Post by musicman12 on 2008-08-14
> **IwasAnex said:**
> Hi everyone,
I have been trying to upgrade from 7.10 to 8.04.1 via the update manager. It appears stuck on the locales. The terminal window states 
```
 
Setting up locales (2.7.9-4) ...
Generating locales...
  en_AU.UTF-8...

```

It was sitting at that for 4 hours and I figured that something must be wrong or something. So I tried to shutdown and reboot in the terminal, but ended up hitting the reset button. After one aborted boot, I got to the recovery menu and set the box to repair packages, at which point it resumed the upgrade. But now it's sitting back at the same spot as before. Is it supposed to take >4 hours to upgrade or is there going wrong? 

Thanks in advance for any help

Sorry to use a quote here but this is the exact same problem I have been having so this solution is with cleaning out some files or am I totally misunderstanding? I wouldnt think this would be a hardware issue since all other upgrades have went fine, like in the quote above been trying to go from 7.10 to 8.04

Thanks for any help :confused:

---

### Post by TDragon on 2008-08-14
> **Franc88 said:**
> That's my problem now with 8.04.1, my freaking wireless is not working. Got it to work for 8.04 but now its dead. The hardware driver is installed and enable but status is "not in use".

I've had similar issues.

---

### Post by anukoolr on 2008-08-14
Hi,

I am a new person to this forums. I am actually amazed with 2 things. One is Ubuntu and the other one is you all... Can you all help me to become a savy like you guys?? I also have a question regarding VMware. Link to my post is [http://ubuntuforums.org/showthread.php?t=889720](http://ubuntuforums.org/showthread.php?t=889720) .  Any help would be greatly appreciated.

Thanks
Anukool.R

---

### Post by dorite on 2008-08-21
Looks to me like the upgrade process is not yet ready for prime time.  My experience is that everything worked (no locale problem) up until time to enter my name (in the "name, id, password, computer name" screen".  I hit enter after my name and the process bombed so thoroughly that the screen went black and there was no video input to the monitor, no response to the keyboard.  A reset took me to the grub loader, then to a seized, black screen.

After a lot of agonizing, I downloaded the whole new 8.04.1 iso and started over.  That worked.  AND it seems like all my data is still there!

I'm afraid I'd have to recommend reinstalling over upgrading.

---

### Post by Sef on 2008-08-21
> Looks to me like the upgrade process is not yet ready for prime time. My experience is that everything worked (no locale problem) up until time to enter my name (in the "name, id, password, computer name" screen". I hit enter after my name and the process bombed so thoroughly that the screen went black and there was no video input to the monitor, no response to the keyboard. A reset took me to the grub loader, then to a seized, black screen.

After a lot of agonizing, I downloaded the whole new 8.04.1 iso and started over. That worked. AND it seems like all my data is still there!

I'm afraid I'd have to recommend reinstalling over upgrading.

Reinstalling is recommended over upgrading.  Upgrading can work, but it can be problematic, especially if propriatery drivers are used.

---

### Post by jcsaintpo on 2008-08-22
> **Sef said:**
> Reinstalling is recommended over upgrading.  Upgrading can work, but it can be problematic, especially if propriatery drivers are used.

I tried installing!
But i always get busybox using the Live-cd and mini.iso

Apparently something to do with ata and Ide-drivers!
I tried using the hints they gave here on the forum, but nothing worked!

---

### Post by Sef on 2008-08-22
From another [post]("http://ubuntuforums.org/showthread.php?t=847108"), there was this suggestion:

> Try this as a boot option: all_generic_ide.

---

### Post by jcsaintpo on 2008-08-22
> **Sef said:**
> From another [post]("http://ubuntuforums.org/showthread.php?t=847108"), there was this suggestion:

in mini.iso it says "can't find kernel"

I tried it in live cd and it didn't help either!
It throws me a bunch of errors
 buffer i/o error in device sr0
 ata.1: status [DRDY]

these errors copied into pages full

---

### Post by Sef on 2008-08-22
I wonder if the problem is with the Hardy kernel.     Check out the I[ntrepid Ibex's Live CD]("http://www.ubuntu.com/testing/intrepid/alpha4").   It is alpha now, but if it boots ok, then I suspect the Hardy kernel would definately be the problem.   It's not for use on a stable system, but I'm not sure what else to do.

---

### Post by jcsaintpo on 2008-08-22
> **Sef said:**
> I wonder if the problem is with the Hardy kernel.     Check out the I[ntrepid Ibex's Live CD]("http://www.ubuntu.com/testing/intrepid/alpha4").   It is alpha now, but if it boots ok, then I suspect the Hardy kernel would definately be the problem.   It's not for use on a stable system, but I'm not sure what else to do.

do i also add all_generic_ide ?

(am downloading now)

---

### Post by Sef on 2008-08-22
> do i also add all_generic_ide ?

I would try it without and if that doesn't work, I would try it with it.

---

### Post by Ahmed Amr on 2008-08-23
hi everyone
i am new to ubuntu. and i have installed ubuntu 7.0 theni upgraded it without doing all the updates no i have 8.04. then i made the updates.
so do i have to make all updates first??
do i have to reinstall ubuntu??

---

### Post by Sef on 2008-08-23
> hi everyone
i am new to ubuntu. and i have installed ubuntu 7.0 theni upgraded it without doing all the updates no i have 8.04. then i made the updates.
so do i have to make all updates first??
do i have to reinstall ubuntu?? 

Yes reinstall would be best.  Before upgrading, make sure you are current with all the updates.

From [Gutsy Gibbon Upgrades]("https://help.ubuntu.com/community/GutsyUpgrades"):
> Before you start

    *

      You can only directly upgrade to Ubuntu 7.10 ("Gutsy Gibbon") from Ubuntu 7.04 ("Feisty Fawn") (see UpgradeNotes).
    * Be sure that you have all updates applied to Ubuntu 7.04 before you upgrade.
    *

      Before upgrading it is recommended that you read the release notes for Ubuntu 7.10, which document caveats and workarounds for known issues in this version. 

---

### Post by msdobrescu on 2008-08-25
Hello,

Is there a 8.04 or 8.04.1 DVD of kubuntu?
Thanks in advance.

---

### Post by Sef on 2008-08-25
> Is there a 8.04 or 8.04.1 DVD of kubuntu?


Here's an [Ubuntu DVD]("https://wiki.ubuntu.com/Mirrors#DVD%20Images").  Read [Psychocats]("http://www.psychocats.net/ubuntu/kde") to change Ubuntu to Kubuntu.

---

### Post by jcsaintpo on 2008-08-29
> **Sef said:**
> I would try it without and if that doesn't work, I would try it with it.

I tried starting intrepid!  I got the same I/O errors!
The "ide" thing thing had same result!

I succeeded only once to install 8.04!  This by installing 6.06 and hen upgrade to 8.04!  But that is so stupid!
I want to install directly!

---

### Post by tananaBrian on 2008-08-29
During the upgrade from v7.10 t v8.04, I got asked many times if I wanted to keep my locally modified menu.lst or not ...I kept keeping it, figuring on taking a more careful look later.  After the upgrade process finished, I did not (of course) see the new kernel listed in the menu.  After logging in, I thought "Never had trouble with the new menu.lst before, so why not try it now?"  So then I ran upgrade-menu.lst and updated the thing.  Now it only includes the memory test option and my Windows XP option ...no boot options that are NOT the memory test for Ubuntu.  (My machine is dual boot Ubuntu / Windows XP Pro).

The mem test took forever and I gave up.  Will it eventually boot into Ubuntu?  If not, then I'm in a pickle... Due to the different partition type, I cannot get to menu.lst to edit it via Windows and I cannot boot into Ubuntu.

Anybody know how to get to and fix menu.lst so it'll have an option for booting directly into v8.04 without the memory test?  Am I stuck now and must d/l the ISO and reinstall from disk?

Thanks,
Brian

---

### Post by keiffee30 on 2008-08-30
i have been running with 7.10 ever since it come out on my main PC. and i have got all the bits install and working as it should 

Apatche 2.x (about 8 web sites working)
PHP5 
Mysql
Wine
RDC
Email
etc...etc

Now 8.04 is out. And i have installed this on my laptop without any issues (well the mouse didn't work untill i turned it on in bios). I have got wine to work better on this version of unbuntu also the screen candy seams to works better. 


Now when i did an upgrade from 7.04 to 7.10 i endded up losing all my data and having to reinstall. This is not good if i have to reset all the web sites and user data. 

Is there a way for taking a image (like in ghost) for backing up all the system before i try a upgrade of 7.10 - 8.04, also is it worth doing should i try the up grade or just leave alone????????

Any comments please

---

### Post by Sef on 2008-08-30
> Is there a way for taking a image (like in ghost) for backing up all the system before i try a upgrade of 7.10 - 8.04, also is it worth doing should i try the up grade or just leave alone????????

If 7.10 is running how you want it, then leave it as it is.  As for backups, check out [partimage]("www.partimage.org/") or [clonezilla]("www.clonezilla.org/").


> I succeeded only once to install 8.04! This by installing 6.06 and hen upgrade to 8.04! But that is so stupid!
I want to install directly! 

It sounds like an incompatibility with some hardware due to a regression.  I'm not sure what else to do at this point.  If I come across any ideas, I will tell you.

> Anybody know how to get to and fix menu.lst so it'll have an option for booting directly into v8.04 without the memory test? Am I stuck now and must d/l the ISO and reinstall from disk?


Download [Super GRUB Disk]("supergrub.forjamari.linex.org/") then burn it and reinstall GRUB.

---

### Post by leden on 2008-08-31
Today, I decided to upgrade my Ubuntu 7.04 (Feisty). The first step I did was to upgrade from 7.04 to 7.10 (Gutsy). Now I am stuck with it because I read elsewhere that upgrading from kernel 2 xx.15 causes a freeze on upgrade (locale packages).
I have the following options in Grub:
Ubuntu 7.10, kernel 2.6.22-15-generic
Ubuntu 7.10, kernel 2.6.20-17-generic (this was created by updating Ubuntu 7.04)
I know I can make a fresh installation with 8.04, but I would like to keep my existing data and configs. Is it possible to install 8.04 without formatting the current partition with 7.10 so I can keep all my data?

How can I get Ubuntu 8.04 working?

---

### Post by keiffee30 on 2008-08-31
Many thanks Sef for the information

---

### Post by nss0000 on 2008-08-31
What is this "back-up-data" you speak of ? Isn't that why I'm moving to HH, to have less data backup and more data quickly available ?? Can you imagine what would happen if I tried to do something I've never done before, instead of letting Ubuntu do what it does best millions of times?

Besides, my Iomega ZIP-250 sometimes corrupts data. Give it a break !!!

---

### Post by Sef on 2008-08-31
> What is this "back-up-data" you speak of ? Isn't that why I'm moving to HH, to have less data backup and more data quickly available ?? Can you imagine what would happen if I tried to do something I've never done before, instead of letting Ubuntu do what it does best millions of times?

Besides, my Iomega ZIP-250 sometimes corrupts data. Give it a break !!!

No upgrade or clean install is 100% guaranteed to be successful.  If you fail to back up your data, you could lose data that you cannot replace.  

If your ZIP-250 sometimes corrupts data, then you need a new device to back up your data to.

---

### Post by theDaveTheRave on 2008-09-01
Hello All.

I've had Wifi connectivity problems over the last couple of days, seems to be related to the laptop running out of power due to a "naff" power cable?

Well I decided that now I've got a hard wired in connection running I would upgrade to Hardy from Gusty.

The process fails at the first hurdle with the error of:

> 
E: The method driver /usr/lib/apt/methods/gpgv could not be found.


so I had a search for the file and it seems that it is a broken link, to this file < /usr/lib/apt/methods/libartsc.so.0.0.0 > this file is no-longer in the repositories . I have used the package manager to re-install the file (and any other file that seems to be a dependant) but nothing seems to work?

I tried renaming the file (so as the system won't find it, and hence won't stumble on the broken link that it contains). I can't download the broken file and install it as it no longer exists in the repositories.

I've done an <fsck> and it threw out a load of errors - which I simply said "yes" when asked to repair them.

Now I am totally stuck, I can't upgrade or anything?

I'm now going to try my last ditch effort and attempt an upgrade via the "rescue" to see if that works, but I don't expect it will.

help please, I'm getting really annoyed!

thanks in advance.

Dave

---

### Post by wpurcell on 2008-09-01
Hello. Hope this is in the correct thread. I just installed Hardy 8.04.1 and the kernel image is 2.6.24-16-generic. Should it not upgrade to -21? Problem solved. I burned another disc and installed from that. Thanks for your time!

---

### Post by dizzler47 on 2008-09-02
hey. ive had ubuntu for a while, but im still new to alot of things. I was upgrading to 8.04, and half way thruogh the installation stage, mycomputer stopped installing. I shut down the computer and rebooted and when i log back in, all i get is a blank screen. can you help me out??

---

### Post by jcsaintpo on 2008-09-02
I installed xubuntu 606 via mini-iso!  In low-memory mode! (old laptop has only 64mb memory!) So had to install the xubuntu-desktop afterwards!

Now i wanted to upgrade to 8.04, but it says "xubuntu-desktop not found, unable to upgrade!"

Is there something I did wrong?
Or is there an other way to upgrade?

---

### Post by WaterKip on 2008-09-03
Just did an upgrade from 6.10 to 8.04.x:

6.10 to 7.04 was a bit tricky:
[https://bugs.launchpad.net/ubuntu/+bug/264181](https://bugs.launchpad.net/ubuntu/+bug/264181)

I started out with a sources.list like this:
```

deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse
deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
```

Run do-release-upgrade to fetch some files from the repo's

Then change your sources.list to reflect this:
```

deb http://archive.ubuntu.com/ubuntu feisty main restricted
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu/ feisty-security main restricted

```

cd /tmp/tmp<some random thing>
./feisty 

And this triggered the actual update, around 4 am I had my 7.04 installation. Fell a sleep and when I woke up I started from 7.04 to 7.10 and from 7.10 to 8.04. Without any problem.

I tried to upgrade another box, from 7.04 to 7.10 and that one just blew up in my face..

---

### Post by emmanuelonas on 2008-09-05
I think the best way to do this is online have a look at this tutorial it may help [http://ubuntu-tutorials.com/2007/10/20/how-to-upgrade-ubuntu-704-to-ubuntu-710-on-ubuntu-server/](http://ubuntu-tutorials.com/2007/10/20/how-to-upgrade-ubuntu-704-to-ubuntu-710-on-ubuntu-server/)

---

### Post by smacfarl on 2008-09-05
Hello all,

I have faithfully been down loading the latest updates with the system updates panel tool on a daily basis.

I was wondering is there an official location were the latest set of updates are talked about in detail on the web.

I just updated a bunch of things, a surprising set, and I wanted to verify each of those updates were necessary. How do I learn more about where the system update tool is getting it's updates from and what the changes in those updates are doing for me. I know you can click on the tabs for each update in the application, but what I would really like is to go somewhere independently of this tool and see the info for myself.

Any suggestions?

---

### Post by masam on 2008-09-05
> **confused57 said:**
> 
It appears to be a DVD writer/hardware incompatiblity with cd images written on the Gigabyte pc.  Downloaded & burned PCLinuxOS_2007 on the Giga machine, would only boot on the Gigabyte pc.  Please ignore the above rantings, I'll delete if the mods deem necessary.

I also noticed that it would not install properly with a DVD drive.
i used an old 8X CDROM and it installed fine though:(
(running it from and older 733 HP)

hope this helps in some way...

---

### Post by Sef on 2008-09-05
> Glad to see most prior posts this Thread show success, not so mine, unfortunately. My Everex gPC has run consistently for the most part with gOS, which is built around the Ubuntu 7.10 core; Update Manager attempted to install 8.04 LTS, unsuccessfully. What do I need to look for w/r/t failures to install of requisite packages for 8.04?

I would burn 8.04 iso and install it that way.  gOS maybe the core, but things are done differently, and therefore, are not 100% compatible with Ubuntu.

---

### Post by fooey on 2008-09-17
i have an old box (600Mhz) running 'Ubuntu 6.06 LTS dapper drake server'. 

my question is .. should i distro-upgrade? i'm using it mainly just as my personal webserver (apache2). there aren't any other services that i run for public use, besides sshd of course. should i go ahead and upgrade is the question?!?

thx

---

### Post by Sef on 2008-09-17
>  have an old box (600Mhz) running 'Ubuntu 6.06 LTS dapper drake server'. 

my question is .. should i distro-upgrade? i'm using it mainly just as my personal webserver (apache2). there aren't any other services that i run for public use, besides sshd of course. should i go ahead and upgrade is the question?!?

If it is doing what you need, then there is no need to upgrade.  The **server version** will be getting **updates until June 2011**.  The desktop version until June 2009.

---

### Post by B4n70 on 2008-09-19
I recently downloaded 8.04, I chose to download the cd as apposed to upgrading 7.10 with the update manager so i would have the disk, but i never knew to use the alternate cd.

Is there any way to update with the disk i have? i foundthis site, but im not sure it applies to 7.10 - 8.04
[http://www.easy-ubuntu-linux.com/ubuntu-upgrade-installcd.html](http://www.easy-ubuntu-linux.com/ubuntu-upgrade-installcd.html)

please could some one advise, Im not keen on setting up my system from scratch.

---

### Post by Partyboi2 on 2008-09-19
> 
I recently downloaded 8.04, I chose to download the cd as apposed to upgrading 7.10 with the update manager so i would have the disk, but i never knew to use the alternate cd.

Is there any way to update with the disk i have? i foundthis site, but im not sure it applies to 7.10 - 8.04
[http://www.easy-ubuntu-linux.com/ubu...installcd.html]("http://www.easy-ubuntu-linux.com/ubuntu-upgrade-installcd.html")

please could some one advise, Im not keen on setting up my system from scratch.


If you have downloaded the alternate cd and burned it as a iso to disk, all you need to do is stick it in the cdrom and a dialog box should come up with the option to upgrade your system. Follow the online instructions. If the dialog box does not come up then in a terminal
```
gksu "sh /cdrom/cdromupgrade"
```

---

### Post by B4n70 on 2008-09-19
The problem is i never downloaded the alternate cd, is it was possible to do an upgrade on the live cd in some way?

---

### Post by Partyboi2 on 2008-09-19
No, you need to use the alternate cd.

---

### Post by dccrens on 2008-09-21
I am running 7.10 and all is good. I have separate partitions for /, /usr, /home, swap, /usr/local , /data, /data2. I have customized many scripts in /etc and /etc/init.d -- things like setting up Virtualbox, custom networking and such.  

My question is if I upgrade to Hardy, will all of these changes be picked up and preserved? Or, will I need to go through the pain of reconfiguring all of these changes? 

I have read through the threads but haven't seen a real definitive answer. Anyone out there have lots of customization such as these and been through the upgrade? Did you have to redo everything by hand?

---

### Post by wattaman on 2008-09-24
Hi!
I'd like to upgrade from 6.06 to 8.04 but don't know how. I'mve just rented a server running on Ubuntu 6.06 and don't know much about linux...
I'm looking at this information I've found:
[I]1.enable the "dapper-updates" repository 
2.install the new "update-manager-core" package - dependencies include python-apt, python-gnupginterface and python2.4-apt. 
3.run "do-release-upgrade" in a terminal window 
4.follow the steps on the terminal window [/I]

It says nothing to me, actually. I know how to connect remotelly and also have (some) access through WebMin, but how exactly I should do this?
Thanks!

---

### Post by Partyboi2 on 2008-09-24
> **wattaman said:**
> Hi!
I'd like to upgrade from 6.06 to 8.04 but don't know how. I'mve just rented a server running on Ubuntu 6.06 and don't know much about linux...
I'm looking at this information I've found:
[I]1.enable the "dapper-updates" repository 
2.install the new "update-manager-core" package - dependencies include python-apt, python-gnupginterface and python2.4-apt. 
3.run "do-release-upgrade" in a terminal window 
4.follow the steps on the terminal window [/I]

It says nothing to me, actually. I know how to connect remotelly and also have (some) access through WebMin, but how exactly I should do this?
Thanks!

In a terminal open up /etc/apt/sources.list
```
sudo nano /etc/apt/sources.list
```
look for these 2 lines and make sure that there is no # at the start of the line.
```
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted 
``` If there is a # infront of them then remove it and save the changes
```
Ctrl+o
enter
Ctrl+x

```
then update any changes you made
```
sudo apt-get update
```
then install update-manager-core
```
sudo apt-get install update-manager-core 
```
then after it has installed the update manager core package
```
sudo do-release-upgrade
```

---

### Post by wattaman on 2008-09-25
Thank you, Partyboy, but I don't have those 2 lines in that file:
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
Should I add them or modify the existing ones:
That's the sources.list I have:
> # 
# deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ hardy main restricted


#deb cdrom:[Ubuntu-Server 6.06 _Dapper Drake_ - Release i386 (20060531)]/ hardy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe

Thanks again!

---

### Post by Partyboi2 on 2008-09-25
> **wattaman said:**
> Thank you, Partyboy, but I don't have those 2 lines in that file:

Should I add them or modify the existing ones:
That's the sources.list I have:


Thanks again!
According to your sources.list you are already using the hardy repo's.
Can you paste the output to
```
lsb_release -d
```

---

### Post by wattaman on 2008-09-25
I did but it says *Ubuntu 6.06.2 LTS*
So I suppose I'm using Ubuntu 6.06.2 :)

---

### Post by SSVegito888 on 2008-09-25
I installed Hardy 8.04 a couple of weeks ago.

Will the update manager automatically upgrade my system to 8.04.1?


Also, is there a way to find out which version of Ubuntu I am using?


Thanks,

SSVegito888

---

### Post by Partyboi2 on 2008-09-25
> **wattaman said:**
> Thank you, Partyboy, but I don't have those 2 lines in that file:

Should I add them or modify the existing ones:
That's the sources.list I have:


Thanks again!
Looks like your system has a difference of an opinion.  What kernel version are you using?
```
uname -a
```

---

### Post by Partyboi2 on 2008-09-25
> **SSVegito888 said:**
> I installed Hardy 8.04 a couple of weeks ago.

Will the update manager automatically upgrade my system to 8.04.1?


Also, is there a way to find out which version of Ubuntu I am using?


Thanks,

SSVegito888
If you are up to date with all your updates you should be running 8.0.4.1 to check open a terminal (Applications>Accessories>Terminal) and type
```
lsb_release -a
``` it should say 
> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy 

---

### Post by spike_naples on 2008-09-25
Im starting to get very frustrated with Ubuntu. I am very new to this and I ordered my cd a few weeks back. When I finally decided to get rid of my windows life and choose "Linux for Human Beings" I was shocked by a stalled installation.

I got my 8.04 LTS cd. My PC is a P4 2.8Ghz with 1Gb of Ram. I have an NVIDIA FX 5500 card and 2 40gb Hardrives.

Whenever I install (I chose all options already) the program just hangs. It shows a progress bar and after about 15% completion it just totally freezes.

Its a very frustrating initial Ubuntu experience form me. Ive checked the cd for checksum errors and it reported as fine. Ive downloaded a new Ubuntu program and still the same thing happens. Ive unistalled so many programs just to make way for the coming of Ubuntu and still the same thing happens.

I'm starting to hate this and after hearing all the good raves about Ubuntu this is what I get in return. Prior to this Ive even been preaching that this is THE WINDOWS KILLER! and yes in a twisted way, it left my windows dead and now I'm running on an almost "naked" setup.

I'm willing to give it one more go and I hope someone out there can help me. Today is my birthday and I'm stuck with reviving a PC stripped of alot of essential software for Ubuntu.

Should I format my drives to give Ubuntu a chance or should I just forget it and stick to WindowsXP?

---

### Post by Sef on 2008-09-26
>  Should I format my drives to give Ubuntu a chance or should I just forget it and stick to WindowsXP?I would recommend dual booting at first.   There are two ways to do it.

1) Read [Psychocats]("http://www.psychocats.net/ubuntu/").   The live cd is used for dual booting.

2) If that fails, then maybe you need to use the alternate cd.  Read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").  Some hardware just be installed by the alternate CD.

---

### Post by ilker on 2008-09-27
hi I heave  a problem. I deleted desktop.ini but now I cannot open ubuntu 8.04 I can only open xp please help

---

### Post by Sef on 2008-09-27
Does it open in safe mode?  (It's under options - bottom left at log in screen.)

---

### Post by jack frost on 2008-09-29
> **Sef said:**
> 1) Hardy Heron Users: If your upgrades are current, then you are running 8.04.1.  If they are not current, then just install all the upgrades.

2) Dapper Drake Users: Automatic Upgrade through the Upgrade Manager.

3) Gutsy Gibbon Users: Upgrade through the Upgrade Manager or [install Hardy Heron]("http://www.ubuntu.com/getubuntu/download") by downloading 8.04.01, burning the iso and installing it.

4) Users of other versions of Ubuntu: Upgrade by [installing Hardy Heron]("http://www.ubuntu.com/getubuntu/download") by downloading 8.04.01, burning the iso and installing it.

5) For more information, read [Ubuntu 8.04.1 LTS released]("https://lists.ubuntu.com/archives/ubuntu-announce/2008-July/000112.html").

6) **Back up** your data before upgrading, there are no 100% guarantees that all will go well.
this may have already been asked.. I am running 8.04.1.. when 8.10 comes out and I do upgrade.. will it erase all my settings,like for virtualbox etc.  I did read that you can upgrade fine if you have the latest version installed.  Just wanted to get clarification etc.  thanks.

---

### Post by Sef on 2008-09-29
> this may have already been asked.. I am running 8.04.1.. when 8.10 comes out and I do upgrade.. will it erase all my settings,like for virtualbox etc. I did read that you can upgrade fine if you have the latest version installed. Just wanted to get clarification etc. thanks.

Ideally, you should keep all your settings if you upgrade.  However, there are problems sometimes, so **back up** your data before you upgrade.

---

### Post by SSVegito888 on 2008-09-30
I have a hypothetical question.


In the future, when I upgrade to a new version of Ubuntu, say 8.10.  Will I need to delete the hardy repos from my sources.list file and re-add the sources I've added manually, such as medibuntu?


Thanks,

SSVegito888

---

### Post by Sef on 2008-09-30
> n the future, when I upgrade to a new version of Ubuntu, say 8.10. Will I need to delete the hardy repos from my sources.list file and re-add the sources I've added manually, such as medibuntu?


If you do it through Ubuntu's updater, no -  though it would be best to delete any nonstock hardy heron repositories.

---

### Post by kline on 2008-10-03
A few hours ago in a different post, I asked a slightly off-top question that was related to my question[s] about my current release of 6.06.

Nutshell is that a year++ ago a power-failure cost me some icons and other things related to keeping my 6.06 LTS current.  Since then, I've kept my system current via synaptic.  I am as up-to-date as I *can* be with 6.06. I was told the 8.04 is yet another LTS version.  I would like to upgrade over the net if I can.  (I have upgraded this way before, but with some trouble.)  

So, I'll start a new post here and ask if there is a way of upgrading from 6.06LTS to 8.04LTS via the net.  Is there a command-line method of drawing 8.04 across and upgrading?  Or would some GUI program be the better [safer!] way to go??

Thanks for any insights.

---

### Post by Sef on 2008-10-03
> So, I'll start a new post here and ask if there is a way of upgrading from 6.06LTS to 8.04LTS via the net. Is there a command-line method of drawing 8.04 across and upgrading? Or would some GUI program be the better [safer!] way to go??


Read the [first post]("http://ubuntuforums.org/showthread.php?t=849915") in this thread.

From it:

> 2) Dapper Drake Users: Automatic Upgrade through the Upgrade Manager.


Always **back up** your data before updating or installing.

---

### Post by kline on 2008-10-04
> **Sef said:**
> Read the [first post]("http://ubuntuforums.org/showthread.php?t=849915") in this thread.

From it:



Always **back up** your data before updating or installing.

A sad experience ' 99 taught me to back up all my servers at least daily; that wasn't the problem.  I couldn't find "Upgrade Manager" and it wasn't until I did a 

% find .... |xargs egrep|egrep ... 

that I realized the string was in System -> Administration.  Then, several hours later, I rebooted and found X11 broken.  (I just installed a widescreen minotor.)  

% x -configure 

created /root/xorg/new, and moving that to /etc/X11 got me the rest of the way.  A few miscellaneous things to fix.  Thanks for your help.

---

### Post by Porpoise on 2008-10-12
Well, having tried, several times now, to upgrade my Acer Travelmate 630 to 8.04 (from 7.10), I've finally come to the conclusion that 8.04 doesn't work on this laptop.

7.10 was working great but 8.04 just doesn't want to know... Sometimes it'll boot then it just locks up, other times, it just won't boot and Xserver will crash - go back to 7.10 and everything is fine again.

I've tried all routes - upgrading from 7.10, installing fresh from Live CD and installing fresh from Alternate CD - it doesn't matter which route I take - no working 8.10!!??!!

I give up!

---

### Post by Sef on 2008-10-20
> Well, having tried, several times now, to upgrade my Acer Travelmate 630 to 8.04 (from 7.10), I've finally come to the conclusion that 8.04 doesn't work on this laptop.

7.10 was working great but 8.04 just doesn't want to know... Sometimes it'll boot then it just locks up, other times, it just won't boot and Xserver will crash - go back to 7.10 and everything is fine again.

I've tried all routes - upgrading from 7.10, installing fresh from Live CD and installing fresh from Alternate CD - it doesn't matter which route I take - no working 8.10!!??!!Sometimes a version just does not work with certain hardware, whereas another version will.  I would run the Ibex Live CD once it is out a couple of weeks.  Run the Live CD for a while to make sure that all is ok between it and your computer.

---

### Post by Naguz on 2008-10-20
This update should never have been released in its current state. Many nvidia owners have experienced huge problems, and although there are several different fixes and tips to work around this, many Nvidia users  will meet a 480xsomething resolution when restarting after this update. Drivers are not availible in the restricted drivers app for me, and uninstalling and reinstalling the nvidia drivers does not help one bit. In addition, random freezes would occur at least once an hour, forcing me to flipping the restart switch. On restart it would hang once early in the booting process, forcing me to restart again, and then it would freeze again after logging in, forcing me to reboot it for the third time. THEN it would boot normally. Uninstalled the latest kernel image, and now it's luckily only the "will not boot after sleep"-problem.

On my laptop, i allowed the updater to rewrite my menu.lst-file. For some reason, it changed all entries from (hd0,3)   to (hd0,1), resulting in an unbootable system. Editing the boot options in grub is not something everyone knows how to do, and people might get stuck on an unbootable system. That, plus the numerous people with nvidia cards and problems, make me wonder how on earth this update got to be released. It should very clearly not have left beta stage yet.

Upgrading from hardy 8.04. The nvidia card is 8800GT from some manufacturer.

---

### Post by Sef on 2008-10-20
> This update should never have been released in its current state. Many nvidia owners have experienced huge problems, and although there are several different fixes and tips to work around this, many Nvidia users will meet a 480xsomething resolution when restarting after this update.

Some NVidia owners have had major problems.   I had absolutely no problems.  Albeit, I did a clean install.  Part of the problem is that NVidia does not open source their drivers, so there will be more problems with them than with drivers that are opensource.

---

### Post by klauszlion on 2008-10-29
I want to upgrade from 7.04 to 8.04 from cd

---

### Post by Partyboi2 on 2008-10-29
> **klauszlion said:**
> I want to upgrade from 7.04 to 8.04 from cd
You can not go from 7.04 to 8.04 direct you will need to upgrade to 7.10 then to 8.04. So you will need to download the 7.10 (Gusty) alternate cd from [[COLOR=Blue]here [/COLOR]]("http://releases.ubuntu.com/gutsy/")and upgrade then download the [[COLOR=Blue]8.04 alternate cd[/COLOR]]("http://releases.ubuntu.com/hardy/") and upgrade.
[https://help.ubuntu.com/community/GutsyUpgrades#Upgrading%20using%20the%20alternate%20CD/DVD]("https://help.ubuntu.com/community/GutsyUpgrades#Upgrading%20using%20the%20alternate%20CD/DVD")

---

### Post by spike_naples on 2009-03-23
Got it running for almost 3 months now. I had a screwed mobo...

I feel like an idiot for cursing Ubuntu then...

My apologies to those I affected.

---

### Post by slakkie on 2009-08-04
Maybe put EOLupgrades wiki page also in the OP, if people want to upgrade from older versions..

---

### Post by itvn2007 on 2010-05-06
Hi all !
 
Tôi &#273;ang mu&#7889;n upgrade t&#432; Ubuntu server version 9.10 lên 10.04 thì ph&#7843;i làm nh&#7919;ng gì?
Ai bi&#7871;t  xin chi gium nhé ! :)
 
Thank you !

---

