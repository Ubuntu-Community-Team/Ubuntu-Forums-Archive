---
title: "How to update all packages not just security updates?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by cj13579 on 2011-11-03
Hi All,

So I have had a google for this (quickly I must add) and couldn't find anything particularly obvious. When I log into my box I get the following message:

```
64 packages can be updated.
58 updates are security updates.
```

However when I use aptitude to get the updates it seems like it only ever tries gets the security updates:

```
58 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 51.2MB of archives.
After this operation, 36.9kB of additional disk space will be used.
Do you want to continue [Y/n]?
```


I'm thinking it might be things like my version of Webmin that it knows there is new version of but doesn't include it in the list?

Is there an option that I can put on the apt-get command to download and update ALL of the packages that have updates available to them regardless of whether they are security updates or not?

Many thanks for your help in advance.

---

### Post by wolfen69 on 2011-11-03
```
sudo apt-get upgrade
```

---

### Post by dFlyer on 2011-11-03
copy and paste the following commands:

sudo apt-get update

sudo apt-get upgrade

---

### Post by cj13579 on 2011-11-03
Thanks guys, those are the commands that I have been using and they give me the output in my previous post.

Perhaps it is lying to me and where it says 58 it really means 64? Probably not...

---

### Post by Majorix on 2011-11-03
Sometimes doing a
```
sudo apt-get dist-upgrade
```
will update packages that apt-get upgrade would not update.

---

### Post by dFlyer on 2011-11-03
The 3 not upgraded are files missing update for a lib most likely. Hopefully they will show up over time.

---

### Post by cj13579 on 2011-11-03
Thanks Majorix - we are up to 61!!

This is almost a fun game!!

---

### Post by cj13579 on 2011-11-03
> **dFlyer said:**
> The 3 not upgraded are files missing update for a lib most likely. Hopefully they will show up over time.

In which case 61 one is probably my final offer then?

---

