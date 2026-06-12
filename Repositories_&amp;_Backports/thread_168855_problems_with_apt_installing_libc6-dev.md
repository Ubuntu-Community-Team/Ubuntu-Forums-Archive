---
title: "problems with apt installing libc6-dev"
date: 2006-05-01
forum: Repositories &amp; Backports
---

### Post by gmork on 2006-05-01
Hi, 


Like
[http://ubuntuforums.org/showthread.php?t=137072&highlight=libc6-dev]("http://ubuntuforums.org/showthread.php?t=137072&highlight=libc6-dev"), I also am experiencing these troubles installing libc6-dev and installing build-essentials is giving the same:

```

libc6-dev: Depends: libc6 (=2.3.5-1ubuntu12) but 2.3.5-1ubuntu12.5.10.1 is to be installed
E: Broken packages

```

using -f does nothing

He fixed it by downloading libc6 and libc6-dev .deb files. Is there an alternative solutions to this? e.g. can this also be done using apt, with an altered sources.list?


kind regards,
gmork

---

### Post by gmork on 2006-05-01
In reply to myself,

The problem seemed to be my sources list,
[http://paste.ubuntu-nl.org/6047](http://paste.ubuntu-nl.org/6047) did the trick. Some missing packages in my local debian mirror...

Cheerio!

---

### Post by bmcage on 2006-05-02
I just had the same problem. A bit more explanation of the problem:

If in Adept/Synaptic you see that version of libc6-dev is 2.3.5-1ubuntu12 you do not have the correct sources in /etc/apt/sources.list. 
If the sources list is correct, and you to "fetch updates", you should see that the version is 2.3.5-1ubuntu12.5.10.1 as of  2 may 2006, even if this is not clear from [http://packages.ubuntu.com/breezy/libdevel/libc6-dev](http://packages.ubuntu.com/breezy/libdevel/libc6-dev), where only ubuntu12 is given.

I would not try to change the local mirror to the general ubuntu list however, as every descent mirror should be up to date, and this will slow down fetching of packages. Just hunt down the error in sources.list and correct it. In my case, the error was that 
deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
was not present (I think, as while editing sources.list I did some other cleanup too). Indeed, I use the belgian mirror, only do that if you life near belgium!

---

