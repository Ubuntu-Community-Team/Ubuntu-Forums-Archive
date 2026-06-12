---
title: "General questions about upgrades &amp; switching"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by KC_kid on 2011-11-16
New Linux user here.. I'll try to make this brief and get to my question but feel I need to provide some background.
We had an old Dell laying around and I wanted a data backup solution = NAS. Tried FreeNAS, didn't care for it, moved onto Ubuntu Server. It's working great, taught myself a lot and still learning. Then, I got a decent PC on the cheap from work (no operating system) and I'm trying different Linux distros to find what I like and think my wife can handle (both of us grew up on Windows).
 
Question: how do people switch from distro to distro, upgrade to new versions, etc. without completely wiping everything and starting over?? I have Ubuntu Server running and it took forever to figure out all the services and adjust the config files (mediatomb, subsonic), users, shares, copy all my data, set up a RAID, etc... I don't want to do all of that over!
 
What if I want to try Debian server? What if our new system is Ubuntu and I want to now use Mint? Maybe try Vector or openSUSE? Do I have to back up data, reformat, re-set up everything, configure it again so it works, copy back data, blah blah until it works? Then again when I want to upgrade?
 
Sorry if I'm ranting here but I don't understand how people switch all the time. I mean even the simple stuff like web bookmarks, you have to start over. I hope I'm missing something...
 
Thanks.

---

### Post by bluexrider on 2011-11-16
Most people try on new shoes using a Live CD/DVD

---

### Post by KC_kid on 2011-11-16
I hope this doesn't come off as complaining...  I'm actually really enjoying Linux and looking forward to using it everyday.  After I get a little more comfortable with it, I'm going to make all of our machines daul boot Windows & Linux so I can always use it.  Thanks again for any honest answers about my question.
 
So far, I'm using Ubuntu Server 10.04 LTS, ubuntu desktop 10.04, I didn't care for Ubuntu (whatever the newest is), I REALLY liked Mint11, looking forward to trying openSUSE and absolutely LOVING the idea of a persistent USB stick with one or more of these on it, so I can take it everywhere!  But for know, I don't even know which desktop version I like!

---

### Post by Rex Bouwense on 2011-11-16
Some people simply install new versions as they come out after backing up their data to some outside source.  Some people create a separate /home so they don't have to back up their data when they re=install.  I would backup anyway because you never know what is going to happen (Murphy's Law applies).  Some people upgrade from version to version every six months or 24 months for Long Term Support versions.  Does that help?

---

### Post by JayKay3OOO on 2011-11-16
Lost of people use virtualbox to run a different OS / Linux Distro inside their current one. With a modest machine fluent results can be achieved to get a feel for an OS before you go live with it and you can continue to use the main OS while this runs.

Virtualbox mainly chews RAM and graphics, but mainly RAM.

The OS is then effectively in sandbox mode as any problems won't affect the OS the virtual machine is running on. You can even just run the live CD via virtualbox.

Windows & Linux can be run in a VM, but aero (was not working for Windows 7 in virtualbox)

Server wise they are all pretty much the same, the main hurdle for users if often getting used to apt and then having to use yum or woof or some other app installer and getting used to tar.gz or another extension that is not .deb (debian files) the such that Ubuntu server uses, but a lot of applications such as webmin are compiled for all the most popular variants.

I can't imagine why u'd want to move off Ubuntu server for now. Get ur ssh server & webmin setup right on it and it's a doddle to use.

For USB sticks I use Puppy Linux as it's a 2 second installer. Load the OS, reboot the os and save the save file (sfs or something) and then that's it. From then on it will save each session settings to this file at intervals or when you shut down. You can run W7 from a USB flash drive to make windows portable, but I've heard performance is a bit naff on USB2.0

I look forward to seeing you in the 'how many of you have completely switched to Linux?' thread in a few months.

Good luck.

---

### Post by jjex22 on 2011-11-16
For us distro hoppers, it's pretty common now to use tools such as virtual box to virtually test out distro's before trying them - I was trying out opensuse 12.1 earlier! You can also download live cd's/dvd's of desktop versions.

I'm not as familiar with distro hopping with a server set up, as in my experience any way once I've got it working I tend not to change. To be honest I just use Ubuntu 10.04 for our home server - regardless of distro's you're going to be using the same programs anyway!

