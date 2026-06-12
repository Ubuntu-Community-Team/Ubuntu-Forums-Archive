---
title: "Download Packages question"
date: 2005-01-25
forum: Repositories &amp; Backports
---

### Post by mping on 2005-01-25
does ubuntu package manager support resuming downloads? you see, i cannot download some ~400mb because my ISP charges extra traffic, only have 1GB international per month  :-(  but i have this happy hours where the traffic doesn't count. Instead of downloading package by package, i want to "queue" them and download them only when i say so, so resuming files must be supported.

Is this possible?
tks

---

### Post by mendicant on 2005-01-25
I know it won't redownload individual packages it already has--well, I typically use aptitude, but I imagine it must be the same for all the various package management tools.  For individual files, I'm not so certain, although I suspect so, because of the existence of:

/var/cache/apt/archives/partial

---

### Post by az on 2005-01-25
"does ubuntu package manager support resuming downloads"

Yes, of course.

---

### Post by mping on 2005-01-26
so, resuming packets is automatic, ie, i do not have that much control over things. I want to upgrade my ubuntu, but im thinkin of downloading all the stuph late nite, and downloading only the packages, then I suppose when i try to upgrade, i already have packages on disk and ubunut will be a nice guy and install them on.the.fly :)

---

### Post by mendicant on 2005-01-26
Right.  So you would do something like:

% aptitude update
% aptitude --download-only dist-upgrade
% ## alternatively--this won't install anything not currently installed (like new dependencies)
% ## aptitude --download-only upgrade

In the morning, you would then just do a normal dist-upgrade or upgrade, without the --download-only flag.  You can also insert various monitoring tools to make sure it only happens during certain hours--save the PID, add batch job to check time and kill the download if it hasn't finished already.  In this case, however, you would have to check to see if everything had downloaded.  You can do so using:

% aptitude --simulate --download-only dist-upgrade

which can be done as any user, and check the line saying:
   Need to get XkB/YkB of archives.
If X != 0, the download hasn't finished.

---

### Post by magnus07 on 2007-07-29
I have a working skype package with dapper drake.
Have installed another DD but skype is no longer available.

Questions are:
1) are anywhere available old versions of packages?
2) where are on my HDD the downloaded packages? are them all .deb packages? what would be the skype name then? 
3) other ways to use skype with DD?

Thanks Magnus

---

### Post by Seisen on 2007-07-30
> **magnus07 said:**
> I have a working skype package with dapper drake.
Have installed another DD but skype is no longer available.

Questions are:
1) are anywhere available old versions of packages?
2) where are on my HDD the downloaded packages? are them all .deb packages? what would be the skype name then? 
3) other ways to use skype with DD?

Thanks Magnus

You can go to [packages.ubuntu.com]("http://packages.ubuntu.com") and search under dapper drake for skype.

---

### Post by magnus07 on 2007-07-30
Thanks you pointed me to a great resource but I'm not lucky.
Since skype has copyrights is not there...

Any other way?
Magnus

---

