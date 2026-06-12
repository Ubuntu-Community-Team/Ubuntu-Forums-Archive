---
title: "[SOLVED] Bug fixing problem? Nothing updates! Filled a report. Answers?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by BastardNamban on 2008-11-19
Forgive me, I'm totally new to Linux- just installed Ubuntu 8.0.4.

Besides having sound issues (I have no idea where to get drivers(?) for my laptop since it's running linux, or even what I need anymore) I am having some real pain trying to update stuff/get multimedia codecs.

I followed the sticky info, made a launchpad account, and filled out a
bug report as best I could, instead of just whining on here :) Here's a link: [https://bugs.launchpad.net/ubuntu/+bug/299864](https://bugs.launchpad.net/ubuntu/+bug/299864)

My question is, how do I fix this? It's keeping me from updating anything!
How are bugs fixed in linux, are there patches you download, like in windows? (XP pro user for years, thank god that's over)

I googled this bug, and it seems some others had it, but I can't seem to figure out if it was fixed or not, and if fixed, how I fix it?

Please help, someone? I want to update, get stuff installed, and start enjoying linux with working sound, and everything. I can't update anything as long as it's like this!

Thanks.

---

### Post by hyper_ch on 2008-11-19
two things:

(1) yuo say something with dictonries comes up to --> it is essential to know the full error so please post that also

(2) it would be good to know what soundcard you have. Run
```

lshw -html > ~/Desktop/hardware.html

```
and attach the hardware.html in your post or load it up onto some webspace.

---

### Post by BastardNamban on 2008-11-19
It will not let me- says I should run it as a super user. I tried running it as an admin command with sudo, but nothing happens- says "PCI (sysfs)" for a few seconds then goes to the prompt again with nothing happening. I catch it saying "frame timeout" real quick, but nothing happens.

I cannot remember what soundcard I have- speaking of which, I don't have my sound working properly. See this post (perhaps the problems are linked?):
[http://ubuntuforums.org/showthread.php?t=984052](http://ubuntuforums.org/showthread.php?t=984052)

Thanks.

---

### Post by hyper_ch on 2008-11-19
it recommends to run as super user (but it's not required) and it should create a hardware.html file on your desktop.

---

### Post by BastardNamban on 2008-11-19
Ok- yes, it did create quite an impressive spec-related file.

I'm kindof afraid to post it, actually, since it's so detailed looking.

What info do you need from it? It's very long.

---

### Post by BastardNamban on 2008-11-19
Here is the bug- I was trying to install GPM, something I found to (ironically) let me copy & paste error messages from terminal error boxes, and I got this- (it looks almost exactly the same as the update manager error, if not BEING exactly THE SAME):

______________________________________________
The following NEW packages will be installed:
  gpm
0 upgraded, 1 newly installed, 0 to remove and 165 not upgraded.
1 not fully installed or removed.
Need to get 382kB of archives.
After this operation, 725kB of additional disk space will be used.
Get:1 [http://jp.archive.ubuntu.com](http://jp.archive.ubuntu.com) hardy/universe gpm 1.19.6-25ubuntu1 [382kB]
Fetched 382kB in 1s (267kB/s)
Preconfiguring packages ...
Setting up base-files (4.0.1ubuntu5.8.04.3) ...
find: /var/cache/fonts: No such file or directory
find: /var/cache/anthy: No such file or directory
find: /var/lib/locales: No such file or directory
chgrp 0 /etc/dictionaries-common/words /etc/dictionaries-common/default.aff /etc/dictionaries-common/default.hash 
chgrp: cannot dereference `/etc/dictionaries-common/words': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.aff': No such file or directory
chgrp: cannot dereference `/etc/dictionaries-common/default.hash': No such file or directory
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)
shogun@Valhalla:~$ 
_____________________________________________________


Also, sorry for the confusion above, here are the specs for my sound card, via your advice:

_____________________________________________________
id:	
multimedia
description: 	Multimedia audio controller
product: 	82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller
vendor: 	Intel Corporation
physical id: 	
1e.2
bus info: 	
pci@0000:00:1e.2
version: 	03
width: 	32 bits
clock: 	33MHz
capabilities: 	pm bus_master cap_list
configuration:	
driver	=	Intel ICH
latency	=	0
module	=	snd_intel8x0
_____________________________________________

I hope this gives you an idea of what I'm dealing with. It's keeping me from installing or updating ANYTHING, and I have no idea how to fix it.

Can you or anyone else help?

---

### Post by hyper_ch on 2008-11-19
well, the sound card should work out of the box.

And regarding that error when you try to isntall something... that is strange... I wonder what you did on your system.

---

### Post by BastardNamban on 2008-11-19
Someone else mentioned Intel drivers are well supported in linux, but my card's family doesn't show up in the Dell linux wiki.

I have no way to hear sound except by finding the Nelson Mandela video that came in the examples folder- I have none of the audio codecs or apps that let me see youtube, because I can't update due to that error. My mp3s don't play, again, due to not having any codecs, due to not being able to update.

I do have the Mandela video, though, and for some reason THAT plays, with sound, so I know my soundcard kinda works, but not properly. Volume controls on the front of the laptop are how I adjust volume, and using them only affects the front 2 treble speakers, the subwoofer is unaffected.

Using the volume up/down option in the video player, it does affect volume, but ONLY the subwoofer! Adjusting up & down with the player's 2 sound options only affects the sub- no change at all to the main front two speakers.

Adjusting the two front speakers only works with the front 2 buttons, and a little volume bar shows up on screen, and adjusts accurately for them as I go up or down. But in the end, both sets of ONBOARD speakers don't work together.


As per the final problem, I often heard it was common for linux people to claim they don't know what the user has done to their computer, but I thought that was just joking (not meaning to sound rude)- I have told you everything I have done, the only other thing that occurred was I enabled "universe", I seem to remember it prompting me for that, and I remember reading somewhere it was a good way to open up features.

That is all I know- if nothing I said so far has helped diagnose, I'm at a loss- cause' I'm having these problems with a FRESH INSTALL- if I didn't do it with any of the little I could do so far, it's the BUILD'S FAULT! I checked the .iso for integrity before I installed, and it said no problems.

I think it's arrogant of me to even think of blaming the build itself, but I have no other idea how something that's supposed to be rather simple to get running out of the box, as it were, can be so F*cked up when I haven't even had a chance to do anything yet!

Sorry, this is driving me nuts. I gotta get sleep- its 230am here. I'll check back in like 9 hours.

If you still think you can help, I humbly welcome anything. Thanks.

---

### Post by Zill on 2008-11-19
> **BastardNamban said:**
> 
dpkg: error processing base-files (--configure):
 subprocess post-installation script returned error exit status 123
Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)
shogun@Valhalla:~$
Regarding the error with installing base-files, you may like to try the fix in post #6 of the following thread:

[http://ubuntuforums.org/showthread.php?t=982090]("http://ubuntuforums.org/showthread.php?t=982090")

---

### Post by BastardNamban on 2008-11-20
> **Little Blue said:**
> hehe, I've got a solution, but it feels like a very dangerous and risky solution so use at your own risk. It worked for me at least!

if you have a look in /var/lib/dpkg there should be a status file. Make a backup of that and then open it.

Search for something like

```
Package: base-files
```

If its the same problem I had the status should be

```
Status: install ok half-configured
```

Change that to

```
Status: install ok not-installed
```

And delete everything pertaining to this package (should be the next dozen or so lines) after "Section: admin"

This should leave you with these five lines in the status file

```
Package: base-files
Essential: yes
Status: install ok not-installed
Priority: required
Section: admin
```

then run apt-get -f install

If you check your status file then it should be back to having a long entry for the package with the status: install ok installed

And everything should be fine then!

I hope this works for you as well as it did for me!


I tried this. I got error again.

Nothing is working, and I have a very strong feeling it IS something wrong with the build itself when it installs.

I am stuck with linux now, after my XP disk is so old, it has no service pack, and while I could install it again, I tried after giving up in frustration on linux the first time I installed 3 days ago, over this SAME PROBLEM. I found that only SP3 is still available on MS's site. Basically, I have a legal copy of XP, but I can't get it updated or recognizing my internet connection until it updates, which I need the internet for, and using a friend's XP box, can't even find the updates to do it, so I move BACK TO LINUX. Then THIS PROBLEM happens again, with a fresh install.

So I am STUCK with linux now, seemingly broken off the CD, as it were, and I'm lucky I even have the internet. I have no idea what to do, and I'm sick of this. Nothing works, I cannot update and thus put THINGS on this computer.:mad:

Any ubuntu coders out there know what's going on here? HELP!

---

### Post by hyper_ch on 2008-11-20
If you prefer going back to WinXP you can download the service pack in linux, burn it to a cd, re-install windows and then upgrade with the downloaded service pack.

You could also download drivers for your lan, wifi, soundcard, .... in linux and also burn it.

But as for your problem, I have no clue what's wrong. I'd suggest you do a re-install of Linux and then you take notes on what you're doing. That will help to find the problem where things go wrong.

---

### Post by BastardNamban on 2008-11-20
Ok, to satisfy all requirements, DESPITE the fact that this IS just installed, I will install it again. I will not do anything other than turn it on, and try to update, and if needed, restart, and try updating again. I will post exactly what comes up. Though, since this is now the second install ALREADY, and the same problem, I fear it will just happen again.

I have an appointment with a friend this evening, when I return, in maybe 5 hours, I will fresh install linux, and report.

I have a feeling this might be fixed if I just went with Intrepid Ibex, but I want to use a version with the longest support possible.

So hold on for a few hours, and really, thanks for your patience. I will try as best as I can to keep mine.

---

### Post by hyper_ch on 2008-11-20
well, the LTS is "only" 3 years for desktops. And non-lts have 1 1/2 years. However if LTS is not working you should try the latest one (Ibex).

---

### Post by Zill on 2008-11-20
BastardNamban:  I know you are frustrated by your problems but please DO NOT SHOUT - we are all just ordinary users trying to help each other as best we can.

In order to resolve the problems I suggest that you break things down and clarify exactly what is happening at each stage.  Please supply as much detail as possible - just saying "I got error again" is not helpful. ;-)

1)  Using the Live CD (i.e. *not* the installed version on your HDD), does Ubuntu load and run correctly (if slowly!) from the CD drive?

2)  With the installed version, straight after the install (no updates) does Ubuntu run correctly?  You may not have multimedia at this stage but do the main applications run OK?

