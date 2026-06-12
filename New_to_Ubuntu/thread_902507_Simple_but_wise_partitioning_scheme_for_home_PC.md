---
title: "Simple but wise partitioning scheme for home PC"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by Forgotten Path on 2008-08-27
First off, thanks in advance for even looking at this thread.  I know most people are tired of hearing about partitioning schemes...

I have decided to install Ubuntu 8.04 on my laptop, no dual boot, just want to get rid of Windows.  I know that it is a good idea to place /home on a seperate partition, but I have also read many sites that suggest seperate partitions for /boot, /, /var, /var/log, /usr, /usr/local, and /tmp.  Are all these really needed for a home PC?  I would like to be able to reinstall while keeping my program settings, etc. intact.  I know these are stored in /usr, and /usr/local, as well as /home, but do I really need /var, /var/log, and /tmp?  I don't think my logs, etc. will ever be a problem.  And what exactly is the reason to put /boot on its own partition?  Some advice on which ones are really needed and some possible sizes would be much appreciated.

Thanks, everyone!!

---

### Post by Nythain on 2008-08-27
i would personally go with
/ - root partition
/boot - seperate partition for boot out of old habbit
/etc - most program .confs are stored here
/home - user settings and themes and configuration for most DE apps

the only reason i could see backing up /var or any of its derivatives is if you say, didnt want to lose mail, or ran a webserver, either way, not to important for a home pc.

---

### Post by Forgotten Path on 2008-08-27
Thanks for the quick reply.

What exactly is the purpose of having a seperate /boot partition?  I read somewhere that it makes it easier to recover kernels, but if I have my data and settings on seperate partitions, wouldn't it just be easier to reinstall?

---

### Post by mcduck on 2008-08-27
Just keep it simple:

/
/home
and swap, of course.

The more you have separate partitions for separate system directories, the more likely you are going to end with some system directory running out of space while others have plenty. Keeping all system stuff on one partition means you don't have to plan how much stuff you are going to install and how much space each system directory needs.

/boot isn't really thet usefull these days. It might be needed on very old systems thata ren't able to handle as large hard disks & partitions as we have these days. And you may need it with some RAID setups as well. But otherwise having a separate /boot just makes things harder than they should be.

Mounting different system directories separatley is only useful on systems with several different types of disks, you could for example keep most of the system on a Flash drive, while putting swap & logs into a normal hard disk to increase the lifetime of the Flash drive. But putting them to different partitions on same disk is much less usefull.

---

### Post by snowpine on 2008-08-27
3 partitions (/, /home, and swap) are perfectly adequate for a home computer, in my experience and opinion.

---

### Post by sydbat on 2008-08-27
As a subsequent question, would it be advisable to consolidate all partitions into /home (example - 4 partitions set up in Windows to prevent XP corruption (music, email, etc)) or to just reformat those partitions into ext3 and reinsert the data?

---

### Post by Nythain on 2008-08-27
> **Forgotten Path said:**
> Thanks for the quick reply.

What exactly is the purpose of having a seperate /boot partition?  I read somewhere that it makes it easier to recover kernels, but if I have my data and settings on seperate partitions, wouldn't it just be easier to reinstall?

in all honesty, i cant really give a good reason or purpose, its just an old habit i've picked up. like others have mentioned, really not required, and your own logic would be correct also, so you really dont have to.

i think, back in the day, it was an added security issue, something to do with loading and mounting and unmounting and all that jazz, but meh, its been a long time.

---

### Post by Forgotten Path on 2008-08-27
Thanks alot everyone...

So, how about:

/
/home
/etc

Should I also have /usr/local?  That is where third-party applications are installed, isn't it?  Ubuntu puts its stuff in /usr, but /usr gets re-written with every new installation, correct?  So there would be no point of having a seperate /usr partition, since my stuff would get erased when the new installation mounted the partition as /usr.  But /usr/local sticks around right?  Or am I completely wrong?

I have a 160 GB (149.05 GiB) HDD.  How big should my partitions be?

/          5   GB?
/etc     500   MB?
/home    154.5 GB?

Is 5 GB large enough for root?  I like to have a lot of programs installed, but I'm not afraid to remove some less commonly used programs to make room and reinstall them later...  I also really have no clue how much space /etc needs, but I didn't figure its much.  If I had a /usr/local partition, it wouldn't need to be that big since there aren't many third-party programs, say 1 GB or so?

Thanks again for all the help...

---

### Post by sheroxe on 2008-08-27
dont forget about swap partition, you'll probably need about 2gb for this

---

