---
title: "Ubuntu back up and restore type thing?"
date: 2024-10-18
forum: New to Ubuntu
---

### Post by shadowtabby on 2024-10-18
Heyo!!!,

SO as we know I am new to ubuntu, and I am a bit affraid that I might mess something up.  SO I am wondering, does ubuntu have a back up and restore thing as well?  OR will I have to just reinstall ubuntu if I some how mess things up?

---

### Post by bobunderwood99 on 2024-10-18
Look at backintime-qt (graphical) and timeshift.

---

### Post by shadowtabby on 2024-10-18
Heyo,

Thank you.  I am installing time shift now.

---

### Post by TheFu on 2024-10-19
> **shadowtabby said:**
> Heyo!!!,

SO as we know I am new to ubuntu, and I am a bit affraid that I might mess something up.  SO I am wondering, does ubuntu have a back up and restore thing as well?  OR will I have to just reinstall ubuntu if I some how mess things up?

There are 50 options. Each has pros and cons.

Main thing is to backup stuff to different physical media. For a beginner, that is usually handled easiest with a $40 USB 2TB HDD.  Get one that has external power, so it isn't slow.

**Timeshift** is for the OS.  If you don't have to do a snapshot daily, have it do one at least weekly, just before you run your normal weekly patching.  Patching more often than once a week is probably too often.

**Back-In-Time** is for your $HOME directory and for all the human-users HOME directories and typical data (documents, images, etc.).  It uses hard-links to minimize the required storage for each "version" it makes.  It is pretty efficient.  The technique uses has been around in Unix for 40 yrs.  You can learn about hardlinks and symbolic links on wikipedia. Good to have knowledge about both of those methods.

You need both types of backups when you are new-to-Linux. The combination of Timeshift and Back-in-Time is a good one for most people.

Beware that timeshift restores don't always work, so be certain you test it BEFORE you count on it and before you really trust it.  I don't know how much you know about using virtual machines, but that is a great way to test a small backup/restore process, so you aren't surprised when it truly is important. It will also build confidence in the solutions that you choose for this need.

When you become more advanced or start setting up servers (no GUI on a server), then you'll need a different backup solution. There are many.  Of course, using other solutions often means either less flexibility or a more complex restore process.  Restores under timeshift are pretty easy to get the OS back as it was.  Timeshift isn't perfect.  There are issues where it is possible to have corrupted backups under some specific situations.  To ensure no corruption is possible, there are other methods that add complexity to an OS setup.  Best avoided.  There are always trade-offs, it seems.

I setup Back-in-Time on my 80+ yr old mother's Linux computer. She loved it and it was easy for her to understand.  Timeshift didn't exist back then.

---

### Post by Norm24 on 2024-10-19
+1 for Back-In-Time.

Easy enough to use and for me has been completely reliable.

---

### Post by shadowtabby on 2024-10-19
Heyo,

Long reply hehe.

Timeshift doesn't always work?  Ooffff, I want something that does, hehe.  Thank you for that heads up.

What if I remove timeshift and use back in time?

 No no I am only using ubuntu on my gaming PC.  So I really don't want to screw things up. Hehe.  So far I am enjoying the learning and find my PC is going faster too.  I don't have old things in my PC either well maybe the i7-8700.

---

### Post by TheFu on 2024-10-19
Most software failures are due to incorrect setup or incorrect expectations.
Most people find that using both Timeshift for the OS and Back-in-time for their data is the best option for simplicity of restore of the OS post-disaster and having really great versioned backups of their personal settings and data.

If you use just one or the other, then you'll need to specifically set them up in the method you require.

I've never seen timeshift fail myself, but I don't use it.  I've only seen it used by others and I've seen a demo of the entire setup including a full restore using both timeshift and back-in-time.  Did I mention that I setup back-in-time for my mother's PC?

If you don't understand, go find some youtube videos about each tool and watch someone actually set them up, listen to the extra tidbits of knowledge they convey.  Before you ask, no, I can't recommend any.  I've not needed them.  

I'm fairly experienced with Linux (over 30 yrs). Actually, I use LVM to take volume snapshots then use rdiff-backup to "pull" backups to my backup server, but that's much more complicated than 99% of the people in these forums want.

---

### Post by shadowtabby on 2024-10-20
Heyo,

Okies maybe I don't need it then, because where you said "[COLOR=#000000]Most software failures are due to incorrect setup or incorrect expectations." I am very very very careful with what I do, and if I am not sure then I wont do it.

Wait so I can do back ups and have it backing up to my NAS???
[/COLOR]

---

### Post by TheFu on 2024-10-20
> **shadowtabby said:**
> Heyo,