3)  After installing just the updates - no additional applications - do Ubuntu and the main applications run correctly?

4)  If the "base-files" error is still there then does the fix I suggested in post #9 have any effect.  Please post *full* details of what happened.

Once the update errors have been resolved then we can look at getting the multimedia working - but for now let's keep it simple and knock the problems down one at a time.  :-)

---

### Post by BastardNamban on 2008-11-20
Ok, I have good & bad news.

I reinstalled from the 8.04 live disk (all times were from live disk)- I tried something different this time. I had always, after I got in, immeadiately gone into firefox, without updating anything first- when I first did all this, I didn't know there were 179 updates, since it only shows them after about 5 minutes. I didn't wait last time (the second time) either.

This time (3rd time), I knew there were updates, and I did NOTHING, and waited for them to appear. Surely opening firefox had nothing to do with all this, I thought, but I waited anyway. The same 179 updates came. I updated like I had tried before.

It worked.

I don't know why, but it did. After I was updated, I restarted, waited for any more updates, and after seeing 10 minutes go by, I decided THEN to open Firefox. It worked. I even updated my media codecs with no problems after it searched for them, clicking on one of my mp3s. I can play anything now, I think. Maybe it's just me- but wmv's look a little less good...

So I have all the updates, and all the media codecs now, I think. I guess opening firefox right away has something to do with the error. I have no idea why, but that fixed it.

