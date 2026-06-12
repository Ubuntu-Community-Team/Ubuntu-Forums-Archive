---
title: "Backup Software for Ubuntu"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by c5vetter on 2013-03-05
Okay, not sure if this is a valid question or not - what do you sages use for automatic back-up of your systems? Most of the programs are Windows-based and do not see how they could be used? (i.e., Carbonite; Second Copy, etc.) Or, is this something that Ubuntu One can be used for? Or, something else inherent within Ubuntu? Or, is this something folks do NOT worry about?

---

### Post by mamamia88 on 2013-03-05
> **c5vetter said:**
> Okay, not sure if this is a valid question or not - what do you sages use for automatic back-up of your systems? Most of the programs are Windows-based and do not see how they could be used? (i.e., Carbonite; Second Copy, etc.) Or, is this something that Ubuntu One can be used for? Or, something else inherent within Ubuntu? Or, is this something folks do NOT worry about?

Well everyone needs to worry a harddrive failure can happen on any os.   I personally just use dropbox for important documents and keep my music on multiple mp3 players.   If something was to happen I just copy the music back and install dropbox.  Drobox gives you 2gb for free which is plenty for word documents and pictures

---

### Post by Megaptera on 2013-03-05
Everyone should back up no matter what o/s they use. At least two backups of important stuff as a minimum - and stored away from each other either in the ether or in your house. Two back up tools spring to mind as a starting point ...
I think Deja Dup is in Ubuntu(?) [https://launchpad.net/deja-dup](https://launchpad.net/deja-dup) or if you want to backup o/s and your settings - Clonezilla [http://clonezilla.org/](http://clonezilla.org/)

I'm sure others will add more ....

---

### Post by gordintoronto on 2013-03-05
Good question! I don't use an automatic backup. Somewhere around here, I have a 250 GB hard drive which contains my historical "good stuff." I don't bother with backup of downloaded videos; if they all disappeared, I would say, "oh, well." I use Dropbox for the stuff I'm currently working on, which means it gets synched to my other computers.

The downside of Dropbox: if I delete a file, it gets deleted everywhere.

---

### Post by mastablasta on 2013-03-06
yes, ubuntu one can be used as backup (5GB free). as mentioned these kind of stuff is syncronised. so delete it here it get's deleted there as well if you let it sync automaticly. aside from Ubuntu one & dropbox, you have spideroak (encrypted files).

anyway to perform automatic backups at home to external disk you can use rsync (or Grsync if you prefer a gui). you can set it to automaticly perform regular scheduled backups.

a few other options are already mentioned dejadup, clonezilla and redobackup (i think basically a clonezilla with a much nicer interface).
there is also "back in time" and similar tools. 

to be super safe you would have 2 disks in RAID and synced. so if one dies you would replace it and then data would automaticly copy form the good disk.

---

### Post by justincarter on 2013-03-06
You know, It is very critical to take backup of  system on an on-going basis. If you are using ubuntu , you can use many software program depending on your requirement. You can try PYBACKPACK.

# apt-cache search pyback pybackpack - user friendly file backup tool for GNOME  # sudo apt-get install pybackpack  # pybackpack

---

### Post by Not Defined on 2013-03-06
I use deja-dup. It has a decent interface and is very simple. You can either get it by running, 'sudo apt-get install deja-dup' or by finding it the Ubuntu Software Center. It uses rsync so it is very similar to Time Machine on Mac OSX.

---

### Post by uc50_ic4more on 2013-03-06
I use Deja-Dup to keep a copy of my entire /home partition on an external drive that is left disconnected from the machine and unplugged from power when not in use. This mitigates against software screw-ups as well as power surges/ outages. To mitigate against theft, fire, floods, etc. that might destroy both my machine and the backup drive I also keep a copy of important stuff in Google Drive and Amazon S3 accounts. I keep config, preference and other system files in my U1 account.

---

### Post by cortman on 2013-03-06
I don't bother with backup software- I've found it to be more a pain than it's worth to me.
I wrote my own script that simply copies the important folders out of my home directory to a compressed folder on an external hard drive. It always keeps 5 old backups on the HDD and deletes the rest. Just add it to a crontab to make it run automatically.
Although honestly I usually just manually copy/paste any more.

---

### Post by mikechant on 2013-03-06
One thing I used to do but don't anymore is compress data. My reasoning is that nearly all 'large' files are already efficiently compressed internally by specialist methods relating to the data they contain (e.g. mp3, flac, videos etc.). And the remaining files are relatively so much smaller that compressing them gains very little. Meanwhile, the disadvantage of compressing files into an archive of some sort is that any corruption could lose the entire archive (maybe 1000's of files) whereas backing up indivdual files without compressing them means that data corruption will most likely only affect a few files. Also, it's a lot easier to restore specific files (deleted accidentally etc.) from a backup of individual uncompressed files.