### Post by impert on 2008-08-27
> Is 5 GB large enough for root? I like to have a lot of programs installed, but I'm not afraid to remove some less commonly used programs to make room and reinstall them later... I also really have no clue how much space /etc needs, but I didn't figure its much. If I had a /usr/local partition, it wouldn't need to be that big since there aren't many third-party programs, say 1 GB or so?

You've left out the swap partition.
5G might be ok for root, but I'd go for a little more.
I can't see the sense in the /etc partition, but others might.
Do you have Disk Usage Analyser? It'll tell you how much space is used and by what in your present set-up.
I'd leave a bit of space for later, if you have any to spare. Not formatted, if you like. You can always format it and expand into it later. If it's big enough to dump your whole /home folder into it, this can be a useful temporary backup. Or you might want to try another distro.
Partitions like /var were used to stop things like log files overflowing and filling the system with junk. Not necessary, I understand, in Ubuntu, which limits the size of these files.

---

### Post by Forgotten Path on 2008-08-27
Oops, forgot to include that.  2 GB should work perfectly, seeing as how I have 1 GB of RAM.  I heard it was good to have a swap partition on each end of your HDD, like this:

SWAP
/
/etc
/home
/usr/local
SWAP

so that Linux could write to whichever partition the heads are closest to, and that it also gives it a choice as to where to put stuff, improving the preformance.  But it seems to me having two swap areas would just be redundant and slow everything down unless you have a really big disk. *EDIT*  Seperating it up would make hibernation difficult or impossible as well, would it not? *EDIT*  But it should be at the inside of the disk, right?

SWAP        2   GB 
/           5   GB
/usr/local  2   GB
/etc      500   MB
/home     140.5 GB

Does that sound reasonable?  / would write to swap the most, followed by /usr/local (with its programs), and then /etc.  (or does /etc ever need to write to swap?)

---

### Post by Skorzen on 2008-08-27
> **snowpine said:**
> 3 partitions (/, /home, and swap) are perfectly adequate for a home computer, in my experience and opinion.

Agreed.
Actually, my / have 5 GB of total space, swap has 256 MB and the rest is at /home.

---

### Post by Forgotten Path on 2008-08-27
Well, before I discovered Linux and Ubuntu, my HDD became corrupted while I was running Windows (I'm not saying its Windows' fault, that just happened to be what I was running).  I ended up losing about 14 GB of music, 12 GB of video, and countless pictures that had sentimental value.  I know its not common, but now I'm paranoid, and I'd like to be able to reinstall without having to lose files or even settings.  Plus, I like to play around with things I probrably shouldn't play around with, and I'd like to have the comfort of knowing my settings and files will be there if I break my install.

I guess I just have a few more questions:

1) * Ubuntu puts its stuff in /usr, but /usr gets re-written with every new installation, correct? So there would be no point of having a seperate /usr partition, since my stuff would get erased when the new installation mounted the partition as /usr.*  <- Is this assumption correct?

2)  *But /usr/local sticks around right?*  <-  Is this assumption correct?  Are third-party apps all that common?

3)  And /etc sticks around to?  And would 500 MB be large enough? (or too large?)

4)  Does where I put these partitions on the disk have any effect on preformance?

And I like the idea of spare space.

SWAP  2 GB
/  5 GB
/usr  ?? GB*
/usr/local  1 GB *
/etc  500 MB *
/home  ## GB
FREE SPACE  ## GB

*depends on the answers I get above

---

### Post by rsambuca on 2008-08-27
For some reason, it appears you are intentionally trying to make things far more difficult than they need be.

/ - 5 to 10 GB
/home - 5 GB
/media - the rest for all your data
swap - 1 GB is plenty.

---

### Post by Forgotten Path on 2008-08-27
Ah, but I love difficult... It gives me something to do.  :lolflag:

---

### Post by rsambuca on 2008-08-27
OK, if you must, how about this...

/ 10 GB
swap 1 GB
/media 149 GB

Create separate folders on your /media partition for your /home, /etc, and whatever else you want.  Then create symlinks from your '/' directory to the folders on the /media partition.  This way, all of your settings will be safe on your /media partition should you ever want to re-install.  Then if you wish, you can re-install, and just recreate the links to your saved folders on the /media partition.

You obviously like to play and tinker with things, and this will give you the most flexibility.  I would like to point out though, you would probably learn a lot more by trying to fix things rather than keep re-installing. :)

---

### Post by panhandle on 2008-08-27
1) Remember the following points as set forth in Nemeth, Snyder and Hein as it pertains to creating partitions:

--If root partition is destroyed or corrupted, user data will likely be saved;

--The system "can continue to operate even after a user's misguided shell script fills up /home;

--Consider possible RAM upgrades when setting up a swap partition.

2) Yes, /usr does get rewritten with every fresh installation.

---

