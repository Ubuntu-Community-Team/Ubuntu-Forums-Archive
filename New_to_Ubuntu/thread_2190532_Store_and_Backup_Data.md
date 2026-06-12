---
title: "Store and Backup Data"
date: 2013-11-27
forum: New to Ubuntu
---

### Post by partloer on 2013-11-27
Just wondering what people do to store and backup their data...RAID, NAS, Cloud, etc?

The end result is to figure out what is the best (balance: simplicity, redundancy, cost) way to store and backup photos / videos.

---

### Post by bashiergui on 2013-11-27
Deja Dup ships with Ubuntu, it's pretty simple to back up to UbuntuOne.
[http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/](http://www.howtogeek.com/108869/how-to-back-up-ubuntu-the-easy-way-with-dj-dup/)

Being of the paranoid variety I don't trust "The Cloud" (aka someone else's server). I use rsync to backup to a second hard drive.

---

### Post by DuckHook on 2013-11-27
***ALERT***
The way I do it is probably overkill for most people.

Given that fair warning:

I have three NASes. All are cheap as borsch, set up with NFS and each component runs on less than 2 Amps. Setting aside the system details (unless you really want them), two are set up to run daily cron jobs using rsync so that they mirror each other. This means that if any one of them kicks the bucket, I only have to switch to the other and it's as if nothing has happened. The drawback with automatic mirroring is that unintended deletions and corrupted data get mirrored as well. This is why the third NAS is *not* automirrored, but must be synced manually, usually once every two weeks. If I have any concerns about the data, I address those before running rsync.

In addition to above, my most critical data is spun off to DVD or CDRom every month. This stuff tends to be data like accounting/financial data, etc... stuff where a series of snapshots will help me recover with a minimum of work, but which, if it were completely destroyed, would be disastrous.

Last but not least, every three months, I spin a USB drive of my NAS and store it off site at a relative's house. That way, if my place burns down, I still have a fallback and minimize my data loss. I'm old school and do not trust cloud storage, and feel vindicated after the recent revelations about the NSA.

Security is another matter and there are firewalls, safeguards galore, but you're not asking about that.

I strictly observe a habit of storing all important data on the NAS. I tell my wife that anything she stores locally should be considered expendable and that I will not lift a finger to recover it if her HDD crashes. She's pretty good about storing by default on the NAS. It helps that I've deleted most local directories and created symlinks for the important ones to the NAS, so it's pretty transparent.

In the above scenario, *rsync* is king. Don't know what I'd do without this amazing little devil and I think it's one of the most underrated apps in the Linux-sphere. If people really leveraged its power, they too would largely avoid disaster.

It is worth noting that the above sounds awfully expensive, but in fact is very inexpensive. One of my NASes is an old laptop with a broken screen which is actually a blessing because it no longer eats electricity for that unnecessary component. I run Ubuntu minimal on it and hooked it up to a cheap USB drive bought at Costco. The others are a My Book Live that's about four years old and, my pride and joy--a first-generation HP Media Vault that's going on eight years. The whole collection probably isn't worth any more than $300 in today's cost. The off site USBs drive up the whole budget, but are not strictly necessary and mostly the result of paranoia.

Excuse the long-winded reply. Maybe there's an idea there that you will find worthwhile.

---

### Post by partloer on 2013-11-29
Thanks DuckHook.  Do you recommend any NAS in particular?  Also if you had two hard drives would you setup RAID 1 on a NAS or one hard drive on a desktop and backup to the other hard drive on the NAS?

---

### Post by DuckHook on 2013-11-29
NAS is a generic term and I like to use the equipment generically. In other words, I don't restrict myself only to the commercially sold "solutions". As already noted, one of my most effective NASes is an otherwise worthless laptop connected to a $80 USB drive. What makes it a NAS is simply loading NSF server on it and exporting a share. So, no, I don't recommend any NAS in particular. They don't even have to run Linux, although I can't imagine myself working with anything that doesn't.

Again, only in my specific case, I've hacked the My Book Live to access it using SSH. I've also hacked the 8-year old HP Media Vault, and installed SSH on it. Doing so gives me complete access into the guts of those two boxes, so in essence, I'm just running three Linux servers of varying capacities.

