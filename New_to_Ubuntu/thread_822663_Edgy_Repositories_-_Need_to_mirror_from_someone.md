---
title: "Edgy Repositories - Need to mirror from someone"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by staverts on 2008-06-08
Hi there, if anyone has a healthy mirrored edgy repository, I would like to mirror/replicate it, so that I can at least have access to the packages, I am using edgy for in many instances still, and since Ubuntu tore down the repos, I'm in a but of a lurch.  I would gladly apt-mirror from someone and store all 30 GB locally, and would be willing to mirror with others who would like to replicate and store the repo.

---

### Post by xurizaemon on 2008-06-11
Try old-releases.ubuntu.com.

```

deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu/ edgy universe
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe
deb http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
## these next two lines reported to no longer work (thanks brolin)
## is there a URL for security updates to edgy?
# deb http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted

```

---

### Post by HFC01 on 2008-06-23
Thanks.  It helped get a few things sorted out.  Excellent.

Thomas
Lisbon, Portugal.

---

### Post by cecco on 2008-07-21
this helped me too. Thank You very much

Francesco

---

### Post by teckhead on 2008-07-30
Thanks a lot.... The repositories are very helpful to me....
I would sure like to get them on DVD...  PirateBay bit torrent for them is
not functional any more... let me know if you know where I could find this...
***************************************************************************
I sure could use a means to update my Firefox 2 in edgy to the latest....
Thank you so much.... Everything else works great.... 
                                                            Mark

---

### Post by xurizaemon on 2008-07-30
@teckhead - 

There is a method to build an install CD / DVD using APT - maybe someone can give us a pointer for you to use? I've never had to do this myself, I just pull things off the network, but if you want an install media handy then this would be the trick.

I wouldn't recommend you download your packages via PirateBay unless you are very careful to check the package signatures against the Ubuntu keyrings. I'm guessing (in part at least) you installed Linux for security's sake - not much sense in then downloading software from an unknown source, is there? Sure, "there are no viruses for Linux", but that won't help you one bit if you download and install malware manually.

---

### Post by FinalJenemba on 2008-08-03
> **xurizaemon said:**
> Try old-releases.ubuntu.com.



Thank you SO much!  Just made my weekend!

---

### Post by MarilenCorciovei on 2008-12-05
Thanks a lot for your help it solved the same problem for me too.

---

### Post by markshoe on 2009-02-07
Thanks, helped me too!

Mark

---

### Post by gigo6000 on 2009-02-17
> **xurizaemon said:**
> Try old-releases.ubuntu.com.


Thanks a lot!!!:D this is what I was looking for, non of the repositories had the quota package...

---

### Post by linuxpimp on 2009-04-21
Thank you!

LP

---

### Post by sgreimer on 2009-08-24
Thanks for the tip on using old-releases.ubuntu.com

---

### Post by k3lt01 on 2009-08-25
For those of you who would like a complete set of edgy (or any other version of Ubuntu for that matter) repos check out [BobSongs excellent Tutorial]("http://ubuntuforums.org/showthread.php?t=352460").

---

