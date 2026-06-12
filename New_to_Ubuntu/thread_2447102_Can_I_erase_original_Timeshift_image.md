---
title: "Can I erase original Timeshift image?"
date: 2020-07-12
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-12
Hello everyone,

Is it safe to erase the original Timeshift image?

How does that work if each subsequent snapshot only saves the changes made since the last?

Do I have to erase *all* snapshots and create a new original one?

Thanks!

---

### Post by TheFu on 2020-07-12
Which _mode_ are you using Timeshift?  rsync or btrfs?

Where do the hard-links all point?  In theory, if the reference count is non-zero, then the data that any link points at will be retained.  This has worked for 40+ yrs.

[https://github.com/teejee2008/timeshift](https://github.com/teejee2008/timeshift) tries to explain.  In my skimming, I really hope people that use btrfs mode are also doing real backups. File system snapshots are excellent for getting a file system quiesced prior to running a backup, but no way, no how, do "snapshots" replace running actual backups.  After creating a snapshot, be certain to delete the snapshot after ... at some point or the storage could fill up with old data that can't be modified, is still marked used, but only by that snapshot made 8 months ago.  The blocks in a snapshot are frozen.

BTW, Timeshift recommends using other, similar, hard-link-based tools for some specific needs.

---

### Post by GhX6GZMB on 2020-07-12
I use Timeshift in rsync mode.
Yes, you can basically erase any Timeshift snapshot, **_provided you do it with Timeshift._**
The original snapshot will be synchronized with the next one before erasing. BUT: be careful if you have differences in "Settings/Users" between the snapshots. It'll work, but you may lose some files due to discrepancies.

If this is true in btrfs-mode, IDK.

---

### Post by jcdenton1995 on 2020-07-16
[QUOTE=TheFu]Which _mode_ are you using Timeshift?  rsync or btrfs?

Where do the hard-links all point?  In theory, if the reference count is  non-zero, then the data that any link points at will be retained.  This  has worked for 40+ yrs.[/QUOTE]

Hi,

I'm using rsync.

In terms of where the hard-links point to I'm afraid I don't know enough about how Timeshift works to go into any detail, sorry. I'm about to make a new thread on how I borked my install faffing around with Timeshift data so maybe more can be revealed there.

---

### Post by jcdenton1995 on 2020-07-16
> **ml9104 said:**
> I use Timeshift in rsync mode.
Yes, you can basically erase any Timeshift snapshot, **_provided you do it with Timeshift._**
The original snapshot will be synchronized with the next one before erasing. BUT: be careful if you have differences in "Settings/Users" between the snapshots. It'll work, but you may lose some files due to discrepancies.

Thanks, I guessed that erasing snapshots with Timeshift would perform extra housekeeping to keep more recent snapshots useable. Can you tell me more about what you mean by users / settings? do you mean if you have added users since making a snapshot, or edited conf files?

---

### Post by TheFu on 2020-07-16
> **jcdenton1995 said:**
> Hi,

I'm using rsync.

In terms of where the hard-links point to I'm afraid I don't know enough about how Timeshift works to go into any detail, sorry. I'm about to make a new thread on how I borked my install faffing around with Timeshift data so maybe more can be revealed there.

You mean you are using timeshift in rsync-mode, correct?  Please try to be technically accurate since "I'm using rsync" means something completely different.

You didn't go and explore the TARGET area just to see what's down there?  Just do it carefully - don't ever modify anything created as part of a backup tool, but looking around is fine.  It it is anything like Back-In-Time, then it is just a bunch of cloned directories stored below groups of timestamp directories which hold each "snapshot" - though not really "snapshots" in the official use of the term as a file system capability like ZFS, LVM, BTRFS provide.  I'd prefer using the term "time-cloned mirror"

Go take a look. See what's there.

"User settings" are the setting made by a user and stored in their HOME directory somewhere.  I would expect Timeshift would have a config file stored in ~/.config/Timeshift/ somewhere which any settings.

---

### Post by GhX6GZMB on 2020-07-16
I didn't write "users/settings", I wrote "Settings/Users", which is a menu in Timeshift.

First, you need to understand that Timeshift is designed to roll back the system settings to a previous (working) state, meaning restoring configuration and settings files among others.
It's NOT designed for doing user file backups (documents etc.), that's a completely different issue.

The "Settings/Users" menu let's you select whether you want to backup or restore the /root and $HOME directories. Default is "no", which is as it should be. You can select "yes" which is a bad idea.
But it does have an intermediate setting, which is to backup and restore **hidden** files in /root and $HOME, which I've found to be a good idea.

_My comment in post #3 was about changing these setting from backup to backup._ IDK if it creates problems, but rather safe than sorry. Stay with one setting.

A last comment: I'm very, very impressed with rsync. But as a 1-year old Linux/Lubuntu user, it's just does too much, which is why I need the help from the Timeshift package. I know there are incredibly experienced users that can hammer out the same result in a CLI command, but that's way over the head of most users.

I attach a picture of the Timeshift menu I mean.

---

### Post by jcdenton1995 on 2020-07-16
> **TheFu said:**
> You mean you are using timeshift in rsync-mode, correct?  Please try to be technically accurate since "I'm using rsync" means something completely different.

Yes that's what I mean, I'm using Timeshift in rsync-mode as opposed to BTRFS

> You didn't go and explore the TARGET area just to see what's down there? Yes I did and it was pretty much how you describe, a timestamped directory containing a few files as well as a directory that was pretty much a copy of a root directory, although the folders within it didn't contain *all* the contents that their counterparts in my actual root directory did.

I'm going to read into hard / soft links tomorrow as I don't fully understand how that works beyond the basic difference between them.

---

### Post by jcdenton1995 on 2020-07-16
Ah right I understand now, I had seen that you can backup hidden files in your home directory which I thought seemed like a good idea.

So what your saying is that if I was to make a backup with Timeshift set to backup my hidden directories, and then subsequently made a image set to *not *backup these files, then that could cause a loss of some files...

---

### Post by GhX6GZMB on 2020-07-16
> **jcdenton1995 said:**
> 
So what your saying is that if I was to make a backup with Timeshift set to backup my hidden directories, and then subsequently made a image set to *not *backup these files, then that could cause a loss of some files...

No, what I'm saying is: _be consistent_. Timeshift will handle the issue without problems, but if you do backups/restores with or without the hidden files arbitrarily, you'll have old and new files mixed and it might get worse along the way. This is a user issue, you being the user in command. My phrasing earlier was not good, I meant data, not files.

One more recommendation from my side: include the $HOME/Desktop directories in your backups. This will save you from having to rebuild the desktops for every user after a crash (or after doing something you shouldn't have done).
Screenshot attached:

[ATTACH=CONFIG]286480[/ATTACH]

---

### Post by TheFu on 2020-07-16
If you need two different tools/methods to have a system backup, seems like using a different tool would be much easier. Why do something twice?

---

### Post by GhX6GZMB on 2020-07-17
> **TheFu said:**
> If you need two different tools/methods to have a system backup, seems like using a different tool would be much easier. Why do something twice?

Perhaps, depends on your working style. System image backups are really only needed before I make changes to the system.
Data backups are needed regularly, thus my split between user data and system data. But everyone has his own preferences.

And I'm not a millionaire with my own data center and unlimited capacity.

---

### Post by TheFu on 2020-07-17
> **ml9104 said:**
>  
And I'm not a millionaire with my own data center and unlimited capacity.

My daily, versioned, backups, for about 15 systems fit onto a single 2TB USB3 HDD.
```
$ cd /Backups
thefu@romulus:/Backups$ df -Th .
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sdf1      ext4  1.4T  1.2T   87G  94% /Data/1.5T

```

Oops.  Sorry, that's a 1.5TB HDD.

If we don't use image-based backups, backup storage is really efficient.  This doesn't include any media files either.  It only includes the files necessary to restore each system to the same working point it was at the time of the backup. Media (music, videos) are handled separately and stored on a different system, never on a desktop. Additionally, I keep 90D or more of backup versions based on the risk for the system. 

The email gateway server has more versions, but hardly any data at all. It is just config files really.
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun Jul 12 01:30:02 2020         63.0 MB           63.0 MB   (current mirror)
Sat Jul 11 01:30:03 2020         13.3 KB           63.1 MB
....
Sun Mar 15 01:30:02 2020         3.72 KB           63.4 MB

```
That report was created last Sunday. It was a fresh server then and is building to 180 days of versioned backups.  Less than 65MB for all those versions seems like a bargain to me.

---

### Post by GhX6GZMB on 2020-07-17
Right. And I have a laptop with 240 GB for everything.
Great for you that you have terabyte storage, but...

---

