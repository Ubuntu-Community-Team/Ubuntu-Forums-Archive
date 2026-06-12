---
title: "Need help trying to install Ubuntu for first time!"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by mnemonik on 2008-06-30
First of all, I hope this is the right forum! And I thank you all in advance for any help that you can give me!

So I downloaded the ubuntu-8.04-desktop-i386.iso and the MD5sum hash check matched what it was supposed to. I used InfraRecorder to burn the iso to a disc, then I checked the integrity of the disc after boot up and there were no issues. I can run Ubuntu from the cd, however when I try to install I get stuck. I get through choosing a username and my keyboard and time perfectly and the problem comes about when I actually get to installing.

I use the guided partitioning and when the "installing system" window gets to the "partitions formatting" it freezes everytime at 5%. The task that it says underneath the status bar is "creating ext3 file system for / in partition #1 of IDE3 master..." I have tried this four or five times and it always freezes right there, I can't move the mouse or anything.

The computer is my Mom's Dell Dimension XPS T600r, and it was running xp sp2, however when I attempt to boot without the ubuntu installer cd it now says there is no OS.

What am I doing wrong??? Please help, and thank you to everyone who does!

---

### Post by bluepowder7 on 2008-06-30
were you hoping to keep WinXP, or get rid of it and have only Ubuntu?
which guided scheme did you use - the whole disk or some other one?
i always go the manual partitioning scheme.  actually, i use the live cd to run gparted to make the partitions, and then use the installer after and select which partition to use manually.

---

### Post by bred on 2008-06-30
> **mnemonik said:**
> First of all, I hope this is the right forum! And I thank you all in advance for any help that you can give me!

So I downloaded the ubuntu-8.04-desktop-i386.iso and the MD5sum hash check matched what it was supposed to. I used InfraRecorder to burn the iso to a disc, then I checked the integrity of the disc after boot up and there were no issues. I can run Ubuntu from the cd, however when I try to install I get stuck. I get through choosing a username and my keyboard and time perfectly and the problem comes about when I actually get to installing.

I use the guided partitioning and when the "installing system" window gets to the "partitions formatting" it freezes everytime at 5%. The task that it says underneath the status bar is "creating ext3 file system for / in partition #1 of IDE3 master..." I have tried this four or five times and it always freezes right there, I can't move the mouse or anything.

The computer is my Mom's Dell Dimension XPS T600r, and it was running xp sp2, however when I attempt to boot without the ubuntu installer cd it now says there is no OS.

What am I doing wrong??? Please help, and thank you to everyone who does!

[COLOR="Navy"]Hi there,
I'm not an expert but give another chance to ubuntu and I think that u should burn the iso file at the lowest speed and on a good dvd...
then try to boot from Cd primary and do a fresh install with gparted[/COLOR]

---

### Post by Yuki_Nagato on 2008-06-30
The type of "guided" formating you used is critical.

If you used the "largest available space" option on a box that had Windows on it, then it tried to install a 600 MB system onto a 10 MB space (Windows likes to consume the entire hard drive).  This might be the root of the problem.  If you do not need the Windows, then do a guided installation using the entire hard drive.  This will take care of all of your swap and formating issues.  If you still want the Windows XP data, get the Windows XP disk out and boot to that.  "Repair" Windows with it (It holds your hand through the process).  We repair the Windows installation so that we can boot to it and make sure that it is, in fact, still alive and worth keeping.

_[http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html]("http://linuxhelp.blogspot.com/2006/01/effective-partitioning-how-and-why-of.html")_

This link will provide some insight into partitioning.  A search with Google will provide you with more answers tailored to your specific needs.

---

### Post by mnemonik on 2008-06-30
I'm still trying to give ubuntu a chance.

No, I don't need the old XP.

I chose for ubuntu to use the whole hard drive when i was partitioning.

I ran a google search of this:

"creating ext3 file system" 8.04 site:ubuntuforums.org

and found someone else who was getting stuck at 5% just like me.

They fixed they're problem by partitioning with system restore cd or something like that and then installing ubuntu with manaul partitioning and using what they already set up. I am downloading that from the link that was provided but its going like 60kb/s and has an eta of an hour (ugggh).

I'm not trying to create a dual boot machine, I only want to boot to ubuntu. Can anyone give me some advice on manual partitioning that would let me complete the install? I tried doing the manual partitioning myself by deleting all the partitions there were and then creating one new one but i kept getting an error msg that wouldnt let me go to the next step of installation saying something along the lines of "no boot partition selected" but I couldn't find any options regarding that...

