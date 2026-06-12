---
title: "Upgrade vs Clean Install"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by andperry on 2012-05-04
I'm in the process of upgrading my systems from 11.10 to 12.04. Is the upgrade process just as good as doing a clean install on to a blank partition? Being new to Linux, I suppose my thinking must be greatly  influenced by Windows - I would always do a clean install there, as Windows is so bad at accumulating junk!

What does anyone think?

---

### Post by *^kyfds( on 2012-05-04
it only really matters if you have lots of files on your ubuntu partition.
 
if you do, it's not really worth doing a clean install as ubuntu doesen't really store many temporary files, unlike windows.
 
if you've accumulated lots of software you don't need, then yes, you might want to do a clean install, but you'll have to back up all the things you want to keep.

---

### Post by holycow131415 on 2012-05-04
People usually say a clean install is better. Upgrades can always go wrong, or make the computer sluggish after the upgrade is complete.

---

### Post by Frogs Hair on 2012-05-04
I don't  upgrade (my choice) , but 11.10 to 12.04 has gone well for some and not so well for others . disable any  PPAS if you have them.

---

### Post by mörgæs on 2012-05-04
Why do you want to leave 11.10?

---

### Post by zombifier25 on 2012-05-04
> **mörgæs said:**
> Why do you want to leave 11.10?

I believe the answer is as obvious as heck :popcorn:

---

### Post by grahammechanical on 2012-05-04
Look around the sections of these forums. See how many posts begin with "I just upgraded ...."

There is no doubt that we get those posts where things go wrong and we do not get the posts where things go right. But it should make you think.

I shared in testing the upgrade path for Ubuntu amd64 and i386 before 12.04 was released. I tested going from 10.04 to 12.04 and 11.10 to 12.04. I did not see any problems but then again I was installing default 10.04 and default 11.10 to run these tests.

How many of us are using a plain. basic, default Ubuntu? Problems come when we have heavily modified the OS. In my opinion.

I have 11.10 with a separate /home partition. I have been using a development version of 12.04 daily since November for testing purposes.

Next week I am going to change my 11.10 to 12.04 but by a fresh install. I will use this 12.04 as a standby OS will I run a development 12.10 every day.

I would not say that an upgrade is as good as a fresh install.

Regards.

---

### Post by tweaked on 2012-05-04
I've never gotten an upgrade to work out of 6 tries. That is the very reason I am here this morning.

---

### Post by *^kyfds( on 2012-05-04
> **tweaked said:**
> I've never gotten an upgrade to work out of 6 tries. That is the very reason I am here this morning.


really?

6 tries? thats highly unusual. I've talked with a number of my mates upgrading to 12.04 and they've had no problems...

:-k

---

### Post by fooman on 2012-05-04
although i am a firm believer in fresh install vs. the upgrade.... i have successfully upgraded 3 computers in the last 2 days from 11.10 to 12.04.

