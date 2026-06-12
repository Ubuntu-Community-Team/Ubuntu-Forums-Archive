---
title: "[Ubuntu] Trouble upgrading from 12.04 to 14.04.1 lts"
date: 2014-08-05
forum: New to Ubuntu
---

### Post by dansemacabre95000 on 2014-08-05
I am still relatively a newbie working with Ubuntu, and my current setup is having issues. I am currently running Ubuntu 12.04.5 lts, 32-bit, a dual-boot system with Windows XP 64 bit, 2.9 GiB, Intel Core 2, GeForce 9600, 577.8 GB. My system often (at least 2-3 times a day) crashes and restarts. When it crashes, the mouse and the keyboard do not work, and if audio is playing it will skip for about 30 secs until the computer restarts. I have been working on and off on the crashing problem for a while, with little success.

In any case, at this point I would prefer to just upgrade to 14.04.1 lts to see if that helps. The update is not showing up in the Update manager, which is set to let me know of the latest lts version. So I have been trying to upgrade via Terminal. Running sudo do-release-upgrade just brings back a message that there is no new release. But when I run: 

    > sudo apt-get update
    sudo apt-get dist-upgrade
    sudo do-release-upgrade -d
    

the upgrade starts, but an error occurs. Here is the last bit of what the terminal says:

    > Ign [http://archive.canonical.com](http://archive.canonical.com) trusty-proposed/partner Translation-en
    ...
    Fetched 0 B in 0s (0 B/s)
    Error during update
    A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.
    W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/trusty-backports/partner/source/Sources](http://archive.canonical.com/ubuntu/dists/trusty-backports/partner/source/Sources)
    ...
    Restoring original system state
    Aborting
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Building data structures... Done
    === Command detached from window (Mon Aug  4 12:28:37 2014) ===
    === Command terminated with exit status 1 (Mon Aug  4 12:28:37 2014) ===

What would be the best next step after this? I also tried sudo do-release-upgrade -p, with pretty much the same results. My internet connection is fine while browsing for solutions to the problem, so how could it be a network problem? I have tried the above command a few times over the past couple of days. Also, for the crashing problem, I also wonder if part of the problem is that my Ubuntu system is 32 bit and my Windows XP system is 64bit. Is there a way to ensure that I update to Ubuntu 14.04.1 64bit without having to do a clean install? Thanks in advance!

---

### Post by whitesmith on 2014-08-05
With problems like these I would recommend a new installation instead of an upgrade. This is usually the safer path anyway. Upgrading often leaves behind a bit of the old OS that later on causes problems with the new version. Others may not agree, but my experience with upgrades has been uniformly disappointing.

---

### Post by grahammechanical on 2014-08-05
Please look at this wiki page and note this comment

> [COLOR=#333333][FONT=Ubuntu]To upgrade to a newer release, from a terminal prompt enter:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]```
do-release-upgrade
```[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]It is also possible to use [FONT=inherit]*do-release-upgrade*[/FONT] to upgrade to a development version of Ubuntu. To accomplish this use the [FONT=inherit]*-d*[/FONT] switch:[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=monospace]```
do-release-upgrade -d
```[/FONT]
[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit][FONT=inherit][FONT=inherit]Upgrading to a development release is [FONT=inherit]*not*[/FONT] recommended for production environments.[/FONT]
[/FONT][/FONT][/FONT]
[/FONT][/COLOR]

[https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html](https://help.ubuntu.com/12.04/serverguide/installing-upgrading.html)

Why are you using the -d switch? It is a big jump from 12.04 to 14.04 but by using the -d switch you are trying to go to Utopic Unicorn (14.10) and that is still very much under development.

We can upgrade from one LTS to the next LTS such as 12.04 to 14.04 but we cannot get Utopic Unicorn (14.10) from 12.04 only from 14.04. That is why you are getting that error.

Regards,

---

### Post by dansemacabre95000 on 2014-08-05
@grahammechanical, I tried using the -d switch because of others having this same problem (wanting to upgrade from 12.04 to 14.04 lts), but the regular sudo do-release-upgrade not working. So that was one suggested solution I read, I think in the askUbuntu Stack Exchange. But what you are saying makes sense, since I know you either have to upgrade sequentially or go from lts to lts. I was just confused as to why it's worked for a couple of other people (according to their comments), but not for me.

@whitesmith, so you would suggest just downloading an ISO version to a CD and doing a clean installation?

---

### Post by Impavidus on 2014-08-06
In my experience release upgrades usually work (7 successes in 7 tries). They don't solve problems though, so if you already have a problem you can better install cleanly than upgrade. You can't upgrade from 32 bit to 64 bit, this change always requires a clean install. Dual booting 32 bit Ubuntu and 64 bit Windows is no problem, but 64 bit Ubuntu would be better anyway. Are you positive you have 2.9GiB memory? My old non-PAE 32 bit 12.04 install has always reported 2.9GiB, both before and after upgrading my memory from 3 to 8GiB. 2.9GiB is the maximum supported by non-PAE 32 bit. I now run 64 bit 14.04 (clean install), but keep the old system as backup.

Download the 14.04 64 bit .iso, burn it to a dvd or usb drive and reinstall. You can keep your old files and settings (for as far as they still apply) in place, but best to make backups nonetheless.

---

### Post by rvboutin on 2014-09-05
Hi,
From my personal experience I have mixed results with upgrade (about 25% success rate). I have several computers running Ubuntu since version 10.10, I was initially not running the LTS version, I am since version 12.04. By 25% success rate I mean, no problem at all or no major problem on reboot once the upgrade has complete. For the 75% failure, I mean: black screen on reboot, unable to boot even in terminal, or repeated error and crash on subsequent use the following days after upgrade (until I got fed-up and do a clean install). So, as you are already experiencing issue with your system I would definitely follow the previous advices and go for a clean install.
Also, you should check that your hardware and more particularly your graphic card has drivers that are supported by the new LTS version 14.04.
Why don't you use a 64bit version? I run it on a PC with fairly similar spec than yours with no problem at all, and that would allow you to use more than 3Gb of RAM if you have more or if you want to upgrade your RAM.
Hope this helps!
Cheers,
Rv

---

### Post by dibuntux on 2014-09-16
Hi, to all that scare you and suggest to make a new installation over an upgrade: yes, takes much longer, but in the end you get exactly YOUR system, not a new one.

I had problem with the upgrade that did not start becouse some sources could not be upgraded. I just removed mono libs and all programs connected, like banshee, and could run the upgrade. Takes half a day, and many times ask for confirmation of keeping your config files.

But then, EVERYTHING was back in place. I use Gnome Flash back, that was automatically selected (the desktop as it is intended to be), and all was where I left it.
I have a RAID setup with 2 mirror disk and one RAID0, no problems. MY old usb Mustek scanner, with difficult setup, was working, my old webcam too, VirtualBox was ok, just had to reinstall Ext pack for the new version. Oracle Java and flash are ok. Just had a bit of a problem with Skype...but hei, it is a M$oft program, what can you expect?

I've been upgrading my AMD64 machine since Ubuntu 7.04...always worted!
Thank you Ubuntu!

---

### Post by riverguy99 on 2014-09-18
Maybe not the most popular solution to your problem, but ask yourself why you want to upgrade to 14.04!  14.04 users report lots of problems, most of which I stressed over when I did installed 14.04 (clean install) on three machines that were running 12.04 without a hitch.  I finally ended up re-installing 12.04 on all of them and am back to being able to work all day with no crashes, blank screens, error messages, and my dual displays worked out of the box (never could get them working with 14.04).

Just a thought . . .

---

### Post by Michael_McKenney on 2014-09-18
12.04 to 14.04 is a huge jump.  I would go at 13.x first and get it stable before jumping to 14.x.

---

### Post by blackbird34 on 2014-09-18
No  Michael, you don't undeerstand:  12.04 to 14.04 is the standard LTS to LTS upgrade and is well supported and documented by Canonical. all releases in between are short-term support.

---

### Post by riverguy99 on 2014-09-18
> **Michael_McKenney said:**
> 12.04 to 14.04 is a huge jump.  I would go at 13.x first and get it stable before jumping to 14.x.

If you really want to "upgrade" to 14.04, a clean install is the best way to go.  Especially if you like the notion of "clean," as in no glitches from pieces of the old OS remaining to conflict with the new one.  But then, if 12.04 is working well for you now, why move to 14.04?  On this forum are many issues with 14.04 that were simply not issues with 12.04.  12.04 is very stable and capable.

---

### Post by Michael_McKenney on 2014-09-18
I am old school on upgrades.  I have been doing it since 1982.  I remember the first Linux flavors, DOS, Windows 1.x beta tester, IBM OS/2 and many other OS installs.  It might be a common upgrade but issues can happen.  Going to a earlier middle revision first some times gets past the problems.  I have installed firmware upgrades that work better jumping no more than 2 revisions at a time.  It might work in 99% of the tries but this could be the 1%.  It is just an option that works.  From what I read about 14.04 is about the upgrade issues it has.  I downloaded 14.04.1 Live CD last night to test server grade hardware with it.  14.04 works fine on my Intel DG33TL mini board.  It would not take long to get from 12.04 to 13.x and then go to 14.04.  I usually kick off the dist-install at night and go to bed.

---

### Post by Impavidus on 2014-09-18
The only upgrade available from 12.04 is to 14.04. The intervening releases (12.10, 13.04 and 13.10) are all obsolete. But 14.04 is solid. I installed it 4 days after release and never had problems, and neither had most other users. Ever thought about how many Ubuntu users never posted problems with 14.04 on this forum because they have none? Many more than those who have posted problems. 14.04 even solved some little issues I had on 12.04 that I never really bothered troubleshooting.

So the upgrade from 12.04 to 14.04 is officially available, tested and pretty reliable. But the original poster of this thread reported serious problems with his computer, which won't go away simply by upgrading, and expressed a wish to move from 32 to 64 bits, which is only possible by clean install.

If people would actually read a thread of about 10 posts before replying ...

---

### Post by Michael_McKenney on 2014-09-18
[http://releases.ubuntu.com/13.04](http://releases.ubuntu.com/13.04)
You can always get older revisions.  Just Google them.  I did 12.04 to 13.04 to 14.04

---

### Post by dvn3ch on 2014-09-19
I have to agree with RiverGuy99, I have not had the best luck with 14.04.  I am currently on a 75% failure rate.  It appears that only the newest hardware has no issues with the new upgrade.  All the older P4's and even one CoreDuo is having trouble with the upgrade.  Mine specifically is to do with video rendering very slow or muddled graphics.  Since this has happened on more than a few PC's, I am ruling out graphics cards...all are different.  Some laptops and others desktops.  Once I take those machines back to 12.04, they work like a charm.

A clean install of 14.04 on a P4 (solid machine, never any issues with Ubuntu) rendered graphics so slow that I could not bare to use it.  Performed a clean install of Xubuntu 14.04 and the slowness went away but the graphics rendering was muddled.  What I mean by that is, for example, I pull up a terminal and the default is normally a semi-transparent screen with fairly light font color.  When I start typing commands, it appears to show what is behind the font, clearly, instead of showing what I am typing.  Changing the preferences in any way just makes it worse.  Tried to install a different terminal emulator and I get basically the same thing.  Other programs show similar issues with the same disappointments when trying to change the default settings.

However, my new rig (about 1.5 yrs old) not only working well with the upgrade but did a flawless upgrade from 12.04 (I normally do clean installs but tried something different).  So it appears that many of the posts here that state a clean install is the problem is patently false.  It appears that the support for older PC's are waning fast for P4's and other not-so-old hardware.  It is probably for the best.  By the time 12.04 comes to an end, I will have replaced theses servers with RaspberryPi or i3 desktops.

---

### Post by dvn3ch on 2014-09-19
> **Michael_McKenney said:**
> [http://releases.ubuntu.com/13.04](http://releases.ubuntu.com/13.04)
You can always get older revisions.  Just Google them.  I did 12.04 to 13.04 to 14.04

Michael, 

I think you are mistaken on what is being said in these other posts, and maybe even of the OP.  You can install any older version clean.  However, the topic is about upgrading through the Ubuntu Update Manager.  The interim releases (12.10, 13.04, etc.) are obsolete now so upgrading from 12.04 to these releases through the Update Manager is not possible.  Yes, you can download the older interims and install them (not sure why but whatever...).  The OP's issue is upgrading not only to 14.04 from 12.04 but to go from 32 bit to 64 bit in the process.  That in itself is a call for a clean install.  I know of no other way to change the OS architecture while it is installed.

By the way, you cannot skip interim releases, like from 12.04 straight to 13.04.  You must go from interim release to interim release.  Only LTS versions can be upgraded straight away (12.04 to 14.04).  There is tons of docs all over the internet that explain this in more detail.  I suggest go take a look before replying to another post about this subject.  Our community is better with you in it but we must be careful when providing advice to others.  If you have not done it (or a variation of it) yourself, it is better to make that statement clear when you post.  Then they can proceed with caution.

---

### Post by Michael_McKenney on 2014-09-19
The earlier releases are available.  As you said, you might need to go from 12.04 to 12.10 and through a certain upgrade path manually.  It is an option that does not require reinstalling the OS completely.   Reinstalling from the ground up is not always an option for users especially if the computer is in production.  Microsoft server products no longer give you an in place upgrade path that is easy.  They want the upgrades done on new virtual or physical machines.  So you don't lose production.   Microsoft gets less support calls for in place failure.  You migrate everything now.  

You are correct, I should have been more clear in my posting.  What I pointed out was the older software is available.   Is it obsolete?  No OS is obsolete if it serves your needs and runs your applications.  My brother still uses DOS 6.22 and PFS First Choice for his business.  He likes it and it works.   I run a corporation data center that is 100% Microsoft.   I still have Windows 2003 32-bit servers running older applications that we need that cannot run on Windows 2012.  Most of the servers are Windows 2012.  None of our vendors have Linux clients.  

So obsolete is only from the perspective of what is new and improved.  If your router and firewall are configured to protect your Ubuntu box properly, 12.04, 12.10 or 13.04 is safe to use.  

What I provided was an upgrade path option that could be investigated and done.  I would think the user wants to run 14.04.1 in the end.  Maybe the path to it is 12.04 to 12.10 to xxxx to xxxx to xxxx to 14.04 since the direct method does not work properly and has issues.   I would not suggest staying on 12.10 or 13.04 for months.  I would say upgrade to 12.10.  If I remember, 12.10 to 13.04 did work.  Then once the user is on 13.04 try going to 14.04.   

Some times baby steps are better than jumping.

---

### Post by Pelvur on 2014-09-19
I've upgraded from 12.04 to 14.04 relatively recently (I guess whenever automatic update were deployed) with no issues. Also some time ago upgraded Lubuntu 13.10 to 14.04 - all went smooth as well. May be it's a matter of luck, or may be hardware.

---