In terms of desktop hopping with the new highly polished distro's around I tend to put /home on a seperate partition so all my personals don't go anywhere, but as for programs I still add them awith each distro (usually by termial linking commands together with && so I can just tell it to go get my common programs and then come back later!

---

### Post by jjex22 on 2011-11-16
I think [this]("http://www.tuxradar.com/content/pain-free-guide-switching-distros") could help - I just picked up a tip or two!

---

### Post by KC_kid on 2011-11-16
Thanks for the quick replies!
I understand the LiveDVD thing, that does help a lot.  I have tried out a few with that method.  I also learned the value of preforming the md5sum check hash thing too, I got a few that had problems.
I guess I was looking for something similar to Titanum Backup in Android.  Back up all your apps & data, settings, etc., Load your new operating system, restore all the data from Titanium and your are good to go!  It even puts shortcuts back on your "desktop"!
Also, when it comes time to upgrade my server, do I HAVE too because of the LTS timeline?  And if so, do I have to find empty space for my RAID while I install new server software and build a new RAID?

---

### Post by KC_kid on 2011-11-16
> **jjex22 said:**
> I think [this]("http://www.tuxradar.com/content/pain-free-guide-switching-distros") could help - I just picked up a tip or two!
 
 
Looks like a great read, thanks for finding that!  And I have used virtual box too.  That's were I first learned about Linux, when I needed to format a USB to ext3 and didn't even know what that was...

---

### Post by jjex22 on 2011-11-16
> **KC_kid said:**
> , when it comes time to upgrade my server, do I HAVE too because of the LTS timeline?  And if so, do I have to find empty space for my RAID while I install new server software and build a new RAID?

You never HAVE to upgrade, but by the time 10.04 becomes unsupported (2015) you may as well! personally our home 'server' is already ~10 years old (most of it) and it's living out it's golden years ferrying files around for us,however by 2015 it maybe time to .. um let it 'live on a farm' ;)

as for the raid issue you shouldn't have an issue as the raid controller(s) are motherboard/card based and have their own firmware - changing your os won't change how you've set your raid :)

---

### Post by Denver Dave on 2011-11-17
I have one USB 16 GB drive with ubuntu 11.10 and another one with 11.04, both created from install DVDs.

