---
title: "Shares, Rights, Groups, &amp; Users"
date: 2016-02-09
forum: New to Ubuntu
---

### Post by kazz2 on 2016-02-09
I intro'd myself in my first post. But it was quickly whisked away to a more appropriate, specific forum based on the question I was asking. So, I'll rehash it a bit to intro this question.

I'm an old system admin. But I've not really done that since the late 90s. I learned through trial-and-error, school of hard knocks, and filled in the remaining cracks with formal training and research.

I understand user rights, group rights, directory rights, file rights, etc. Just not as pertains to Ubuntu. I'm trying to take an aging Windows Small Business Server 2003 server and a Windows Home Server (2) out of service, consolidating their shares, etc. into an Ubuntu server that will support multiple users and multiple Windows PCs. I dragged into service some hardware that's been lightly-if-at-all-used over the years. A 790i Ultra SLI motherboard with 8GB of RAM, a SATA DVD optical drive, a SATA2 500GB hard drive and four Hitachi Deskstar 3TB HDs I've wrangled into a ZFS zpool RAIDZ.

All is running, spinning, happy, etc. I've created three samba shares so far. I've started to try to understand how owner, group, and user rights get applied. But I've found that most of it involves reading dense documentation and text-based tutorials, etc. But I just can't get through that. I virtually can not learn by reading pages of text. I have to have something conceptual explained either verbally and interactively or through video/presentation with examples, etc. When I'm able to get started there, gain understanding, perspective, conceptualize intelligent questions, etc. I can finally turn to manuals and walls-of-text tutorials.

My issue is that I'm used to defining users and defining groups as roles. Some roles may have read access to a directory while others have the ability to change and, of course, delete. But the only rights I've seen are for ownership and a single group. I want multiple groups with a variety of rights for the same files and directories. I'm certain it's there I just need an orientation and perspective to help me understand before I tear into text file formats, command parameters and options, etc.

Does anyone know of such a resource? I've watched Youtube videos, free Ubuntu server videos, samba videos, etc. But they're all about installation and very basic, single-user access situations. I'm looking for best practices and their conceptual application in a Ubuntu server.

I hope this makes sense. I've always excelled at interactive classroom settings and failed at read, memorize, and apply.

I appreciate hearing about any education/training/orientation options that can fit my style of learning.

Thanks!

---

### Post by bab1 on 2016-02-10
> **kazz2 said:**
> ...
My issue is that I'm used to defining users and defining groups as roles. Some roles may have read access to a directory while others have the ability to change and, of course, delete. But the only rights I've seen are for ownership and a single group. I want multiple groups with a variety of rights for the same files and directories. I'm certain it's there I just need an orientation and perspective to help me understand before I tear into text file formats, command parameters and options, etc.

This is a Windows paradigm.  There are no "roles" per se.  By default there are some user groups that you can use (adm, staff, users).  You can't nest groups inside of other groups either.  The system is this way so that you can successfully manage a multi-user, mutli-tasking system.
The closest you will come to Windows type access control is with Linux ACL's, but I warn you, it will become very confusing real quick as there are not GUI tools to implement of document what you have done.  In the end you just have to be clever about how you manage access and data structure.> 
Does anyone know of such a resource? I've watched Youtube videos, free Ubuntu server videos, samba videos, etc. But they're all about installation and very basic, single-user access situations. I'm looking for best practices and their conceptual application in a Ubuntu server.

Most of this stuff is in pieces as each tool is a separate project.  The basic tools that come with the kernel are what makes up the distro.  Have you looked at a basic Ubuntu system administrator's guide.  [**Here**]("https://help.ubuntu.com/community/SystemAdministration") is a good starting point.  [**Here**]("http://ubuntuguide.org/wiki/Ubuntu_Trusty_System_Administration") is another guide to Ubuntu system administration.

---

### Post by kazz2 on 2016-02-10
That paradigm you reference came before Windows. And so do I. :D

Thank you for the links. I'm not interested in ACLing unless it becomes absolutely necessary. I'm just going to have to make some test directory structures, populate them, create users & groups, etc. and run some scenarios. Access is either granted as an owner, as a member of a group, or as "other". I imagine that should get me through the need to have users who can modify a directory's contents as well as those who can read/execute, but not modify well enough. It's just felt like, in comparison to what I'm used to, I was missing something when I was going through file permissions. That there had to be more. As long as that's not true I'll carry on.

Thanks again!

---

### Post by Geoffrey_Arndt on 2016-02-10
kazz2 . . ,

I find youtube really supplements any text/manual based instruction.   The key is to find the right videos.   If you query on "Understanding Linux File Permissions" in the Youtube search bar (not Google, but Youtube search), you'll see range of videos, several of which are excellent.   Just pause the video to take notes (I enter those real-time into a Zimwiki db for later reference - - very intuitive.)

This is one of the videos that explain the permisssion system well (and audio is easy to understand):   [https://www.youtube.com/watch?v=qbwnKgOGbAQ](https://www.youtube.com/watch?v=qbwnKgOGbAQ)

---

### Post by kazz2 on 2016-02-10
That looks like a very nice series. Thanks for the heads up!

---

### Post by kazz2 on 2016-03-13
The information here and in another thread I created took me to where I needed to go with user and group privileges. I thought I'd post the link to my other thread here and close this thread as solved.

[http://ubuntuforums.org/showthread.php?t=2314500](http://ubuntuforums.org/showthread.php?t=2314500)

Thanks everyone!

---