I still have the same sound problems, the speaker sets are disconnected, but the error is gone. I can only assume next time there are updates available, there will be no problems.

I will mark this solved, thank both of you, and apologize if I lost my patience.

I still have messed up speakers, and I have no idea what Ubuntu has natively working as far as drivers. I'm not sure if my graphics card is enabled, etc., but the bug is gone.

---

### Post by Zill on 2008-11-20
> **BastardNamban said:**
> ...I still have the same sound problems, the speaker sets are disconnected, but the error is gone...
Congratulations on fixing the update error - patience is a virtue. ;-)

If you want to get your sound working then please post *exactly* what is happening and as much information about the PC spec as you have.  It may be best to start a new thread for this so that things don't get too confused when people search the forums later!

---

### Post by hyper_ch on 2008-11-20
> **BastardNamban said:**
> I guess opening firefox right away has something to do with the error. I have no idea why, but that fixed it.
Me neither, firefox should not have any influence on that... instead of waiting you could have opened a terminal and run this:
```

sudo apt-get update && sudo apt-get upgrade

```
That would have started the update process...

> **BastardNamban said:**
> I still have the same sound problems, the speaker sets are disconnected, but the error is gone. I can only assume next time there are updates available, there will be no problems.
Hmmm, you might want to search the forum for "pulseaudio". It could be that this is causing problems.

---

### Post by BastardNamban on 2008-11-20
Thanks :) I already had a separate post that was just questioning my drivers & sound, you can see it here: [http://ubuntuforums.org/showthread.php?t=987104](http://ubuntuforums.org/showthread.php?t=987104)

I have to head to bed- Its like 2am & I have a job interview tommorrow to (hopefully) keep me here.

Before I go- Aside from the minor issue of flash not working (despite putting in adobe, 2 times!), I have just explored like every customization option I could find in the last 2 hours- I've made the panel bar transparent, moved button positions, found the login user settings and changed things around a bit, like making passwords show-up blank for security, customized Nautilus to something less eye-gouging than "human" orange, taged folders with special symbols, customized panel menus/nautilus bookmark menus with custom folders, uploaded all my saved firefox bookmarks (no prob!), and tweaked nearly everything I could find.

I must say, I am really, really impressed with what I now see is Linux's true power- you can customize EVERYTHING, a lot of stuff you can't do easily in Windows is cake in Ubuntu. I used to use Style XP to skin XP, but Ubuntu seems like I can create simple colors & backgrounds, even natively change looks. Impressive. And every little permission/way the files & windows can be commanded, moved, arranged, etc. is even more impressive.

I can see it's just what I dreamed of- I get it now! So much of this was cake for me to figure out, just by exploring and having fun with it.

XP? Dead to me. Unless I want to use parametric CAD modeling again, I'm not going back. Linux is really impressing the hell out of me! :biggrin:

---

### Post by ubuntumaybe on 2009-02-05
Hi,

Thanks very much. I had this extremely frustrating problem and your solution repaired it. Thanks.

---

