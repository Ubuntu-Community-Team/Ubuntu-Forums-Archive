---
title: "Create 2nd USB from working USB"
date: 2011-09-19
forum: New to Ubuntu
---

### Post by Denver Dave on 2011-09-19
I have a working USB 8 GB boot disk and have made various additions and settings changes since the initial install.  Seems like a good time to make a backup of this disk and use a larger USB drive. 

Is there a way to backup my 8 GB USB boot disk to a 16 GB new boot disk?   Seems like everyone would be doing this for backup purposes.  

However, I've examined the startup disk creator tool from within ubuntu and also the create startup disk when booting from the DVD and both seem to want to start fresh from the beginning install.

How do we make a new startup USB with how we have our system running now with various changes?  I really did searches before I posted this - seems  complicated.

The allocate drive space screen makes no sense to me.  The bottom part is fine - new 16 GB USB, but seems like the top part should be which drive contains the system files to be copied, but apparently this is not what it is asking.

Is there more to this than making a bootable disk and copying the files over?   Is it really this hard to make a working backup copy of our boot USB?

---

### Post by uncontrolable™ on 2011-09-19
I would create the backup set using remastersys, then use that image with the Startup Disk Creator.

---

### Post by Denver Dave on 2011-09-19
Thanks - a google search gives lots of discussion about Remastersys including the following.   Still wondering, I'm a beginner ubuntu user, surely other beginners would like to make a working backup of their system USB.   There's not an included tool to do this??

I have not a clue, but here is what I found:

Debating if might be easier to just start over, but I guess this is the time to learn.   Would be nice to have a "Make new startup disk from current installation".

= = = = = =

[http://www.webupd8.org/2010/08/create-full-system-backup-or-custom.html](http://www.webupd8.org/2010/08/create-full-system-backup-or-custom.html)

sudo add-apt-repository "deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/"
sudo apt-get update
sudo apt-get install remastersys

Do not replace "karmic" with "lucid" or other Ubuntu version name!

Remastersys is a tool which can be used to create a custom live Ubuntu / Debian CD. But it's not like the other such tools we've already covered as it can be used to clone your current installation which you can then use to either share it with your friends or create your own Ubuntu derivate. Don't worry about your private data and such, that's not going to be included onto the CD.

But that's not all there is to Remastersys: you can also use it for a full system backup onto an installable CD, DVD or USB drive - this will also include your personal data and you can later use it like any live CD/USB to reinstall your whole system and data.

= = = = = = 

What the heck - here goes.

- Boot from my modified USB not orig DVD
- find the terminal - not under administration, but is under applications
- can't seem to cut and past into the terminal window (added later - use ctl+shift+v to paste into terminal, not sure why not ctl_v, but works), wonder the odds of me being able to type correctly - command not found - maybe here's the typo - 3rd times a charm... made it past line 1 (note to self, investigate script files)
- I'm in trouble now, looks like might have installed something
needs more space - I guess I say yes from archives - maybe good I'm trying to get a bigger drive
- warning the following packages can not be authenticated - wonderful
- sure installing a lot of stuff
- python-support ???    
- I'm thinking maybe I did something wrong ....
- warnings about could not determine root device

- what the heck, remastersys does seem to be in the administration menu

- It is necessary to close all other windows and unmount any network shares while running remastersys backup.  (wonder what network shares means) Please do so now and then clickOK when you are ready to continue.

- I have the remastersys backup screen - let's see must modify config file

- change user name from custom to ubuntu - don't see where set password
- working directory - bet I don't have enough space on the orig boot USB ... hmmm
- well run the thing and see what happens

Can't believe this is how beginners are supposed to backup their boot USB, but thanks.

---

### Post by Denver Dave on 2011-09-19
Yep - ran out of space on orig boot USB.   Wonder how to stop this process.  Force quit out of everything.   

Guess I'll install fresh to the new USB from DVD - need the practice and would like to log everything I add and change anyway.

<sigh>

---

### Post by yndesai on 2011-09-20
Usually what i do is take backup of 

/var/cache/apt/

this at least ensure that all those
packages that i had installed are available 
for re-installation.

---

### Post by Denver Dave on 2011-09-20
> **yndesai said:**
> Usually what i do is take backup of 

/var/cache/apt/

this at least ensure that all those
packages that i had installed are available 
for re-installation.

Looks like the copy has potential, just getting into the file system structure - thanks.

General Q - if we make a bootable disk and copy all the files from the / directory to the new disk, wouldn't that be a bootable system disk less any files located on other drives?

= = = = 
I'm only starting so not a big deal, but apparently running out of disk space on original USB when making backup copy was not a good thing.  Did install larger GB drive from DVD and there are a lot of tweeks to remember when installing from scratch including:

- Install various packages, Skype, Openshot, Thunderbird
- remember to unmute the mike
- turn off screensaver pw
- fix audio input and play around with volume settings
- switch to classic layout

---

### Post by Denver Dave on 2011-10-26
Back to my original question.

I have one Bootable 16 GB bootable USB drive.  I'd like to backup where I'm at onto a 2nd drive that I could also use if the first one fails or get's lost or maybe give to a friend.

This discussion seems really complicated, involving additional programs, disk images etc.

Isn't there a command to create a bootable USB drive in linux - like the fdisk /s command in DOS (or maybe it was format /s)?  Then rather than use a disk image with fragmentation and bad sectors, isn't there a command to copy every file and subdirectory files from USB drive 1 to USB drive 2 - like the xcopy dos command (xcopy c: a: /s)?

Is this possible, or am I missing something basic in my understanding?

Thanks.

---