I just use commands of the form
```
sudo rsync -av --progress [source] [destination]
```
stored in a script file.

The -a flag is important for backups since it preserves all the file attributes so you can restore the system to exactly how it was at backup time (date/time stamps, permissions etc.).

---

### Post by dryicebomb on 2013-03-06
+1 to deja-dup. Its very simple and its built in.

---

### Post by justincarter on 2013-03-12
deja-dup is Really great for for keep the back-up pf your useful data and information.  It is very easy to install and works awesome.

---

### Post by pinballwizard on 2013-03-12
> **cortman said:**
> I don't bother with backup software- I've found it to be more a pain than it's worth to me.
I wrote my own script that simply copies the important folders out of my home directory to a compressed folder on an external hard drive. It always keeps 5 old backups on the HDD and deletes the rest. Just add it to a crontab to make it run automatically.
Although honestly I usually just manually copy/paste any more.

Ditto.

---

### Post by bookherd on 2013-11-07
I've used SpiderOak for years, but now that I finally need to retrieve lost data, I'm finding the restore process to be incredibly slow and glitchy, while customer service is non-existent.  

I need simple, reliable online (off-site) backup because of my nomadic lifestyle.  I need about 100GB of storage (I've currently got under 75 GB, but want room to grow).  And I need the company to be stable, maintain reasonably fast servers, and do more than autorespond to support requests.

I'm currently doing a comparison of alternatives, with a bias toward "backup" options rather than "syncing" solutions (I only have one computing device, so those features don't do much for me).  I'll report my findings here, but in the meantime, if anyone can recommend an online backup service -- or, better yet, a site that collects customer reviews! -- I'd appreciate hearing about it.

---

### Post by bookherd on 2013-12-06
I've now looked at about a zillion options for online backup; here are the Linux-compatible contenders I thought worth mentioning here. Note that I have a bias toward GUIs, US companies (easier to call customer support from where I am), and "backup" vs "sync/sharing". I also have only one machine and <100GB to back up.  Note also that these prices will change as the date of this post recedes into the past.

Before giving any online backup provider (including the companies listed here) your credit card number, find out whether they throttle upload speeds after a certain amount, and whether they limit the size of files you can upload.  These are really common cost-cutting measures that they may not mention up front.

**Adrive**: 50GB free, 100GB for $25/yr.  Too good to be true?  Maybe: I found lots of reports of slow speeds and poor customer service.  Might be good as a secondary or less-crucial backup solution.

**AltDrive**: $44.50/yr for unlimited backup, no syncing/sharing.  Reputation for prompt/friendly customer service, even weekends.  I'm currently testing them out as a replacement for SpiderOak.  My only real hesitation comes from their location -- Seattle is in the same geographic region as I am, which decreases the odds of me being able to get my data back if I survive a [major regional disaster]("http://en.wikipedia.org/wiki/Cascadia_subduction_zone").  But... you can only worry about so many things. :)

**CrashPlan**: $60/yr for unlimited backup, no syncing/sharing.  A strong contender for my purposes, especially because they're such a well-established name in the backup business.  Lots of good reviews, too.  They do get quite a few complaints about slow upload/download speeds, though.

**iDrive**: $150GB for $34.65/yr. Not an Apple product, despite the cutesy name. Great reputation for reliability and support, everything looks amazing, except... their Linux service is command-line only.  This is a dealbreaker for me, but it might be perfect for you.

**KeepIt**: £49.50/year.  Based in the UK, looks like a good price for a good service.  Again, the location means this isn't for me; YMMV.

**Ubuntu One**: $30/year for 20GB.  I like the integration and the idea of supporting Ubuntu with my dollars, but $150/yr for 100GB just isn't too appealing when I look at all the other options.

**Wua.la**: $144/yr for 100GB.  Looks like a good service, but I'm leaning toward less expensive solutions for my limited needs.

Hope this is helpful to someone else!

---

### Post by Resistent on 2013-12-06
> **mamamia88 said:**
> Well everyone needs to worry a harddrive failure can happen on any os.   I personally just use dropbox for important documents and keep my music on multiple mp3 players.   If something was to happen I just copy the music back and install dropbox.  Drobox gives you 2gb for free which is plenty for word documents and pictures