Many people like RAID, but I don't. That's just a personal bias. RAID has its place, and back in my working days, it would have been foolish not to implement it. But in my present circumstances, it's just a little home network, so fault tolerance is not a big deal and the complexity and the administrative overhead is just not worth it to me. If one of my NASes fail, I simply redirect my mounts to the other (they are automirrored daily using rsync and cron) and it's back to being fully operational again. What do most home users store on their NASes anyway? Videos, photos, music and some static critical data like docs, spreadsheets and their income tax records. None of it changes frequently. It's not as if we have a dozen interactive users hitting a database with multiple transactions every minute and can't afford to be down for even 15 minutes. Another problem with RAID is that it is not as robust. This sounds weird but it's true. You may have mirrored your data across two HDDs but you still have just one failure point in the MOBO, RAM, the CPU and the PSU. But that's just me. Only you can answer the question of which method is best for you depending on your preferences, your desire to experiment and your use-case.

---

### Post by partloer on 2013-12-01
DuckHook,

For NAS I am looking for a stable, and power efficient solution.  I agree it doesn't have to be a commercially sold "solution".  However as this will be power on all of the time many of the commercial solution require very little power.  If there is another option that offers very little power I am interested.  

I have also read that many people really don't like RAID so I am trying to figure out another option such as two NAS systems to use as backups or one as a file system and another as backup.  I am storing what most home users have video, photos, docs, etc but in the last year I have had a few hard drive failures on newer hard drives so I am trying to avoid lossing this data.  You are right that for home users 100% up time, multiple users is not needed I am interested in what some people recommend for home use backups.  Overall I like the way your backup system is setup.  What I am wondering what are the pros/cons setting up a file server where you files are stored on, then backup to your NAS?

---

### Post by DuckHook on 2013-12-01
> **partloer said:**
> ...I am looking for a stable, and power efficient solution...this will be power on all of the time...If there is another option that offers very little power I am interested.There are more cheap power-efficient homemade solutions available than you think. A really good solution that I haven't tried yet, but intend to implement once one of my current pieces die, is to hook a Rasberry Pi up to a USB drive. Both use no electricity to speak of and a RPi is only $39. But because an RPi is a surprisingly powerful little beast, I can load a full OS on it and it can also be used for all sorts of other services, including many of the "server" functions that people mistakenly associate only with massive towers.

That sort of setup is essentially what my Western Digital My Book Live is. It's a RISC processor bundled with a SATA drive housed in a tiny fanless box and running an almost full Linux OS. You can turn on SSH through the Web interface, and once you can SSH into it, you have full control over all of its internal workings including nfs-server, cron and rsync, which are the only apps needed to set up the backup strategy referred to in my earlier posts. The thing sips about 10 watts. Equal to $7 per year.

The HP Media Vault is older and is, relatively speaking, a hog with a PSU rated at 90 watts, though it is probably running at half that. I guesstimate that it's using about 50 watts. Equal to $35 per year.

The laptop power supply states that it's 90 watts, but in most laptops a huge portion of that power goes to the screen. Since mine is broken and disconnected, and since I have no load on the GPU and very little on the CPU, I figure that the laptop is actually using 40 watts max. The USB drive uses less than 10 watts. Combined equal to $35 per year.

All told, the whole gang consumes about 110 watts, which is about the power consumption of a bright lightbulb, spread over *three* standalone servers. Equal to $77 per year.

I'm already paying a higher energy price than needed just for redundancy. Most people would say that the third NAS is not needed at all. With just two My Book Lives (or equivalents), you could conceivably cut your power usage down to less than 20 watts, or about $14 per year.> What I am wondering what are the pros/cons setting up a file server where you files are stored on, then backup to your NAS?I've largely already described the pros and cons in my two previous posts. Your best solution will depend on how your usage-case interacts with those pros and cons. No one can make this decision for you and there is no simple formula that can be applied to a given situation. For example, one of the biggest factors is risk tolerance: some people are happy (or *think* they are happy) with no backup strategy at all, so they forego any of the administration and expense involved in buying, maintaining and sustaining a Fileserver/NAS.

One important point bears mentioning and then I'll shut up and go away:

Mirroring is not the same thing as backing up. They are very different uses and should not be confused for each other. What I'm doing with rsync and the three Fileservers/NASes is a mirroring strategy. The primary purpose of mirroring is *redundancy*—to always have another working fileserver available if one should die. However, if my house burns down, or if I delete an important file and don't realize it in time, then that data is lost the moment the drives are synchronized or my house is gone.

A backup strategy is not for data redundancy, but for *preservation*. This is what the offsite USB storage is for, and the DVDs that I burn of my critical financial data.

Best practice requires having procedures that look after both.

---

### Post by buzzingrobot on 2013-12-01
Whatever approach you choose, pay attention to how you're supposed to *restore* the files you've backed up. 

If you can't easily find what you're looking for, back ups are useless.

---

