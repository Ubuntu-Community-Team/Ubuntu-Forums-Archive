---
title: "Mission-critical data, HFS+ partitions, and Time Machine"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by goodmanj on 2008-05-28
Hi.  I'm only sort of a beginner: I'm returning to Linux after going Mac-only for five years, and am going to set up a hand-me-down PC as a software RAID server.  I have two questions:

1) Some of the data is currently on an external USB hard drive, formatted with an HFS+ partition.  I'd like to read and write that data using the Ubuntu box until I get the RAID set up.   How safe and reliable is the Linux hfs+ driver in Ubuntu?  Do I risk corrupting my disk and losing important stuffs?  I assume it's safer to mount the filesystem read-only and copy it all to the RAID, but the disks are still on order and I'm impatient.

2) I'd like to access this RAID server from my Mac.  After a herculean effort, I've got the Ubuntu box running netatalk and acting as an AFS server.  Yay me.

I'd really love to be able to use Time Machine to back up to this server, but from what I read online, this is impossible ... or maybe it's possible to back up, but not to restore, which is useless.

Can Ubuntu be made to act as a reliable Time Machine backup server?

3) OK I said I had two questions, but oh well.  To make Netatalk work with Mac OS 10.5, I had to recompile the Debian package from source to enable encrypted AFS logins.  Now Ubuntu's Update Manager keeps asking me if I'd like to download the latest version of netatalk.  NO!  How can I tell it to ignore that package for future updates?  (The "hold package" option in aptitude didn't affect the GUI Update Manager tool.)

---

### Post by SunnyRabbiera on 2008-05-28
> **goodmanj said:**
> Hi.  I'm only sort of a beginner: I'm returning to Linux after going Mac-only for five years, and am going to set up a hand-me-down PC as a software RAID server.  I have two questions:

1) Some of the data is currently on an external USB hard drive, formatted with an HFS+ partition.  I'd like to read and write that data using the Ubuntu box until I get the RAID set up.   How safe and reliable is the Linux hfs+ driver in Ubuntu?  Do I risk corrupting my disk and losing important stuffs?  I assume it's safer to mount the filesystem read-only and copy it all to the RAID, but the disks are still on order and I'm impatient.

2) I'd like to access this RAID server from my Mac.  After a herculean effort, I've got the Ubuntu box running netatalk and acting as an AFS server.  Yay me.

I'd really love to be able to use Time Machine to back up to this server, but from what I read online, this is impossible ... or maybe it's possible to back up, but not to restore, which is useless.

Can Ubuntu be made to act as a reliable Time Machine backup server?

3) OK I said I had two questions, but oh well.  To make Netatalk work with Mac OS 10.5, I had to recompile the Debian package from source to enable encrypted AFS logins.  Now Ubuntu's Update Manager keeps asking me if I'd like to download the latest version of netatalk.  NO!  How can I tell it to ignore that package for future updates?  (The "hold package" option in aptitude didn't affect the GUI Update Manager tool.)


well for your first question, I do think that linux can read HFS, but writing to is is another question... it should be possible none the less...
RAID I am unsure of, and yeh i dont think time machine is viable on linux...
if you are worried about backing things up linux does have tools for that but managing time machine stuff... I dont think its possible, at least not now...

---