there was only one hiccup that i encountered,  and it happened to me on all 3 occasions...see my post (# eight) in this thread to explain:

[http://ubuntuforums.org/showthread.php?t=1973125](http://ubuntuforums.org/showthread.php?t=1973125)

btw,  all three computers were using some 3rd party PPA's which i *did not* remove or disable before upgrading.  as the upgrade began,  i was prompted that those PPA's would be removed...i gave the ok and the upgrade proceeded.

so besides the "freezing" episode explained in that other thread...the update worked perfectly and all 3 are humming along with no problems at all.  :p

---

### Post by mcblades on 2012-05-04
I tried to upgrade using a usb stick.  Install hung up after downloading packages and I had to do a clean install (off the same flash drive but this time successfully).

dejadup/rsync is your friend!

I strongly recommend you BACK UP before trying an upgrade.

Also, if you print via CUPS to a postscript printer I would check it works on 12.04 before upgrading.  I have had loads of "fun" trying to work out why CUPS was crashing my konica-minolta magicolor 4750dn.  In the end I have a virtual box with oneiric and cups which is running the print server until this is sorted out.

I seriously considered going back to oneiric but 12.04 fixed a network card issue and improved my wacom bamboo to the point of usability so it's swings and roundabouts.


good luck

---

### Post by DGINSD on 2012-05-04
I vote fresh install, a bit more work, but I like knowing my set up is "clean". I keep a septate home partition and perform a spring cleaning before the install.

Make a list of your installed packages and determine the ones you still really need (mostly names as versions change). Make a copy of your fstab modifications. Make a list of added repositories. This should help get the fresh install running close to the old

---

### Post by unibroker on 2012-05-04
> **holycow131415 said:**
> People usually say a clean install is better. Upgrades can always go wrong, or make the computer sluggish after the upgrade is complete.

I am new to Ubuntu as of November and originally had 11.10.  I started learning the command line shortly after and stumbled upon the update/upgrade commands one night.  Dumb luck was on my side that night because other than some "test page" artifacts on boot up I had no trouble that night and since.

BTW, those artifacts have cleared up (probably in the testing phase) as the first thing I do in the morning when I boot up is hit "Update".

---

### Post by ratcheer on 2012-05-04
I have done it both ways, maybe even more ways than that. My strong recommendation is to back up your home directory. Clean out your web browser's cache before backing up - it can contain hundreds of MB of crap. Then do a clean install. Then restore your home directory from the backup. You will have to install many of your applications, but their settings will remain intact.

Tim

---

### Post by jonedney on 2012-05-04
I upgraded 11.10 to 12.04 and everything went very smooth (took roughly 2 hours).  I never upgrade Windows, always clean install, just from past experiences.

Jon

---

### Post by buzzingrobot on 2012-05-06
Just as an aside, I followed the 12.04 betas, installing a few times from CD with no problems at all.  When the release hit the street, I decided to do a clean install.  That was trouble.  I have never been able to get a 12.04 release CD to boot, primary or alternate.  I see a quick flash of a message about running a command list and something telling me I need to load a kernel first.  Then, the machine locks up. 

With A USB drive, the boot stops before grub runs. This seems to be due to bad blood between my Nvidia card and the kernels in the install image (apparently, all the 3.2 and 3.3 kernels).

The only way I was able to install the release 12.04 was to install 11.10 and dist-upgrade from there.  Understandably, it went quite smoothly.

---

### Post by Sef on 2012-05-06
Usually I have done clean installs, but for 12.04, I did an upgrade through the upgrade button. Everything went fine.

> The only way I was able to install the release 12.04 was to install 11.10 and dist-upgrade from there. Understandably, it went quite smoothly.

Dist-upgrades are not recommended now. If that was the only way you could upgrade, and it was successful, then I am glad it worked for you.

---

### Post by buzzingrobot on 2012-05-07
> **Sef said:**
> Usually I have done clean installs, but for 12.04, I did an upgrade through the upgrade button. Everything went fine.



Dist-upgrades are not recommended now..


Not to be a contrarian, but who is not recommending upgrading? Ubuntu.com provides clear instructions and Update Manager goes out of its way to call a user's attention to it.

---

### Post by colin.p on 2012-05-07
Just for grins and giggles, I did a clean install of 12.04 from 10.04 and allowed the installer to keep my settings from 10.04 (I have a separate "home" partition). I had of course backed up "home" before hand. Everything went reasonably smooth except the installer put grub somewhere in one of the partitions, just not in the boot partition. After getting that sorted out, I found that HUD would not display anything.
A little sleuthing and I found a post that said to remove all the hidden folders in "home", then HUD started working. Then I just put back whatever hidden folders I need before I install any software. Oh yes, I also got rid of any old PPA's that would have caused issues I'm sure.
I think next time I will allow the installer to wipe out all partitions, as well as home, since with backups, I would just bring over whatever and whenever I needed.
So I vote for a clean install, even though previous to lucid, I had updated from intrepid to jaunty to karmic with no real issues.

---

### Post by coldjeanz on 2012-05-07
I didn't want to do a clean install so I just backed up my important files and went ahead and did the upgrade. Everything went smoothly, took less than 2 hours. I was worried too but I have a habit of taking risks and then dealing with the consequences after :biggrin:

I think it really just depends on your setup, I read that people with a certain graphics card/driver had a horrible time upgrading but I read that mine shouldn't have any problems.

---

### Post by buzzingrobot on 2012-05-07
> **colin.p said:**
> J
...So I vote for a clean install, even though previous to lucid, I had updated from intrepid to jaunty to karmic with no real issues.

Yep, so would I under normal circumstances, meaning that the install image boots on my hardware.

Even when Ubuntu developers test the update routine. there's no way they can predict or duplicate what's on machines "in the wild".

I did my 11.10 install on newly partitioned and formatted drives, grabbed the updates immediately after the reboot, and then did the dist-upgrade. It was a pristine system.

---

### Post by manoyth on 2012-05-14
I have thought to make a clean install but without formatting. I will choose "Something else" in the installer. I 'll mark the partition on which I have Ubuntu 11.10 as / (mount point) without choosing format. It will delete everything except for /home folder. What do you think? Should I try firstly to make an upgrade?

---

### Post by Wheel on 2012-05-14
I am preparing to migrate from 11.10 to 12.04.
9.10 was my first flavor of Ubuntu.
I have upgraded to each version since.
Each upgrade was quickly followed by a clean install as each upgrade cause aggravating problems which I could not solve.
My skill level is a *bit* lower than many who prowl these forums <cough>.
I have already burned my copy of 12.04, although I will try an upgrade first.
We shall see.
Whatever you decide on, don't forget to back up first.

---

### Post by d4m1r on 2012-05-14
I've only upgraded once (11.04 -> 11.10) and minus a few quirks, everything was working fine.....I'd say the **proper way** to do is a clean install, but it's more time consuming, so doing an upgrade instead is a shortcut.

---

### Post by czgirb on 2012-05-14
> **mörgæs said:**
> Why do you want to leave 11.10?

Would you mind to tell me, what should we do, if we wish to stay with our current OS, which will be not supported again?
Currently, I'm using 10.04 Lucid Lynx and I think it's a rock solid

---

### Post by holycow131415 on 2012-05-17
> **czgirb said:**
> Would you mind to tell me, what should we do, if we wish to stay with our current OS, which will be not supported again?
Currently, I'm using 10.04 Lucid Lynx and I think it's a rock solid

You can keep using it as long as you want. Its just that you wont get any updates. If you like the way the UI is, I'd suggest switching over to Linux Mint, as they are developing the DE Cinnamon, whose goal is to operate and feel like a modern gnome 2.

---

### Post by mörgæs on 2012-05-17
> **czgirb said:**
> Would you mind to tell me, what should we do, if we wish to stay with our current OS, which will be not supported again?
Currently, I'm using 10.04 Lucid Lynx and I think it's a rock solid

What I meant was that people should think twice before switching to a brand-new (meaning buggy) release. If there is no particular reason to move then waiting a couple of months is a good idea - or just skip every other release.

Don't use an unsupported release, though. When 10.04 is out of support in one year from now you could try Mint, Xubuntu or Debian stable.

---

### Post by Peripheral Visionary on 2012-05-17
As long as you don't need a lot of new software, [COLOR=DarkOrange]**upgrading is not mandatory!**[/COLOR] Use 10.04 as long as you wish, only be aware that security updates to Lucid will end in April of next year.

By the time support for Lucid ends, Precise will be every bit as rock-solid as Lucid is now.  I don't recommend upgrading right away to the latest release unless you're willing to accept a little risk and are willing to learn how to fix or work around the ordinary bugs that are part of the "cutting edge" latest editions.

---

### Post by rgreener25 on 2012-05-17
Hmm i have never managed to successfully update what i would do is download ubuntu 12.04 lts and backup your files, do a clean install, copy them back across and then follow the lts route, updating every 2 years unless you need cutting edge software in which case follow the standard route, updating every 6 months

NOTE When i say updating i mean by backing up and doing a clean install

---

### Post by goaliedude3919 on 2012-05-23
The first time I did an upgrade, there were a few things that didn't go quite right, but they weren't obvious and ended up causing major problems later on. However, I hate having to reinstall all my software and transfer files when doing a clean install, so I decided to upgrade from 11.10 to 12.04. So far I only have one problem and I'm slowly getting it worked out.

---

### Post by czgirb on 2012-05-23
> **rgreener25 said:**
> Hmm i have never managed to successfully update what i would do is download ubuntu 12.04 lts and backup your files, do a clean install, copy them back across and then follow the lts route, updating every 2 years unless you need cutting edge software in which case follow the standard route, updating every 6 months

NOTE When i say updating i mean by backing up and doing a clean install

Currently, my CQ40 ... Vista, 2GB-RAM, 320GB-HDD ... the partition are as follow:
* C drive ... 100GB (OS and Software installed)
* D drive ... the remaining (Data)
I use to separate OS (incld. installed software) and Data ... cos, I wish, if OS re-installation required, it will not effect my data.

In Ubuntu, I tried to googling, but find none are described partition details ... or maybe my computer's knowledge is un-sufficient to understand the term used.
Please guide me ... and sharing your partition suggestion for my 320GB-HDD.
Thank you.

---

### Post by Wheel on 2012-05-23
My recent upgrade attempt from 11.10 to 12.04 failed.  The system simply froze up about one minute into the process.  The download worked fine, but that was it.
In 4 prior clean installs -- following successful but trouble-plagued upgrades -- each was done to a clean partition.  All went well.
This time, I clean installed without removing the partial (failed) upgrade and it went very well.
I'm stubborn; I'll try an upgrade again when 12.10 comes around, but I'll also burn the .iso first.

---

### Post by Hotshot5000 on 2012-05-26
Are you sure after starting updating and freezing that you looked into the terminal? I had the same problem and it seems it's some program in command line

---

### Post by madjr on 2012-05-26
always better to try clean install:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/876146](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/876146)

---

### Post by Wheel on 2012-05-26
> **Hotshot5000 said:**
> Are you sure after starting updating and freezing that you looked into the terminal? I had the same problem and it seems it's some program in command line
I don't see how that would've been the case with me this time.  I wasn't using terminal to upgrade.  Everything was closed, and I simply opened Update manager and clicked the upgrade button.
I will keep that in mind for next time as I'm likely going to use terminal to attempt the upgrade to 12.10

---

### Post by kagashe on 2012-05-26
Hi everyone,

I am Ubuntu user since version 5.04 and use to have number of partitions on my personal machines and never doing any upgrade.

Since Jan 2010 I am using an office Laptop and installed 10.04 in dual boot with Windows XP. Initially I used Windows for opening .dwg .dwf files. Then I had a net banking account which necessarily required Internet Explorer with Microsoft Virtual Machine.

In order to use Ubuntu and Windows simultaneously I installed Windows on Virtual Box.

Besides Windows C:/ and Ubuntu 10.04 on ext4 this Laptop had large NTFS E:/ drive but no partition to install Ubuntu 12.04.

Since the large NTFS partition was being used to store files mostly from Ubuntu 10.04 I had to defrag it using Windows.

Then I tried to resize the NTFS partition on Ubuntu 10.04 but the operation failed and also made the partition unmountable. I used testdisk on Ubuntu 10.04 to correct it and mount it.

Then I decided to try the gparted on Ubuntu 12.04 startup disk and used the check function on the NTFS partition. The error log advised me to run chkdsk using /f option on Windows to correct the errors and reboot twice on Windows.

Finally I could resize the NTFS partition using gparted on Ubuntu 12.04 startup disk and install Ubuntu 12.04 on another ext4 partition.

I was already using latest Thunderbird (from PPA) on Ubuntu 10.04. I copied the .thunderbird folder on Ubuntu 12.04 and all mails and address books could be accessed.

I have installed Virtual Box just now on Ubuntu 12.04 and same Windows hard disk is running well.

I did not try upgrade since I was using LibreOffice, Firefox, Thunderbird from PPAs.

Sorry for the long post but I am visiting ubuntuforums after long time.

Kamalakar

---

### Post by Ashish Mishra on 2012-05-30
I upgraded from 10.04 to 12.04 and my netbook is working perfectly fine. Although contrary to what a friend had suggested before upgrading, my netbook is getting more heated with 12.04.

---

### Post by terrykiwi83 on 2012-05-30
my own experience with upgrading from 11.04 x64 to 12.04 x64 was smooth, and my system runs fast and responsive. So pretty positive!

---