Thanks to everyone who has replied so far!

EDIT: system rescue cd not restore!

---

### Post by bluepowder7 on 2008-06-30
you can use the LiveCD that you already have to partition your hard drive.  insert it, select the option to try out the system, and once you're in, find GParted or Partition Editor or something like that in the System - Admin or System - Pref menu.

from there, erase all the partitions, click apply.
create two partitions (one big one for root, one small for swap), click apply
if you want, create 3 or 4 partitions instead (root, swap, boot, home, and whatever else), click apply

yes, i found that doing the "click apply" often keeps gparted from crashing or failing to do what i tell it to do.

then, click the install icon (if there is one) and install the OS!  use the manual scheme when you get to it, edit each entry, select the filesystem, tell it to format it, and so on...

---

### Post by mnemonik on 2008-06-30
> **bluepowder7 said:**
> you can use the LiveCD that you already have to partition your hard drive.  insert it, select the option to try out the system, and once you're in, find GParted or Partition Editor or something like that in the System - Admin or System - Pref menu.

from there, erase all the partitions, click apply.
create two partitions (one big one for root, one small for swap), click apply
if you want, create 3 or 4 partitions instead (root, swap, boot, home, and whatever else), click apply

yes, i found that doing the "click apply" often keeps gparted from crashing or failing to do what i tell it to do.

then, click the install icon (if there is one) and install the OS!  use the manual scheme when you get to it, edit each entry, select the filesystem, tell it to format it, and so on...

ok one big and one small would do fine for me... I don't think i need anything fancy which sounds like having 4 partitions would be.

how big should the small one be if the big one uses all the rest (i assume)? what is "swap" used for?

thanks!

---

### Post by eriqjaffe on 2008-06-30
> **mnemonik said:**
> ok one big and one small would do fine for me... I don't think i need anything fancy which sounds like having 4 partitions would be.

how big should the small one be if the big one uses all the rest (i assume)? what is "swap" used for?

thanks!Actually, having three partitions isn't a bad idea - one for the main system, one for your home directory (or directories, if it's a multi-user setup) and one for swap.  The main benefit of having a separate partition for /home is that if you need/want to reinstall your operating system, you can do so without touching any of your documents and configuration files.

Swap is drive space that gets used as RAM if you run out of physical RAM.

---

### Post by ChameleonDave on 2008-06-30
> **mnemonik said:**
>  what is "swap" used for?

thanks!

Wikipedia is your friend.

