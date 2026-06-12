---
title: "Clamav &amp; Cron"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-09-14
I am a recent convert to Linux & Ubuntu.  Have to say, so far I love it.  Easy to use and easy to learn.

I do have one question.  I have searched the boards and found some info on this, but not exactly what I was hoping for.

From what I read I realize I have less to worry about with my desktop & virus/malware (I used to run McAffe in windows).  My situation is that I still sharedocs with other windows users and I would like to scan my documents folder every Sunday night at say Midnight, just to be sure.

I have ClamAV installed, from Synaptic install.  How would I go about scheduling this to occur?

I looked at the cron MAN pages and I still don't "get it"

Also, is there a certain folder or something I should be looking for/at with regard to unexpected access, etc?

Thanks in Advance

---

### Post by kaivalagi on 2008-09-14
Take a look at crontab for setting up cron jobs, if you know what the command for clamav needs to be you shouldn't have a problem.

If you are running gnome, then gnome-schedule is the gui frontend to cron...I can't remember if it comes with the default gnome setup or not, but it can be installed using synaptic. There will be an equivalent gui in kde I am sure...I just don't know what

Hope that helps

---

### Post by J0hnnyBr@v0 on 2008-09-14
Thanks for the help.  I got it installed and will see what I can do.  It requires you know the command line, unfortunately I can't just select a program...so I will need to do a little more research.

I grabbed the documentation from the CamAV site as well in hopes of some insight.

Thanks

---

### Post by kaivalagi on 2008-09-14
> **J0hnnyBr@v0 said:**
> Thanks for the help.  I got it installed and will see what I can do.  It requires you know the command line, unfortunately I can't just select a program...so I will need to do a little more research.

I grabbed the documentation from the CamAV site as well in hopes of some insight.

Thanks

```
clamscan -r -i ~/
```

will scan recursively though your home directory, only showing infected files it finds, there are options to move infected files and output to a log for unattended runs...

---

### Post by J0hnnyBr@v0 on 2008-09-14
I completed my scan and was amazed to find that it had identified one of my VMWare files as linux.Lionworm-1. I am wondering if this is a false positive.

Has anyone ever heard of this virsu as the internet has very little info. Says it is a file infector.

I keep hearing about how secure linux is, but found got this after just 2 weeks. Needless to say I have some concerns.

Any advice or info?

Thanks,
Eric

---

### Post by kaivalagi on 2008-09-23
> **J0hnnyBr@v0 said:**
> I completed my scan and was amazed to find that it had identified one of my VMWare files as linux.Lionworm-1. I am wondering if this is a false positive.

Has anyone ever heard of this virsu as the internet has very little info. Says it is a file infector.

I keep hearing about how secure linux is, but found got this after just 2 weeks. Needless to say I have some concerns.

Any advice or info?

Thanks,
Eric

For what it's worth I get virus detected at work when running database queries, sometimes the virus definitions clash with normal everyday operations...

I am guessing this is what's happening here

---

### Post by J0hnnyBr@v0 on 2008-09-23
I wanted to post this in case someone else comes across the same issue in the future.

Last night I set a cron job to run clamscan and log to a file. This morning, the file had the following line:

/home/eric/vmware/Windows Vista/Windows Vista-s003.vmdk: Trojan.Bat.FormatC-6 FOUND

I did a search online for Trojan.Bat.FormatC-6 and came up with this from Google:

[http://forums.clamwin.com/viewtopic.php?p=5059](http://forums.clamwin.com/viewtopic.php?p=5059)

"Trojan.Bat.FormatC-6 is an extremely "loose" signature. I believe it would be heavily prone to false positives. The signature basically checks every file for the following two strings:

"ctty nul"
"format c: /autotest /q /u"

A virtual PC disk image contains many things other than files, including swap files, caches, other sorts of miscellaneous memory that may not necessarily be present on the "c:" drive inside of the virtual machine.

You're actually going to be less effective scanning a virtual pc disk image in this way because most of the signatures expect to be scanning files that are executable in nature, and have signatures at exact locations in the files.

VPC disk images are not executables they're giant images. All of those offsets and file type checks inside of the definitions get tossed out the window when you scan in this fashion."

In addition, I used my home drive as a shared folder for my virtual Vista and ran the McAfee against the drive. It came up clean.

Hope this helps someone in the future.

Thanks

---