Okies maybe I don't need it then, because where you said "[COLOR=#000000]Most software failures are due to incorrect setup or incorrect expectations." I am very very very careful with what I do, and if I am not sure then I wont do it.

You need BOTH timeshift and something link Back-in-Time.  You'll thank me later.

> **shadowtabby said:**
> 
Wait so I can do back ups and have it backing up to my NAS???[/COLOR]

Depends on the capabilities of your NAS and how files are stored there.  In general, it is a bad idea to use storage that client machines can access over the network for backups.  Why?  Because when they get malware/cryptoware, they have access to the NAS storage and can make all the data there they can access useless.

---

### Post by shadowtabby on 2024-10-20
> **TheFu said:**
> You need BOTH timeshift and something link Back-in-Time.  You'll thank me later.



Depends on the capabilities of your NAS and how files are stored there.  In general, it is a bad idea to use storage that client machines can access over the network for backups.  Why?  Because when they get malware/cryptoware, they have access to the NAS storage and can make all the data there they can access useless.


Ah okies I know I have my NAS access controlled with a firewall, which seems pretty good and need to have an assigned IP address on the router and allowed in the firewall.  Only mine and my sisters devices are allowed to access it.  On the router.  I restricted that to mine and my sisters computers.

---

### Post by TheFu on 2024-10-20
> **shadowtabby said:**
> Ah okies I know I have my NAS access controlled with a firewall, which seems pretty good and need to have an assigned IP address on the router and allowed in the firewall.  Only mine and my sisters devices are allowed to access it.  On the router.  I restricted that to mine and my sisters computers.

Think about it.  If the machine pushing the backup data has malware, any storage, anywhere, that it can access will be destroyed.  You don't want backups to be accessible by the likely cracked system.  A firewall is fine, but hardly the solution.  

What happens when your computer or your sister's computer have cryptoware on them?  Any storage they can access will be corrupted.

---

### Post by shadowtabby on 2024-10-20
> **TheFu said:**
> Think about it.  If the machine pushing the backup data has malware, any storage, anywhere, that it can access will be destroyed.  You don't want backups to be accessible by the likely cracked system.  A firewall is fine, but hardly the solution.  

What happens when your computer or your sister's computer have cryptoware on them?  Any storage they can access will be corrupted.


My sisters PC has kapesrky on it, and yeah kaspersky is really good here, and we are not going to have a debate about this (because americans love to argue about kaspersky and I am really not in the mood for arguements).

