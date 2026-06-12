---
title: "Adding space to Ubuntu Partition...only saw 30 gig possible..."
date: 2013-02-13
forum: New to Ubuntu
---

### Post by PIE09gbLmgG6 on 2013-02-13
Ubuntu Community,

I have not been excited about computers in a long time! Ubuntu is finally where I wanted it to be!

As I trying to understand linux better...when I installed UBUNTU 12.10 on my pc it only gave me the option of 30 gigs...did I miss something?

I have 500gigs I wanted to give to this partition...

I know there is always a way to add space...but I'm lost...

ego-

---

### Post by ibjsb4 on 2013-02-13
Is this a WUBI install?  Ubuntu inside windows?  If so, WUBI is limited to 30G max.

---

### Post by deadflowr on 2013-02-13
Yep, that's a WUBI thing.

Follow the advice on setting up a dual-boot with Windows and Ubuntu here:

[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

And come back if any questions on what is what cross your mind.

---

### Post by PIE09gbLmgG6 on 2013-02-13
Wow! That was fast.

Wubi install yup.

With work I have to have the dual boot. I'll check the links and report back.

Ego-

---

### Post by Mark Phelps on 2013-02-13
You already have a dual-boot (the good news) but you can't make it bigger (bad news) and to migrate this to a standalone install could take a lot of work.

You said "at work" -- so is this a company-supplied PC? If so, you would do best checking with any IT folks "at work" to see if what you want to do is OK before trying this.

And, if the PC came pre-installed with Win7, you should read through the following material before attempting a dual-boot:

You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by PIE09gbLmgG6 on 2013-02-13
MP,

Thanks for the heads up. My work was totally fine with me loading it...I'm in education and try to find open source for schools and what not...joomla led me here...and libre office...linux was a natural progression...

I'm debating just getting a laptop with ubuntu preloaded...is that possible...I really want to break the harness of windows...and apple is too restrictive for me...

I'll just play with the wubi for now...

Any chance you know when the ubuntu phones will be coming out? That has me so excited!

Ego-

---

### Post by deadflowr on 2013-02-13
> I'm debating just getting a laptop with ubuntu preloaded...is that possible.

Here:

[https://www.system76.com/]("https://www.system76.com/")

---

### Post by PIE09gbLmgG6 on 2013-02-13
Deadf,

Thanks...Never heard of that brand...checking them out right now...

Ego-

---

### Post by PIE09gbLmgG6 on 2013-02-13
Another just quick question...Virus scanner...is that needed with ubuntu?

Ego-

---

### Post by deadflowr on 2013-02-13
> **egosophist said:**
> Another just quick question...Virus scanner...is that needed with ubuntu?

Ego-

It's an often asked question.

Some will say yeah, and many many others will say no way.

Whatever makes you comfortable, be it having an AV or not. 

There are some good pages in the community wiki on security, but I like this thread in the forums:
[http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

It's very basic, and not as in depth as some of the wiki pages, but it's easy to understand and read.

Anti-virus is just one cog in the security apparatus of any system, and for linux it is not an essential part.
From the wiki:
[https://help.ubuntu.com/community/Security]("https://help.ubuntu.com/community/Security")

---

### Post by PIE09gbLmgG6 on 2013-02-14
DF,

Got some reading to do...I always hear that linux is virus proof...this should be an interesting read.

Liked the link for the system76...def a birthday gift coming up for myself!

Appreciate the helpfulness of this community...never had such a kind and generous response from so many people.

ego-

---

