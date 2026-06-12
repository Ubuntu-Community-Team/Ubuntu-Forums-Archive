---
title: "Update question"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by CelainaF on 2012-05-10
I am as new and unfamiliar with Ubuntu as it gets. I'm aware of the newest update becoming available, and I'm curious as to whether or not an update will reset my system (meaning be rid of all my files and the like) such as upgrading with Windows, or if Ubuntu is amazing and special and I won't have to toss my hard drive onto a cloud again. 

I know this is probably a dumb question and I apologise.

---

### Post by ammofreak on 2012-05-10
Hi ):P
Upgrading to a newer version of Ubuntu will not erase one's computer configuration. For example, if one is using Cinnamon as a desktop instead of Unity, then after the upgrade, one will still be using Cinnamon. Basically, hard drives, wifi, webcams, etc., should still work.I hope this answers your question...:)

PS: as one being new to Ubuntu, I would suggest becoming familiar with the version one has initially installed. Your Update Manager will notify you of any updates automatically. Use the software that interests you, solve any problems that might arise, learn from any of the many websites (Google it:popcorn:) teaching Ubuntu Linux. Then, and only then, will one be ready for the next step in the journey to perfect computing. Listen well [COLOR="SeaGreen"]Grasshopper[/COLOR]:lolflag:!!!

---

### Post by CelainaF on 2012-05-10
Haha, thank you very much. I really appreciate it. :)

---

### Post by deadflowr on 2012-05-10
There is no such thing as a dumb question. Updates and upgrades  will not wipe out your files(although if, and this is a big if, the update runs afoul somehow, it can bork your system.)
As a precaution to this it is highly recommended to backup your files. Either through the default(if your on ubuntu 12.04 it is deja-dup)or through a backup program found through the software center.
If your system does bonk out, you can use the liveCD to gain access to your files, just remember to only select TRY and not install. Then from there you can decide whether to copy them or not.
If you're really worried about having to do that, then learn about patitioning schemes and how to set a home partition. That way if the system crashes you can reinstall without fear of losing your personal data. 
I hope this relieves some of your worries.

---

### Post by CelainaF on 2012-05-10
Thank you :)

---

### Post by Lateralis on 2012-05-10
To echo what Ammofreak has said, you should be able to upgrade without wiping everything.  You can do the upgrade one of a couple of ways, but in any situation I would still strongly recommend you perform a backup of all of the files that are important to you on to an external storage medium.  An upgrade will not tamper with any of your personal files in your /home directory but:

1) keeping a good backup of your data is good practice
2) in the event the upgrade isn't smooth and you find yourself in a position of needing a fresh install, everything is already backed up. 

As I say, an upgrade should work out OK - I have previously never had any troubles upgrading and on one machine I manually upgraded 2 or 3 times - but there is a chance something will break due to the nature of the upgrade.  


TL;DR Ubuntu *is* magical and special and amazing (relative to Windows) and you should be able to upgrade without "tossing your hard drive into the cloud", but still perform a complete back up of your personal files before doing so just in case.

---

### Post by 3rdalbum on 2012-05-10
> **deadflowr said:**
> 
If you're really worried about having to do that, then learn about patitioning schemes and how to set a home partition. That way if the system crashes you can reinstall without fear of losing your personal data. 
I hope this relieves some of your worries.

Just a couple of notes:

1. Reinstalling Ubuntu doesn't necessarily mean losing the data in /home. The Ubuntu installer can preserve the contents of your home directory even if it's on the same partition as the rest of the system (/). As long as you choose "Upgrade" or "Something else" and don't elect to format the partition, you'll be able to preserve /home.

2. Having /home on a different partition, or better yet on a different hard disk altogether, does make things a little more reliable. If you get a filesystem crash on /, then your personal documents and settings in /home are not affected. It also seems to make it less likely that you will have filesystem damage at all. When I used to have a Mac (OS 9) this was the only way I could keep my computer running for a year or longer without having to do a reinstall.

Note, however, that I've never experienced a filesystem crash on Ubuntu, not even on my computers with just one partition. Linux seems to be superbly reliable at maintaining the integrity of the filesystem, and fixing any minor damage without causing more problems. I'd trust my life on my data being on my Ubuntu hard disks.

---

### Post by deadflowr on 2012-05-11
@3rdalbum

That is sound advice about reinstalling, and as far as reformatting, that seems to be a lingering effect of windows;As I have reinstalled windows in unformatted drive come out worst then before.

As for filesystem crashes, I wholeheartly agree. I have never had a serious filesystem crash. Chances are if your filesytem is crashing something more serious is afoot;ie a physical problem such as a dying hard drive.

---

