---
title: "Can't download any software from Ubunto software center"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by newbie 2 ubunto on 2013-02-12
Hello everyone,

I am a John martin' new Ubuntu user, and couldn't be happier with the decision. I am currently using ubunto 10.10 (32bit). I have been facing a Problem That when i try to Download a software from Ubuntu Software center . This error showed up showed up immediately :

Failed to Download repository information
Check your internet Connection

Details about error :

W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz)  404  Not Found [IP: 91.189.92.202 80]
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I'm sure (or at least hopeful) that there is a simple fix to this problem, but it's certainly lost on me. I will post the window's contents, below. Thank you so much in advance for any help. I've heard a lot of great things about this forum, and even more about Ubuntu. I am looking forward to working past this issue so I can continue learning more about the power of this OS. 

Thanks again,
JOHN

P.S. I apologize for the length of this thread.

---

### Post by mcduck on 2013-02-12
Your problem is that 10.10 has reached it's end-of-life in April 2012, and it's software repositories are now closed.

You should upgrade to a more recent Ubuntu version, but the tricky part here is that when upgrading, you can't jump over versions, and the next one (11.04) is also already out of support.

While it is possible to do the upgrade by manually editing your sources.list to use old-releases.ubuntu.com, the easiest and quickest way for you would be to back up all your personal files and make a fresh install of 12.04 LTS or 12.10.

---

### Post by westie457 on 2013-02-12
Welcome to the Forum.

Firstly, the version you are using went End of Life in April 2012 and is no longer supported.

While it is possible to point you in the direction of using to old repositories the best recommendation is to download 12.04 LTS (Long Term Support) and do a clean install.

The differences between 10.10 and 12.04 mean that to upgrade to 12.04 something is likely to break in the process.

Before doing this Back up any personal files first.

---

### Post by d4m1r on 2013-02-12
Any reason you installed 10.10? As people have mentioned, it is an old release that has reached the end of its life in terms of updates. I as well would recommend for you to reinstall Ubuntu using a copy of 12.04 LTS. The LTS = long term support and in this case, guarantees you updates for 5 years. If you haven't transfered any important files to your 10.10 partition, you can just install 12.04 immediately and overwrite out 10.10 partition during the install process. If you do have important files on there already, copy them to somewhere else like a USB stick first and transfer them back after you install 12.04.

---

### Post by Sendo Eevpix on 2013-02-12
Yes, that version is dead and useless. Completely out-of-date unsupported. Though I am feeling like saying it is a net work problem with Ubuntu, because I have just spent a few days unable to update my computer. So ... I don't know what to actually say.

---