### Post by Forgotten Path on 2008-08-27
> **rsambuca said:**
> 
You obviously like to play and tinker with things, ...  I would like to point out though, you would probably learn a lot more by trying to fix things rather than keep re-installing. :)

That is very true, and if I do tear something up, I always try to fix it, but my computer is used for school, mainly, and if I have a term paper due I need it back up and running fast, faster than I could figure out how to fix it.:rolleyes:

If I used symlinks, could I symlink to /usr and get all my programs back after a reinstall?  Or does it not work that way?

---

### Post by rsambuca on 2008-08-27
I create a /home directory on my /media partition and link to it.  It works very well.  It should work with /usr, but you just have to make sure the permissions are set correctly.  To be honest, I still don't know why you would need to save /usr from an old install.

---

### Post by Forgotten Path on 2008-08-27
I'm just wondering if saving /usr would prevent you from having to reinstall programs.... but I have a feeling it won't.  I think I can deal with that if saving /etc will save me my settings.

So, how about making a /home partition and then a folder on /home called etc, which I can symlink to from root.  Then I'll have my files and all my settings saved on one partition.  And if I find that I'm installing alot of third-party stuff, I'll also symlink /usr/local onto my /home partition.

---

### Post by tad1073 on 2008-08-27
Partition1: Swap
Partition2: /
Partition3: /home
Partion4: Media or /mnt

For me it is as follows:

Disk0, Partition1: Swap
                    Partition2: /

Disk1: /home

Disk2: Media

---

### Post by mcduck on 2008-08-28
Why would you make /media or /mnt a separate partition? They are both places where other filesystems get mounted into, not places where you would actually put files. That means that they don't really need take any space,and they contain nothing you would need to save. Just mount points for other disks and such..

I _can understand creating a separate storage partition (in addition to home) and mounting that _inside_ /media or /mnt (or your home directory), but I see no point in making /media or /mnt itselt a separate partition..

---

### Post by rsambuca on 2008-08-28
> **mcduck said:**
> Why would you make /media or /mnt a separate partition? They are both places where other filesystems get mounted into, not places where you would actually put files. ...
Why not?  I put a lot of files in /media.  My audio library, my video library, etc.  I access it from all of my different distros.  Thousands of files in it, actually.

---

### Post by mcduck on 2008-08-29
Well, I have the habit of using the directories for the purposes they are made for. /media for removable medias (as they will automount there anyway). I'd think it would be rather confusing to use the mounting directory as storage space.. Even more so for somebody asking for help with partitioning.. :)

Besides, actually writing something into /media itself would require either root access or changing it's ownership/permissions, and I really wouldn't do that for any system directory.

---

### Post by rsambuca on 2008-08-29
> **mcduck said:**
> Well, I have the habit of using the directories for the purposes they are made for. /media for removable medias (as they will automount there anyway). I'd think it would be rather confusing to use the mounting directory as storage space.. Even more so for somebody asking for help with partitioning.. :)

Besides, actually writing something into /media itself would require either root access or changing it's ownership/permissions, and I really wouldn't do that for any system directory.
Your system is obviously set up differently than mine.  My /media partition is for... my media files.  Imagine that!  I have never had to change any permissions and my media partition is accessible by all users and across all distros.

---

### Post by mcduck on 2008-08-31
Never ever heard of using /media that way..

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/media.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/media.html")

Anyway, that sounds like useful configuration as well. ;) But where do all the removable drives and CDs mount then?

---

### Post by rsambuca on 2008-08-31
They still go into the /media partition.

---

### Post by cyberkost on 2008-08-31
Forgotten Path, thank you for a good thread!  I have a need similar to yours -- a partition setup that would allow me the flexibility to wipe out everything except the data (or whatever might be there) on "/home".  I've converged on "/boot" (doing RAID 10, so I need this), "swap", "/", and "/home" being the partitions I want (with all these "tmp", "var", "usr", "usr/local", "etc" being directories under "/").  As I mentioned I'm thinking of doing RAID 10 over 4 320GB disks, but from partition size perspective I'm thinking of this as an installation on a single 640GB disk.  I'm fairly certain that "/boot" is going to be fine with 50-100MB, but how do I split the rest of the space between "/" and "/home" for Ubuntu 8.04 Desktop installation (I'll be adding LAMP, SAMBA, etc. later on)?  40/600?  140/500? 240/400?

Also, for RAID it seems to be recommended to have an unraided partition on each physical disk (b/c Ubuntu is supersmart about using them optimally)...  I have 4GB RAM and 512MB video (but I'll be installing 32-bit Ubuntu) -- how large should my swap partitions be (assuming I'll have 4 of them).  Will it have any effect on my computer's ability to hibernate?

---

