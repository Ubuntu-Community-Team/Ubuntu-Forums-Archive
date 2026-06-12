---
title: "Lost Windows 8 after aborted Ubuntu install"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by rudi3 on 2014-02-26
Hi,
After a messy Ubuntu installation it was aborted.
I tried to install Ubuntu alongside Win 8.
I think I have totally forked it.
Using the Win 8 DVD going into CMD prompt in Advanced Options and navigating around with DIR, there is a Windows directory but no bytes.
Output from Boot Repair.
[http://paste.ubuntu.com/6998019](http://paste.ubuntu.com/6998019)
Any help appreciated.

---

### Post by squakie on 2014-02-26
I'm hoping user Oldfred sees this thread.  They are an expert on this.  One of the things I noticed was the use of logical volume sets.  I really don't anything other than what they are, but I remember seeing a post about those  and having problems on an install.  Just in glancing through the boot-repair output I didn't see any ntfs partition - do you know what device it is supposed to be on?

Did you search the forum and read up on UEFI, Windows 8, and Ubuntu?

---

### Post by oldfred on 2014-02-26
I do not know LVM, but the old 12.04 alternative installer clearly said it was a full disk install, or it erased entire drive.
Please add to this bug.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

You only show the separate /boot and LVM partition(s). Windows & any recovery partitions are gone. 

Did you make Vendor recovery DVDs  set or flash drive of full image backup of Windows?
If not and new system some vendors may send you new copy of its OEM Windows image (not installer) for a nominal charge. Others may not. Then you have to purchase a new copy of Windows that is the full installer as the Microsoft product key is in the UEFI, but only good for vendor's OEM version.

One user just posted that he was able to get the store's tech to create the recovery image from a identical model in the store. I call that good customer service by the store, but most might not do that.

---

### Post by rudi3 on 2014-02-26
Thanks for your response oldfred,
"Did you make Vendor recovery DVDs  set or flash drive of full image backup of Windows?"
Of course not. :)
The laptop is around a four year old HP Pavilion DV6. It came with Win7 installed which I "upgraded" to win8 about 18 months ago.
Anyhoo, I will apply Data Recovery to the HDD to see what can be retrieved in the way of Documents etc.
Sorry for thr delayed reply, am in Queensland Australia.
Again, Thanks for your interest oldfred and squakie.

---

### Post by squakie on 2014-02-26
Thanks for jumping in oldfred!!  I still get a little lost on some of this, and I don't know anything about LVM's either except that I have seen similar posts that make it sound like they are a pita to do things like this with.

Dave

---

### Post by oldfred on 2014-02-26
You can see if testdisk will find old partitions, not sure what LVM does to partitions.

I also have used photorec but it is a long slow process, requires lots of space on another drive for recovered files and files do not have full names, just extensions.

 [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by rudi3 on 2014-02-26
"not sure what LVM does to partitions."
Lovingly Violates Microsoft.
Using GetBakData Advanced Data Recovery Tools, looks very promising so far.
Some of the DR software doesn't even acknowledge the presence of my HDD.
With GetBackData I can open .docx, .txt etc in the myDocuments folder, however the trial version doesn't let copy or save.
Waiting for the licence fee at mo. $49USD.

---

### Post by rudi3 on 2014-02-26
Finally key has arrived for GetBackData.
BE AWARE.
While the software is excellent the key for $49USD is licensed to the HDD you are retrieving data on ONLY.

Gone from BE AWARE to be BEWARE.
Software is crap.
They are known as recoverdatatools.com and getbackdata.net the software Recover Data for Windows.
The trial looks good but the bought version crashes in scan modes and save modes.
[This guys experience]("http://www.complaintsboard.com/complaints/recoverdatatoolscom-c342194.html") pretty much happened to me.
PLUS, get this.
When they finally contacted me they requested remote control to repair the software.
In remote control we communicated with Notepad.
After a couple of minutes fiddling behind a black screen the tech came back on Notepad and wrote the Accounts Dept. had contacted him and said I had been charged twice, they needed to pay a refund.
No, I wrote, Paypal and Bank statements show one payment.
Well, he wrote, we need to see your Bank statement and UNDER REMOTE CONTROL opened up the bank website and told me to put in the USERNAME AND PASSWORD.
I wrote, Do you think I'm stupid. The connection dropped out a few seconds later.

---

### Post by rudi3 on 2014-03-05
Gone from BE AWARE to be BEWARE.
Software is crap.
They are known as recoverdatatools.com and getbackdata.net the software Recover Data for Windows.
The trial looks good but the bought version crashes in scan modes and save modes.
[This guys experience]("http://www.complaintsboard.com/complaints/recoverdatatoolscom-c342194.html") pretty much happened to me.
PLUS, get this.
When they finally contacted me they requested remote control to repair the software.
In remote control we communicated with Notepad.
After a couple of minutes fiddling behind a black screen the tech came  back on Notepad and wrote the Accounts Dept. had contacted him and said I  had been charged twice, they needed to pay a refund.
No, I wrote, Paypal and Bank statements show one payment.
Well, he wrote, we need to see your Bank statement and UNDER REMOTE  CONTROL opened up the bank website and told me to put in the USERNAME  AND PASSWORD.
I wrote, Do you think I'm stupid. The connection dropped out a few seconds later.

---

### Post by docJ on 2014-03-06
Poor Rudi3, bad came to worse for you, I'm real sorry reading about your mishaps.
GetDataBack is the real deal, available from runtime.org; I've used it twice in the past with great results; please note it does take a fair while to run
Your getbackdata is a rogue software PoS that plays on similar name to grab would-be customer from the real thing.

I've also read good reviews about Recuva, a free, no strings attached, alternative
Good luck!

---

### Post by mastablasta on 2014-03-06
how about this: [http://itknowledgeexchange.techtarget.com/linux-lotus-domino/recovering-files-from-an-lvm-or-ext3-partition-with-testdisk/](http://itknowledgeexchange.techtarget.com/linux-lotus-domino/recovering-files-from-an-lvm-or-ext3-partition-with-testdisk/)

apparently testdisk can recover LVM but the question is can it also recover NTFS?!

---

