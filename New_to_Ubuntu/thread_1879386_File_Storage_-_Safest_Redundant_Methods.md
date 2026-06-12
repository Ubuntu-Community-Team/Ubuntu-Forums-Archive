---
title: "File Storage - Safest Redundant Methods?"
date: 2011-11-11
forum: New to Ubuntu
---

### Post by Kellemora on 2011-11-11
Hi Gang

I asked this on our web masters forum and no one commented, so I'll pester you guys, hi hi.....

I'll start by saying, due to the massive loss of countless years of irreplaceable data, I'm terrified of even Raid 5 Systems now, unless something has changed that I don't know about.  We had a controller card go bad and it was not replaceable, so everything current and not physically backed up elsewhere was lost.

Although I run triple redundant storage, in-house - off-site - and off-premises, plus a manual mirror physically carried and stored off-site.
We had a few glitches in a mirroring system that deleted several files, which will happen with any system occasionally, no way around that.
You delete a file and it gets deleted from all the mirrors.  That's why we make manual physical copies of everything and store them.

I'm going to be replacing my entire file storage systems and methods very soon, hopefully before the end of the year and am looking for recommendations on which way to go.

I've tried a NAS System, it's way to slow, it uses it's own filing system and controller card.  As before, if that card goes, we've lost everything.

I don't like to use what are known as backup sets.  I prefer exact mirror copies of my data.  EG:  Main File Server where we do our work, copied to a in-house Mirror, copied again to an off-site Mirror, copied again to an off-premises mirror.
In-house = same building.
Off-site = different building same property.
Off-premises = different physical location, different city and state.

Normally we have 4 to 6 users storing data daily, but maintain the data for several users.  EG:  We have a Master Photo File Database where Sorted Images are placed by one of the 4 users for any number of family members.  Plus accounting packages for various business enterprises.  And of course all of our personal data.  
Roughly 2 Terrabytes is what we currently have in File Storage Systems.

I had asked at the webmasters web site because web sites are storing data from hundreds to thousands of users daily (some in the millions of users) and can't afford to lose any of those users data.
I'm sure the files are saved across numerous file servers on the big companies.  But what about the little guys with only 25 to 100 users that are hosting their own web sites?
Even those that use Hosts still have to maintain and update their programming from time to time and upload the main program files.  I assume they also maintain the databases and users data?????

I'm just looking for something totally reliable.  As I said, I had a Hot Swap RAID 5 System that I did run backups from, but we still lost a lot of data when it's controller card went south.  Some of the backups failed due to a glitch in the software for same, so when we went to restore everything we found the backup had failed in some areas and deleted much data we thought was saved.  We now manually back up each important folder to a totally different system and carefully check it.  But even doing this causes problems and a lot of manual work if the main file becomes corrupted.

Simply put, I just have too much data to store now to be manually doing anything anymore.  Over 120,000 files on individuals each with secondary files containing sorted data.

What do you consider the safest method of file storage currently in use?

If it's a RAID System, is there one with standardized controller cards so if the systems card fails, it can be replaced, or the drives swapped out to new cabinets?  I've seen all the ads for storage systems, but none answer my most basic question, what if that controller card fails.

Thanks for any and all input!

TTUL
Gary

---

### Post by QLee on 2011-11-11
[QUOTE=Kellemora]...
Thanks for any and all input!...[/QUOTE]
The advice I have always seen is that if you choose to use hardware RAID, you buy a second controller exactly the same as the first at the time you set it up so that there is a spare available when the first one fails.

Maybe you should consider using software RAID.

And also maybe you should consider asking a moderator to move this from the absolute beginner talk sub-forum, in case you have further questions. Signal to noise ratio here might be unacceptable if you are serious about the question.

---

### Post by drdos2006 on 2011-11-11
You might want to lok at Nextenastor.

[http://en.wikipedia.org/wiki/Nexenta_OS](http://en.wikipedia.org/wiki/Nexenta_OS)
[http://www.nexentastor.org/boards/2/topics/1002](http://www.nexentastor.org/boards/2/topics/1002)

[http://v-reality.info/2010/06/using-nexentastor-zfs-storage-appliance-with-vsphere/](http://v-reality.info/2010/06/using-nexentastor-zfs-storage-appliance-with-vsphere/)

I understand that Ubuntu server will be incorporating some licensed version for Ubuntu 11. There are a few advantages that I read about compared to straight RAID setup.

regards

---

### Post by The Cog on 2011-11-11
To my mind, you cannot trust RAID for this. A software hiccup or user error could delete the lot, and that would be faithfully replicated to give you lots of expensive empty disks. We use USB drives to copy our data on to. We keep them off site, and rotate a number of them so we have several versions of different ages - hopefully long enough to discover a monumental wipeout before the oldest version gets re-used. rsync can speed up the backup process - it skips files that have identical sizes and timestamps.

---

### Post by Kellemora on 2011-11-12
Thanks for the replies!

The Cog, it then seems I guess, that the way I have been doing it, using Portable External USB Hard Drives all mirrored together, is still the best solution.  Plus the manually made mirror of individual files.  I do know not to overwrite known good copies until the new copy is double or even triple checked.  EG: our accounting files dating back to 1977.

Also, since I've accumulated so many old IDE drives over the years, I have an external IDE connection and use these old drives to store original data copies and keep them on dusty old shelves, clearly marked as to what they contain.

For those who like some Humor in their lives.  It was only last year 2010, that we finally copied all of our Ancient Master Individual Files from 5-1/4 Floppies over to duplicated CDs and the NAS before the last of our 5-1/4 readers died.  We did not trust 3-1/2 floppies as data loss was too high on them.  We even used Single Sided Single Density 5-1/4s punched so we could use both sides of the media and never lost a bit of data from those old reliable black jacketed floppies.
They didn't hold much, but what they held was very important and they were reliable!  Even so, we had three copies of each one and they took up a lot of shelf space, hi hi.....

If anyone knows why I cannot PUT files somewhere using RSync, but can FETCH files with RSync for storage with no problems, that problem has been bugging me ever since I started using Ubuntu back in 2008.

TTUL
Gary

---

