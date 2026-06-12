---
title: "I think I broke Synaptic"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Jackelope King on 2008-04-25
When I try to load Synaptic, I get the following error:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I get a similar error when I try to use Applications -> Add/Remove...

Both programs identify the error as coming from /var/lib/apt/lists/ppa.launchpad.net_awn-testing_ubuntu_dists_gutsy_main_source_Sources
However, I cannot access or edit this file, as it informs me that I do not have permissions to do so.

Please help!

---

### Post by spiderbatdad on 2008-04-25
could you copy and paste your file called: /etc/apt/sources.list

please post inside code tags...the # symbol in the editor menu of this window.

---

### Post by Jackelope King on 2008-04-25
Okay, you pointed me exactly where I needed to go to fix it! Thank you so much!

---

### Post by Haxor on 2008-04-25
Hey,

I have the same problem with the same repository, it looks like it is a common problem, I have found that some of these reports have been made before with different repositories.
Some fixes refer to modifying apt.conf, copying status.old over the status file, issuing a dpkg command, etc, but none had worked for me.
Commenting out that line in the corresponding .list file is just a temporal fix but there is gotta be a real fix

Warper

---

### Post by isaacj87 on 2008-04-25
The best thing to do is to disable the AWN-Testing PPA repo for now. It's currently broken, which is why it's giving that error message. 

Here's the announcement from the AWN Forums dated 04/25/08:

> The Awn-Testing PPA is broken again. No ETA on when this will be fixed - waiting on the Launchpad admins.

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1725&page=1&isLive=true]("http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=1725&page=1&isLive=true")

---