See discussion about separate data USB drive here with link in thread to read-only issue I bumped into:
[http://ubuntuforums.org/showthread.php?t=1879124](http://ubuntuforums.org/showthread.php?t=1879124)

For me, running ubuntu from a thumb drive is a wonderful solution.  I'm still trying to figure-out how to make a "copy" of my application USB drive, in case I lose it or something goes wrong.  Here is the discussion: [http://ubuntuforums.org/showthread.php?t=1846917](http://ubuntuforums.org/showthread.php?t=1846917)

I'm thinking that cloning may not be quite right, because there may be bad sectors.  Somehow create the boot and partitions on the backup drive and then a copy for all the files from currently used drive to the new one.   Anyone else keeping a backup application USB drive.

The data drive shouldn't be a problem, just copy all the files from one drive to any other drive that has enough space (I think).

Dave

Dave

---

### Post by KC_kid on 2011-11-17
> **jjex22 said:**
> 
as for the raid issue you shouldn't have an issue as the raid controller(s) are motherboard/card based and have their own firmware - changing your os won't change how you've set your raid :)

The above also applies for software raid?  I didn't know if what you said implied hardware raid or not, that tells you how much I know... 
I did create a /data, where the raid lives, if that helps anything, I don't know.  Its two disks in the raid and the third has /boot swap /home and just / I think.

Thanks again for any and all the responses.  Honestly I have no one to bounce this stuff off of because nobody I've talked to even knows this is possible or exists.  One guy did have a freenas setup I guess..  Anyway, good or bad, feedback is feedback.

---

### Post by jjex22 on 2011-11-17
Sorry I did totally forget about software raid! I've been a bit spoiled of late with home pc's coming with raid controllers! I can only testify to reinstalling the same version of ubuntu - so long as you only reformat that disk/partition - a reinstall of ubuntu (desktop version though I wouldn't have thought it mattered) could tell the disks were in raid, so that wasn't an issue but I did have to manually mount the array whenever I rebooted - I chose to put up with it as I'm lazy! but this would be very irritating for a headless server... I'm sure other's on here will know more!

---

### Post by grahammechanical on 2011-11-17
I have created a couple of 10-15GB partitions that I install different versions of Ubuntu in to test them out. I have not tried any other distribution. I do not like messing with my working system. I test each Ubuntu release before I convert my working install.

I have Grub Customizer installed on my working Ubuntu to correct any changes to the Grub bootloader that one of the other installations may make.

Regards.

---

### Post by 3rdalbum on 2011-11-17
I think your question is a little off-the-mark, actually. Your question, if you remember, was "How do people manage to distro-hop on their home servers without having to start over again?".

The answer is that people with home servers don't generally distro-hop. They install a long-term distro, set it up the way it needs to be, and then stuff it in a closet and forget about it until the day it dies. Or until after the next blackout and you can't figure out why you can't access the server anymore :-)

In short, find a good solid distro that will be supported on the server for years, install it, set it up, and forget about it. If you want to do experimentation, use a different computer.

Someone earlier recommended running Ubuntu from a thumb drive. I totally killed a thumb drive after running my server's OS off it for six months. Maybe I was unlucky or the drive was faulty anyway. Still, it's been working without a problem, 24/7, for about a year on an ordinary laptop HDD. My advice is that if you don't want to be setting up your server again anytime soon, leave solid-state storage to the gamers and experimenters, and instead employ conventional media to run your server.

---

### Post by Denver Dave on 2011-11-17
Or maybe figure out how to do a backup from a USB boot disk that can restore to a working USB?   On my XP desktop, I run shaddow protect to backup my 250 GB HD to my 2 TB MyBook USB drive.   Backing up a 16 GB ubuntu USB boot drive might not be that bad, if I knew how to do it with a linux tool or command and knew how to restore.  

In ubuntu 11.10 after clicking on Home, I see the following folders:

Computer
- Home
- Desktop
- Documents
- Downloads
- Music
- Pictures
- Videos
- File System
- Trash

I'm not clear if each of the above are separate folders or if some are also included in file system.  Either way, if running from a USB boot drive (and maybe from a HD), it might be a good to back up.   

Even if I have the data separate (all the data), installing a new system can be tedious and the USB drive could just get lost (drop out of my pocket).

Debated whether to include the above on this thread, but decided to because maybe backup strategy does relate to upgrade and switching strategy.

Ideas? Thoughts?

---

### Post by KC_kid on 2011-11-18
My goal in this experiment was to have a central storage location for all of our data.  So when I installed the server, I made a new partition called /data and that has the directory of all of our files.  I also created a /home that has some temporary files on it, the boot HDD is only 30gb, so /home is only about 20gb.  I've got all the data copied over, it's protected from HDD failure in the RAID and I'm planning my 1st rsync to USB external now, that's going in the gun safe.

I installed Ubuntu Server 10.04 LTS so I should not have to update for a few years.  Also, after trying a few distros out, I'm going with Linux Mint 11 for the new desktop and I put mint 11 LXDE on a micro SD card for taking with me.

I also figured out that you can sync your Chrome settings with Google and when I installed a new dristro, I just resynced chrome and all my stuff came back!  Even the theme I set up, that worked great.  The only thing when switching distros now is installing all of the extra programs I want, Wine, etherwake, putty, etc...  

So I have the central storage that's in our network and I have a customized OS on a USB that I can plug into any PC, log into our VPN (built into Tomato) and access my shares from anywhere!  I'll be traveling around Kansas next week so I can try this out on all the old computers I come across at inlaws, grandparents houses, friends, etc...

This Linux deal is pretty sweet!!:guitar:

---

### Post by KC_kid on 2011-11-18
The only thing now is, what do I do if the boot disk fails?  Would I be able to read the RAID from another computer with Linux?  If I bought a new drive, installed ubuntu server, would it read the RAID?  Any one know a good cloning program?!

---

### Post by RotorRick on 2011-11-19
The guy who inspired me to try Linux had written two software programs for his boss' small business, and one day we visited him: he had 6 computers, all running various Linux OS's! Don't ask me which ones, because I didn't know what they looked like at the time. What I do know is he had two different servers, a "test machine" to try out new programs/OS, another for programming new applications/progs, and a more general use one. Two of them, he said, had Windows in dual boot, for those special times where he wanted to try something on the Microsoft side of the world. He recommended I try Ubuntu, and specifically mentioned this website forum as the greatest tool to help sort through technical issues.

Someone mentioned PuppyLinux, and I tried it, I was impressed! Frankly THAT is likely the best way of having a "Linux on a stick" USB option, it's so lightweight and speedy I was actually giddy! Not really what I want for a permanent OS for a high-use laptop/desktop, but that's where Ubuntu/Mint and others do a fine job.

---

