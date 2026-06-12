---
title: "my ideas for Raid 6 and backup, would like your recommendations"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by goulding-tom on 2014-05-14
i am currently running Ubuntu 14.4 and XBMC perfectly on a intel Nuc. a big thanks for that by the way Ubuntu, works perfectly. also got netflix working perfectly, after scouring the web, i, er, found it in the app store....that was a tad embarrassing...but i digress.

[B]here is the background of my config
[/B]
my backend is a very very old readynas that quite honestly i am surprised hasnt blown up yet and it sorely needs a replacement.

as i am replacing an older pc (with still very very decent specs) that was windows for XBMC i would like to resuse that as a replacement server running Ubuntu 14.4 desktop.

i have the Nuc as a client, along with a Raspberry PI and an older Mac and some pads, phones. Some of this is older kit (sorry i am a hoarder of IT stuff, dont like to throw it out).

Other info relevant. wired network only for server and main clients (cat 6 as it happens)
wireless for other items like pads and phones etc and an older mac
also use the new Ubuntu server for a general backup area


[B]here is my ideas on replacing my NAS
[/B]
get 4-6 4tb drives (i expect that to grow by the way, more on that later)  (yes i will probably have to sell the kids to afford that)
build a Raid 6 array under Ubuntu desktop (i would prefer to use the desktop version)

for this i will probably need a raid controller card simply to have enough SATA ports. _So the first question is_: Does anyone have a recommendation for this on one that play nicely with Ubuntu 14.4?

next i need a backup of this array. heres where i would like your suggestions. i realise there is a lot of back and forth on this and there is no real one size fits all but i would appreciate information from someone who has experience in a similar config.


**New NAS **
older i5 (server 1) retargetted with Ubuntu as  server in raid 6 with 'some as yet unspecified' raid controller card. used for XBMC files and a general backup area for pc/laptops etc


[B]for backup (server 2)
[/B]an even older board with scratch disks as JBOD or raid 0

**the backup idea**
i have the main server (server 1) running 24/7  (yep i will have the nas version of the seagate drives)
once per week: i will automatically remote boot server 2 (either by WOL packet or with Ubuntu commands as yet unknown) and rsync to server 2 and remote shutdown the server on completion (not sure how yet but i will read the manual). The idea is server 2 should only be on for the duration of the sync and then shutdown or deep sleep.

**the backup idea 2 (the competitor)**
maybe backup 1 id far too exotic and i am overcooking it in an attempt to reuse stuff i have lying around. there wont be many changes per week, its a home server not a business server.
Should i get a couple of really big usb drives and attach them to server 1 and either rsync the deltas (which i dont think will work very easily or will it?) or once in a while connect to the server and manually copy any changes 

Although it might look as if i want to tinker around with this the reality is i wont and i dont. i am looking for the reliability of Ubuntu and a good raid card and good nas capable disks.  i will probably apply security patches to the OS only. the reason for using the Desktop version is to make it easier on me to run. i do want to have it run an SQL DB for XBMC (dont know how to do that yet but i am sure that will be okay). i will also have it running the server component for PLEX (sorry have a few client forced to use this) and a couple of possible TV backend software as well (apologies no idea on this yet as i have not done any homework on it). Might even throw in an itunes server solution in there somewhere.  So server 1 will need flexibility which i know i will get from Ubuntu.

[B]the questions
[/B]So on the RAID controller card...any recommendations for an Ubuntu friendly card?
on the backup should i go for what looks like an exotic remote boot and backup of server 1 or just keep it simple with a couple of USB drives
is rsync the right solution to copy changes from 1 server to server 2 or just put in usb drives and manually copy

thanks for any help and suggestions. i would greatly appreciate recommendations from someone who has faced a similar dilemma.

Tom

---

### Post by TheFu on 2014-05-14
TL;DR