Dropbox is not encrypted. I would never use it for important documents.
I use Wuala.com , you get 5 GB for free. And data is encrypted before upload.
[https://www.wuala.com/en/learn/technology](https://www.wuala.com/en/learn/technology)
I used it with Windows, and now with ubuntu too. You can backup data or make a sync between folders.

---

### Post by Resistent on 2013-12-06
> **bookherd said:**
> I've now looked at about a zillion options for online backup; here are the Linux-compatible contenders I thought worth mentioning here. Note that I have a bias toward GUIs, US companies (easier to call customer support from where I am), and "backup" vs "sync/sharing". I also have only one machine and <100GB to back up.  Note also that these prices will change as the date of this post recedes into the past.

Before giving any online backup provider (including the companies listed here) your credit card number, find out whether they throttle upload speeds after a certain amount, and whether they limit the size of files you can upload.  These are really common cost-cutting measures that they may not mention up front.

**Adrive**: 50GB free, 100GB for $25/yr.  Too good to be true?  Maybe: I found lots of reports of slow speeds and poor customer service.  Might be good as a secondary or less-crucial backup solution.

**AltDrive**: $44.50/yr for unlimited backup, no syncing/sharing.  Reputation for prompt/friendly customer service, even weekends.  I'm currently testing them out as a replacement for SpiderOak.  My only real hesitation comes from their location -- Seattle is in the same geographic region as I am, which decreases the odds of me being able to get my data back if I survive a [major regional disaster]("http://en.wikipedia.org/wiki/Cascadia_subduction_zone").  But... you can only worry about so many things. :)

**CrashPlan**: $60/yr for unlimited backup, no syncing/sharing.  A strong contender for my purposes, especially because they're such a well-established name in the backup business.  Lots of good reviews, too.  They do get quite a few complaints about slow upload/download speeds, though.

**iDrive**: $150GB for $34.65/yr. Not an Apple product, despite the cutesy name. Great reputation for reliability and support, everything looks amazing, except... their Linux service is command-line only.  This is a dealbreaker for me, but it might be perfect for you.

**KeepIt**: £49.50/year.  Based in the UK, looks like a good price for a good service.  Again, the location means this isn't for me; YMMV.

**Ubuntu One**: $30/year for 20GB.  I like the integration and the idea of supporting Ubuntu with my dollars, but $150/yr for 100GB just isn't too appealing when I look at all the other options.

**Wua.la**: $144/yr for 100GB.  Looks like a good service, but I'm leaning toward less expensive solutions for my limited needs.

Hope this is helpful to someone else!

why don't you buy an external harddisk with encryption? A 2,5" harddisk is not big.

---

### Post by hashky on 2013-12-11
I have been using CrashPlan for 2 years on Windows XP and now Windows 7 (main computer).  I tried to set up a Ubuntu file server to use for backups, but was soon consumed by Samba and "permissions" plus it was on site.  I installed Linux Mint 16 on the computer that was to be the file server.  I installed CrashPlan on it.  I now backup both the online and to the Linux Mint computer.  I am going to install CrashPlan on my Ubuntu computer and back it up there also.  I now make image backups of my Ubuntu computer and store them on my main computer (to backup to CrashPlan).

CrashPlan is free to use.  It just costs to backup to their servers.  Ditto for Ubuntu One.  Can you back up computer to computer with Ubuntu One?   

The downside is that I am dependent on CrashPlan.  CrashPlan can not be used for syncing.

External harddist:  Do you keep them connected all the time?  Do you store them offsites?  Where?  How many do you need?

---

### Post by jan-goebel-g on 2013-12-11
How do u know that dropbox is not encrypted? Last time i checked (a month ago) it had the best encryption/most encryption and secure connection methods of all the common cloud services.

I still have to decide weather to use dropbox or ubuntu one for backups of my system, i have 31gb on dropbox so it should be an easy one bot somehow i like having the option to backup to dropbox in deja dup instead of having to go over the local dropbox folder.

Any thoughts on that, any even better solution?
I really dont want to run BOTH ubuntu and dropbox clients at once, its eating battery after all im just not sure which one is better on battery usage (if i wont get an answer here ill open a thread on that^^).

---

### Post by mastablasta on 2013-12-12
@bookherd
Thanks for a nice and short review. i don't think speed is too important if you backup at night or in background. but easy recovery, customer service, good price are. ofcourse faster seped is always better than slower...:-)
> **jan-goebel-g said:**
> How do u know that dropbox is not encrypted? Last time i checked (a month ago) it had the best encryption/most encryption and secure connection methods of all the common cloud services.

really ? does it use user generated keys? i don't think data there is encrypted before tranmission. further more they have the master key and can show the files to anyone. if their security is breached you documents could go into the wrong hands. a few excerpts form wikipedia (but i do not know how truthfull they are):
> 
It also uses SSL transfers for synchronization and stores the data via AES-256 encryption,[43] though this is done with Dropbox's own encryption keys, and not the users'

> 
On July 31, 2012, Dropbox announced that an employee's account had been hacked, resulting in a number of Dropbox users being spammed by email.[80] In March 2013, users reported additional spam resulting from the July email leakage.[81]

> 
On June 6, 2013, The Guardian and The Washington Post publicized confidential documents suggesting Dropbox was being considered for inclusion in the National Security Agency's classified PRISM program of Internet surveillance

More under privacy concerns section... but point is if there is a leak, if something goes wrong in their security others have access to your data. this is because they have the keys to unlock your data and not you.

> **Resistent said:**
> why don't you buy an external harddisk with encryption? A 2,5" harddisk is not big.
you are correct - it's not big, neither they are expencive. but you will probably store it at home. let's say there is a fire or flood in your home. an unnexpected event. you data as well as your "backup" will be destroyed. propper backup should be offsite. in our law this is at least 50km away from user location (then again we are a small country). anyway more is better. it should also be safely locked with only the user having the key to it. especially for importnat documents you want to put as much obstacles as possible to deny access to unauthorised entities.

---

### Post by monkeybrain20122 on 2013-12-12
I use fsarchiver for cloning my installation. It is fast and light and quite easy to use (even though it is command line) The greatest selling point is that you can restore your clone to any partition as long as it is big enough for the content whereas many other tools (e.g Clonzilla) insist that the partition to restore to has to be bigger than the original one, even though the original partition may be mostly empty, this is a show stopper for me.This makes fsarchiver ideal if you want to copy your installation somewhere, say and external hard drive, or if you want to repartition drives with OSes already installed on it (it is a lot faster and safer to clone your Linux OS, then delete everything and repartitin and then restore the oses to the new partions, than using gparted to shrink and expand partitions with data even when the adjeciency  relations are correct) .  It also supports backing up when you are using your computer (with some limitations)

I don't update my OS when a new release comes out. I would install it in an external drive and work with it for a month or two, customize everything, do all the necessarily tweaks and see that every thing is ok. When I am ready I just clone the system with fsarchiver, delete my old one, and restore the image into my hard drive.
  
You can automate it with a cron job even though I do it manually.

The biggest shortcoming IMO is that it doesn't do incremental backup (but I suppose if it does it would be a lot slower and more resource demanding)

P.S. There is a gui called qtfsarcher, but I wouldn't bother. It only takes one command to do
the backup and one for resrtore. It is more complicated to push the buttons and the gui doesn't support many options (like excluding folders)

For routine data backup/synchronization I use unison.

---

### Post by bookherd on 2013-12-17
As an update to my previous post, I've found AltDrive to be a little glitchy, so now I'm giving CrashPlan a try.

@Resistent: 
> why don't you buy an external harddisk with encryption? A 2,5" harddisk is not big. 
For all the reasons mastablasta mentioned, but also, I've been living the nomadic life for the past 2 years. On-site backup, for me, would mean carrying an external drive around with me in my car. That's hardly a secure backup plan.

@mastablasta:
> Thanks for a nice and short review. i don't think speed is too important if you backup at night or in background. but easy recovery, customer service, good price are. ofcourse faster seped is always better than slower...
You're welcome. However, after it took weeks (seriously) to download ~75GB of lost data, I have to disagree with you about speed not being important. :)

Glad to see so many different backup solutions flying around! :D

---

### Post by Bucky Ball on 2013-12-17
> **c5vetter said:**
> ... is this something folks do NOT worry about?

!!! I'll forget you said that ... ;)

Big fan of Luckybackup here. Sounds like a toy. It's not. In the repos.

---

### Post by jones quest on 2013-12-18
I use timeshift ([http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)) for system backups (backup goes to a separate drive) and rsync for home partition stuff (documents, music, etc. which puts the files to my NAS).

---

### Post by fantab on 2013-12-18
> **cortman said:**
> I don't bother with backup software- I've found it to be more a pain than it's worth to me.

I feel the same. +1.

I have accounts with Dropbox, Ubuntuone and Skydrive(since the Hotmail days). The only data I need to 'backup' are documents and I back 'em up to all three. 
However, I back up my most important and 'sensitive' files to 4-16Gb 'pen'drives and lock 'em up. I find pendrives to be a much cheaper and more reliable solution than any cloud/ether based service.
I don't use any 'backup' software.

My two cents...

---