My PC is unbuntu, and now pro.... I thought that was supposed to hardern things like that? (I am still learning about ubuntu so it's taking a little time for this, only had it for 3 days).  Like I hear there is malware for linux, but no where near as much as windows, and the only windows PC's there are here is my sisters.  She doesn't do much things apart from games and typical things.  I have taughter her to only get games from trusted sources like steam, or epic or something.  Also our DNS we pay for stops a lot of things as well (yes I tested by going into malware etc sites on purpose).

I'm not completely knew to computers.  Just linux.  Cause I have been a windows user all my life till now.

---

### Post by TheFu on 2024-10-20
You'll need to unlearn much of what MS-Windows taught you.  Linux isn't Windows.
[https://linux.oneandoneis2.org/LNW.htm](https://linux.oneandoneis2.org/LNW.htm) tries to explain the big differences. Most of the difference is philosophical.

Kaspersky is only a concern due to Russian ties and the ability of that govt to apply pressure to family still in Russia to force the company to do things they would never do. The company has tried to minimize their Russian ties, but we see coercion from a few countries.  Those biases will remain on all sides. How can they not?

I don't know anything about unbuntu.

---

### Post by shadowtabby on 2024-10-20
> **TheFu said:**
> You'll need to unlearn much of what MS-Windows taught you.  Linux isn't Windows.
[https://linux.oneandoneis2.org/LNW.htm](https://linux.oneandoneis2.org/LNW.htm) tries to explain the big differences. Most of the difference is philosophical.

I don't know anything about unbuntu.

Heyo,

Yeah I agree, been using pc's since 5 (mainly for gaming, dad got me into it.) and that was only windows.

So I do agree with you, I do need to unlearn a lot from MS, and changing to linux cause I am sick of ms's crap, was a huge change for me.  

Thank you for your honesty about not knowing anything about ubuntu.

---

### Post by ian-weisser on 2024-10-20
> **shadowtabby said:**
> OR will I have to just reinstall ubuntu if I some how mess things up?


Nothing wrong with reinstalling.
Nothing wrong with messing things up, either. It's one way to learn.
Lots of people reinstall for good reasons. Messing things up is just one good reason. There are others.

Using my notes, I can reinstall, restore my data from backups, and restore my customizations in about 20 minutes. I lose only the data since my last backup. So I backup before anything risky, then I lose nothing at all.

You're already halfway there: You know how to install, so you know how to reinstall.

It's a bit like Minecraft or a lot of other games: Try dying and respawning a few times, and it's not scary any more. And you learn a bunch of good habits along the way.

---

### Post by shadowtabby on 2024-10-21
> **ian-weisser said:**
> Nothing wrong with reinstalling.
Nothing wrong with messing things up, either. It's one way to learn.
Lots of people reinstall for good reasons. Messing things up is just one good reason. There are others.

Using my notes, I can reinstall, restore my data from backups, and restore my customizations in about 20 minutes. I lose only the data since my last backup. So I backup before anything risky, then I lose nothing at all.

You're already halfway there: You know how to install, so you know how to reinstall.

It's a bit like Minecraft or a lot of other games: Try dying and respawning a few times, and it's not scary any more. And you learn a bunch of good habits along the way.


Thank you.  Ig maybe I don't need the backup and stuff, because all my photos etc goes on my nas anyway.  And I do get emails if anything is up with the nas, security scans are every night.

---

### Post by TheFu on 2024-10-21
If you don't have 3 copies on 3 different physical media, then you don't have any backups.  That's the rule.  And a RAID mirror is counted as 1 copy.

We all start out making ZIP files and calling those "backups".  then we often start copying files using a file manager to other storage and call that a "backup".  The flaw with these is that we humans are lazy and quickly decide that we just did a backup last week or last month or 8 months ago and that's good enough.  

Backup tools exist to make extremely fast and storage efficient backups either daily or weekly.  These can be automated, but often, we  - being lazy humans - don't bother with the automation part.  I had a tape drive, but that was extremely slow, noisy and the tape media wasn't cheap.  Because it is a linear storage format, getting back a few files off tape was a hassle too.  

In the early 2000s, I was using **rsync** to mirror all the storage on a system.  1 copy to another HDD.  It wasn't automatic, but I did mostly run my rsync script once every 1 or 2 weeks.  That became every month, then every 6 months.  Life got in the way and I couldn't remember the last time I'd run the script, so I ran it 1 Saturday morning.  Talk about lucky.  Early, the next Saturday morning that computer was hacked.  The hacking method wasn't silent, so I received thousands of notifications by the time I got up to check email.  Because I had made a backup (really just 1 mirror) 7 days before, I was able to compare everything between the two disks and see what had changed and what had not changed.  It was extremely clear who they'd hacked into the system and where they'd setup their beach to attempt to get more access.  I was very lucky.  Of course, a few other files had also changed, but I remembered those documents that I'd been editing that week, so those were never a concern.  If I didn't have a recent mirror, I'd have been screwed and not been able to trust any of the files, including data files, on the system.  Pure luck.  

After removing the attacker's beachhead files and patching the program they'd used to get into the system at all, I immediately added my manual rsync script to happen automatically, once a week.  rsync is great at all sorts of things, but it really isn't a great backup tool.  rsync does about 80% of what a great backup tool should do, but for almost ZERO effort, it isn't hard to setup a real backup tool that does versioning for very little extra storage.  90 days of versioned backups needs just 1.3x the space that a mirror needs.  So if you are backing up 100G of stuff, for 90 days of daily, versioned, backups, just 130G of storage is needed (that's an estimate).  Doesn't that seem like a bargain?  Also, once the first backup is made, all the following backups take just a few minutes.  Most of the backups of systems here take less than 2 minutes a day to finish.  

I backup about 10 systems every night.  The backups for last night started at ....
```
INFO: Backup Start:	2024-10-21-00:03:01
```
and the last backup of the last system ended at ....
```
EndTime 1729484549.58 (Mon Oct 21 00:22:29 2024)
```
A little math says that in less than 20 minutes, I backed up about 10 systems.  Again, that seems like a bargain to me.

I've posted example backup scripts here, but *back-in-time* will easily do about the same thing.

Versioned backups are important for a number of reasons. You can look up why.

---

### Post by ian-weisser on 2024-10-21
> **TheFu said:**
> If you don't have 3 copies on 3 different physical media, then you don't have any backups.

TheFu is, as usual, spot-on with a great lesson.

This site is soaked in the tears of folks who lost forever their only copy of beloved family photos and other valuables.
Rarely lost by Ubuntu. Commonly lost by folly, fire, and/or forgetfulness.

It may not be a big consideration right now as you start out and learn.
But, like regular visits to the dentist, it's one of those good habits you want to develop.

---