RAID is for availability. Is that really necessary for any home environment? If you can handle 10 hrs of downtime to save $400 in HW costs - forget RAID. OTOH, if you want to learn RAID systems ... there are 2 sorts HW and software.  HW will have higher performance, but that data is tied to the HW-RAID card forever.  SW-RAID is much more flexible - I've moved disk arrays between 3 different systems (different Linux OSes too). The performance is good enough for most home needs, but 3x slower than a quality LSI card would provide.

If you want a RAID card - carefully read the HCL for Linux. Avoid cards that are not supported by kernel-provided drivers. I've been burned - the vendor only provided a driver for a 2 yr old kernel. No updates.

Backups come BEFORE RAID. RAID is not a substitute for backups.  Nightly backups are trivial to automate, so why not do it.  They are highly efficient these days (storage, time, network).  1.15x the base storage for 30 days of versioned backups.  Why wouldn't you do that?  

Split the data into 2 sorts 
a) large media files that seldom change
b) OS, applications, personal files and personal settings, documents

Use rsync as-needed for the media files - monthly, quarterly, whatever. 1 extra copy, perhaps with parity (snapraid)

Use a real backup tool for everything else. I like **rdiff-backup** for many, many reasons, but there are other tools. Also, you can limit the things backed up - no need to backup the OS, since reinstallation from an ISO is 15 minutes - just backup the settings, list-of-packages, and any other things that change.  If a DBMS server is involved, you'll want to script a dumpDB or bring the DB down during the backup processes to avoid corruption.

Practice the restore process to ensure you don't miss something trivial. Practice makes perfect, right?

XMBC is great as a viewing app, but leaves much to be desired as a server.  I switched to Plex about 6 months ago for the server and wish I'd changed years ago.  Plex is NOT F/LOSS, but it is free. That gave me pause - not happy about using closed-source. No need for a Plex account at all - I've never created one - also I block the plex external websites at the network layer to reduce tracking.  Plex is a great DLNA server, so there are DLNA clients for every platform. Better than any other DLNA server I've tried. There is a Plex Plugin for XBMC too.  Smart-TVs tend to be DLNA clients, so you may not need anything connected to the TV at all.

If you insist on RAID ... know that some failures will create complete data loss. I've helped folks here twice in the last few months who lost all the data because they didn't have backups, but they did have RAID. It was ugly.

My blog talks about backups a bunch, with multiple discussions and examples for rdiff-backup.  I was looking at the backup results this morning.  My XMBC/Plex machine backup took 18 seconds.

If you care about reliability, do not use USB drives. Ports get flaky, USB get disconnected for some reason, over time it gets worse and worse.  If you insist on USB ... use autofs to mount them as-needed, only when used. See exibit "a"

```
[3938006.712555] Descriptor sense data with sense descriptors (in hex):
[3938006.712566]         72 01 04 1d 00 00 00 0e 09 0c 00 00 00 00 26 00 
[3938006.712579]         00 4f 00 c2 00 50 
[3938006.712587] sd 14:0:0:0: [sdg] ASC=0x4 ASCQ=0x1d
[3938007.109416] sd 14:0:0:0: [sdg] Sense Key : Recovered Error [current] [descriptor]

``` That is a USB connected disk. So ... did the data get written or not?  The log file is full of USB errors like this, regardless of which port or drive is being used.

---

### Post by spynappels on 2014-05-14
Listen to TheFu, he is wise in the way of the backup!

To add my tuppence worth on the RAID questions:

LSI cards are good but expensive. Personally, I think software RAID on Linux is fine for home use. I'd suggest using RAID5 and a hotspare rather then RAID6, Just because there is extra overhead in RAID6 compared to RAID5 and in the event of loss of a disk, it will only start rebuilding when the disk is replaced. With a hotspare, the rebuild could start immediately on disk failure with the right setup.

Oh, and you could actually create a RAID1 of 2 USB thumbdrives for the OS, as long as you write any logs to the data array, they should last a very long time with little or no writes required to the USB thumbdrives.

---

