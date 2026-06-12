---
title: "Failed to download repository information"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-05-14
I keep getting this so I ran 
sudo apt-get update



and found, W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
So I took it out of the list, then ran sudo apt-get update and now I see this at the end


W: Failed to fetch [http://ppa.launchpad.net/toine512/jtv-downloader/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/toine512/jtv-downloader/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I though that trusty was the new 14.04??
How do I fix this one?

---

### Post by Vladlenin5000 on 2014-05-14
Neither have packages for 14.04 yet, that's all.

---

### Post by ibjsb4 on 2014-05-14
[http://ppa.launchpad.net/toine512/jtv-downloader/ubuntu/dists/](http://ppa.launchpad.net/toine512/jtv-downloader/ubuntu/dists/)

[http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/)

---

### Post by EZZ9 on 2014-05-16
Neither have packages for 14.04 yet???
I don't think you're getting my question right.
 I am on 14.04 I was getting updates, but now it has stopped.
Software updater use to work, but now says 
[h=1][Failed to download repository information]("http://ubuntuforums.org/showthread.php?t=2224044")[/h]

---

### Post by sammiev on 2014-05-16
> **EZZ9 said:**
> Neither have packages for 14.04 yet???
I don't think you're getting my question right.
 I am on 14.04 I was getting updates, but now it has stopped.
Software updater use to work, but now says 
[h=1][Failed to download repository information]("http://ubuntuforums.org/showthread.php?t=2224044")[/h]

Check out post number 3 and change the source.list to match. There is no 14.04 repository for those yet.

---

### Post by deadflowr on 2014-05-17
Handbrake's in the official repositories now.(universe)
I don't think the ppa is of any use for trusty.
disable it.

I don't know what's up with the jtv-downloader, but it hasn't been updated in over a year now.

---

### Post by EZZ9 on 2014-05-18
I thought I would give info of what I did, but everyone is stuck on that and not what is happening.
I don't think you're getting my question right.
 The questions is. 

Software updater uses to work, but now says all the time.
[B][URL="http://ubuntuforums.org/showthread.php?t=2224044"]Failed to download repository information??
[/URL][/B][URL="http://ubuntuforums.org/showthread.php?t=2224044"]
[/URL][B][URL="http://ubuntuforums.org/showthread.php?t=2224044"] How can I fix this?
[/URL][/B]

---

### Post by Bashing-om on 2014-05-18
EZZ9; Hello.

Five people have tried to help/advise.
So OK, let's do this in baby steps.

The base of the package management system is the index files. These index's are contained in the "/etc/apt/sources.list" file and in the 3rd party directory "/etc/apt/sources.list.d/".

So show us these index files for advisement on how to remove the problematic lines.
Post back - between code tags - the output of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We will do this gradually and get you to comprehend the process.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