Swap is virtual memory: [http://en.wikipedia.org/wiki/Swap_space](http://en.wikipedia.org/wiki/Swap_space)

---

### Post by mnemonik on 2008-06-30
alright 3 partitions does sound like a good idea now (system, swap, and home).

So I managed to get into the partition editor, but here are my final questions (hopefully!) How big does the system partition need to be? how about swap? (I'm thinking a good sized swap would be nice since this is an older machine and only has 512mb RAM, does swap size directly convert to virtual RAM size or does a gig of swap not ~= a gig of RAM?)

---

### Post by ad_267 on 2008-06-30
There's different ideas of what swap size should be. If you have 512 mb of ram then 1gig swap partition should be about right. Having a gig of swap definitely isn't like having an extra gig of ram though.

A separate /home partition is a good idea. I initially just had a root partition and a swap but now have a separate /home.

For the size of your root partition and home it depends on how much space you have really. I think a basic ubuntu installation takes up about 3 or 4 GB. I'm using 10GB out of 16 at the moment with a lot of extra applications and games installed. I have 80GB for /home and am using 25 of that.

---

### Post by mnemonik on 2008-06-30
furthermore, does it matter what type of partition i create (fat32, ext3, etc..)

---

### Post by cjv8888 on 2008-06-30
Give the swap about twice your RAM or no more than 2 GB.
I would suggest using ext3.

---

### Post by ad_267 on 2008-06-30
Yeah the swap partition is formatted as swap. Your root partition should be ext3. If you want to share your /home with a windows installation you could make it ntfs I think but ext3 would be best. You can alternatively have a /data partition that is ntfs if you want to share data with windows. If you're running Ubuntu only then make it ext3.

---

### Post by ChameleonDave on 2008-07-01
> **ad_267 said:**
> Yeah the swap partition is formatted as swap. Your root partition should be ext3. If you want to share your /home with a windows installation you could make it ntfs I think but ext3 would be best. You can alternatively have a /data partition that is ntfs if you want to share data with windows. If you're running Ubuntu only then make it ext3.

No, NTFS causes problems.  For Windows compatibility, use FAT.  Or, better still, use Ext2 or Ext3 (and install the ext2fs drivers on Windows so that Windows can access the partition).

---

### Post by bhadotia on 2008-07-01
What an informative thread ! :popcorn:

Cleared all my concepts about linux installations. I love this forum. Kudos!:)

---

### Post by ad_267 on 2008-07-01
> **ChameleonDave said:**
> No, NTFS causes problems.  For Windows compatibility, use FAT.  Or, better still, use Ext2 or Ext3 (and install the ext2fs drivers on Windows so that Windows can access the partition).

How does ntfs cause problems? I'm not trying to argue I'm just interested. I've found ntfs to be better as it supports symbolic links and since Gutsy ntfs support has been included by default. I also managed to mess up a fat32 partition from Ubuntu once.

---

### Post by ChameleonDave on 2008-07-01
> **ad_267 said:**
> How does ntfs cause problems? I'm not trying to argue I'm just interested. I've found ntfs to be better as it supports symbolic links and since Gutsy ntfs support has been included by default. I also managed to mess up a fat32 partition from Ubuntu once.

NTFS is a Microsoft trade secret.  It has taken long and painstaking reverse-engineering to get Linux NTFS support to the point where it probably won't nuke your files.  I still don't trust it.  I see people with NTFS problems on the forum.

FAT is a much better documented format.  It is old and primitive, but all operating systems can use it.

Personally, I prefer to use Ext3.  It is a decent, modern, journalled, open-source filesystem that Linux can never have problems with.  And drivers are available to make it work for when I occasionally boot into Windows.  I use ReiserFS for the root partition.

---

### Post by mnemonik on 2008-07-01
Alright I'm sorry I'm being such a nuisance but I think I figured out the partitioning but around 23% in the install it gives me one of two error messages.

The first one is [errno 5] input/ouput error. It then recomends I either burn a new cd, clean it, or clean my cd drive lens. I can't imagine it would be the cd since before installing I checked the integrity and it said it was all go. The other thing it said was that maybe my hard drive was ****** up, and this was what the other error said as well. I am going to shoot myself if the hard drive is messed up, it was working yesterday with XP, why would it all of a sudden be messed up when I'm trying to install ubuntu??? The last thing it recommends is to try installing again in a cooler environment. Well yeasterday it was around 80 degrees so I thought hmmmmm ok and i tried this morning when its gotta be only 60 out. same error.

I'm really trying to give ubuntu a chance but i feel like it is not trying to help me!!! GRRR. sorry.

Thanks so much for putting up with my novice-ism!

---

### Post by eriqjaffe on 2008-07-01
IIRC, the XPS T600r is a fairly old Pentium III machine, correct?  If that's the case, you may need to use the "Alternate Install" CD, which is an install-only disc (there is no "live" environment to install from).  It's much more useful on older systems, especially considering that installing from the LiveCD requires something like 384mb of RAM.

There's a checkbox on the download page to get the Alternate disc.

---

### Post by mnemonik on 2008-07-01
nothing too different about the alternate installer besides no live? I'm downloading right now.

---

### Post by bhadotia on 2008-07-01
Nope ! Everythings the same basically but with that glowy frontend of the live CD . If you need help with installation procedure post back.
Have fun installing;-)

---

### Post by mnemonik on 2008-07-01
downloaded the alternate 8.04 installer, md5sum mathes.

before i was booting from the live cd, but now when i put the alternate in and turn on the computer it just says no OS found, and i'm not seeing any option to boot from the cd... please help!

---

### Post by bhadotia on 2008-07-01
My friend had that problem.
His latest lenevo laptop could not read any CD which was written with cd burner - only commercial CDs which had data already written on them. What I mean is that his cd drive was messed up. 
I think your old PC needs a change of CD drive.
Still , try again . Clean the CD . insert it again and again , it might just work . Or just request a free CD or buy one from ubuntu.com. But you need to wait a few weeks for the CD to be delivered (I had to wait 4 weeks for the CD to be delivered to my place (India) from nietherland or so).
Good Luck.

---

### Post by mnemonik on 2008-07-01
thanks, i am gonna try to clean the cd, and the drive's lens then retry.

---

### Post by ad_267 on 2008-07-02
> **mnemonik said:**
> downloaded the alternate 8.04 installer, md5sum mathes.

before i was booting from the live cd, but now when i put the alternate in and turn on the computer it just says no OS found, and i'm not seeing any option to boot from the cd... please help!

Was the live CD one you burnt or one you ordered from Canonical? Weird that the live CD worked but alternate install won't.

---

