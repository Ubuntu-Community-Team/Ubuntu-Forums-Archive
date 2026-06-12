---
title: "Ubuntu beta upgrade erro"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Peterfc on 2008-10-04
Hi All

I installed the new beta version 8.10 on a machine i have been using for various testing for music/ video and Mythbuntu and surfing etc with this machine i have had no problems since the upgrade.If i have any  problems ant any time i just do a new install and all is ok. 

At work i have a machine i use for day to day work Open office Presentations/ mail surfing etc. I decided to upgrade to 8.10 beta on this machine all seemed well and on reboot all i now get is the picture on my desktop. I have tried to use the recovery mode i case after the install something happened at the reboot stage. Again upon booting up only the picture on the desktop came up and nothing else.  Their is a previous version of Ubuntu on my machine on a drive with 19.6 GB. When i boot from the previous version i am ok. 

My question is i am able to drag all my folder etc i have on the desktop on the machine i upgraded to onto another drive. That's ok but all my book marks are in Firefox these are vital to me also i have a lot of email in folders on Thunderbird can anybody help with how to move these to my Drive 19.6 Gb from my Drive 42.2 GB.

Windows 114.9 GB

Drive 42.2 GB

Drive 19.6 GB

Dell Dimension 2400 series 200GB drive 1gb ram Dvd/rw all the rest onboard.

---

### Post by kansasnoob on 2008-10-04
I don't know how to find the Thunderbird mail, but you should be able to find out the proper folder(s) with a Mozilla search. I don't use Thunderbird)

But basically transferring files and/or folders from one Ubuntu install to another isn't that hard. You see right now I have Windows XP, Ubuntu 8.04, and Ubuntu 8.10:

[ATTACH]87276[/ATTACH]

After I installed 8.10 I wanted to transfer my bookmarks from 8.04 to 8.10, so I went to Places and mounted the "25.6GB Media" partition. I then just went to Home (in the  now mounted partition) and View > Show Hidden Folders. Then I located the proper folder > .mozilla > firefox > xxxxxxxx.default > places.sqlite and then I just copy-n-pasted that folder to the desktop of the same mounted partition. I then repeated that for my Home > Documents, Home > Downloads, etc.

I placed all the stuff I wanted to transfer on the desktop just to make it simpler for me! I then transferred each folder to the 8.10 partition. Clear as mud:confused:

It was easier to do than it is to explain:(

---

### Post by Big_Kahunaca on 2008-10-04
If your Firefox bookmarks are important, you can export them by clicking Bookmarks -> Organize Bookmarks --> Import and Backup (or if you have an older version, file->export)  This should export them in either .html or .json.  Restoration is the opposite proces...

As for Thunderbird, this link may help....

[http://kb.mozillazine.org/Profile_backup#Manually_back_up_the_profile]("http://kb.mozillazine.org/Profile_backup#Manually_back_up_the_profile")

---

