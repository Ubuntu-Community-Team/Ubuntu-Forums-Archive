---
title: "Clamav scan completed virus found"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-09-14
I completed my scan and was amazed to find that it had identified one of my VMWare files as linux.Lionworm-1.  I am wondering if this is a false positive.

Has anyone ever heard of this virsu as the internet has very little info.  Says it is a file infector.

I keep hearing about how secure linux is, but found got this after just 2 weeks.  Needless to say I have some concerns.

Any advice or info?

Thanks,
Eric

---

### Post by t0p on 2008-09-14
> **Virus Encyclopedia Search Results**

ELF_RAMEN.B3
Aliases: Net-Worm.Linux.Ramen.b (Kaspersky), Linux/Lion.worm.a (McAfee), Linux.Lion.Worm (Symantec), LINUX/LionWorm.1 (Avira), Linux/Adore-A (Sophos),
This is a File Infector virus. It is detected by the latest pattern file.

[http://www.trendmicro.com/vinfo/virusencyclo/alphalisting.asp?NAV=39&ltr=E]("http://www.trendmicro.com/vinfo/virusencyclo/alphalisting.asp?NAV=39&ltr=E")

And now you know as much as most of us, I think.  Google showed 3 results on the critter!

---

### Post by J0hnnyBr@v0 on 2008-09-14
Yep...that was the same set of results I got.

I guess I delete the file and scrap my Virtualized Vista

Thanks

---

### Post by J0hnnyBr@v0 on 2008-09-15
I wanted to post this in case someone else comes across the same issue in the future.

Last night I set a cron job to run clamscan and log to a file.  This morning, the file had the following line:

/home/eric/vmware/Windows Vista/Windows Vista-s003.vmdk: Trojan.Bat.FormatC-6 FOUND

I did a search online for Trojan.Bat.FormatC-6 and came up with this from Google:

[http://forums.clamwin.com/viewtopic.php?p=5059](http://forums.clamwin.com/viewtopic.php?p=5059)

Trojan.Bat.FormatC-6 is an extremely "loose" signature. I believe it would be heavily prone to false positives. The signature basically checks every file for the following two strings:

"ctty nul"
"format c: /autotest /q /u"

A virtual PC disk image contains many things other than files, including swap files, caches, other sorts of miscellaneous memory that may not neccesarily be present on the "c:" drive inside of the virtual machine.

You're actually going to be less effective scanning a virtual pc disk image in this way because most of the signatures expect to be scanning files that are executable in nature, and have signatures at exact locations in the files.

VPC disk images are not executables they're giant images. All of those offsets and file type checks inside of the definitions get tossed out the window when you scan in this fashion.

In addition, I used my home drive as a shared folder for my virtual Vista and ran the McAfee against the drive.  It came up clean.

Hope this helps someone in the future.

Thanks

---

