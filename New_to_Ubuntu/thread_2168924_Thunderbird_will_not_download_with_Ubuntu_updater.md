---
title: "Thunderbird will not download with Ubuntu updater"
date: 2013-08-19
forum: New to Ubuntu
---

### Post by ed5 on 2013-08-19
This is the error I get, all other software downloads fine.


Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by sandyd on 2013-08-19
> **ed5 said:**
> This is the error I get, all other software downloads fine.


Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

The Mozilla ThunderBird-Stable PPA no longer exists.
Run
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:mozillateam/thunderbird-stable
sudo apt-get update

``` to remove the Thunderbird Stable PPA and use the Thunderbird versions from the Ubuntu Repositories

---

### Post by ed5 on 2013-08-19
> **sandyd said:**
> The Mozilla ThunderBird-Stable PPA no longer exists.
Run
```

sudo sudo ppa-purge ppa:mozillateam/thunderbird-stable
sudo apt-get update

``` to remove the Thunderbird Stable PPA and use the Thunderbird versions from the Ubuntu Repositories

Will this erase all of my email addresses and messages?

---

### Post by carl4926 on 2013-08-19
> **ed5 said:**
> Will this erase all of my email addresses and messages?
No it will not

---

### Post by ed5 on 2013-08-20
> **carl4926 said:**
> No it will not


ppa-purge: command not found

---

### Post by Vladlenin5000 on 2013-08-20
Install it.

---

### Post by ed5 on 2013-08-20
> **ed5 said:**
> ppa-purge: command not found

Try this link, it fixed mine.

[http://subfictional.com/2013/01/05/how-to-install-firefox-and-thunderbird-including-beta-aurora-nightly-on-ubuntu/](http://subfictional.com/2013/01/05/how-to-install-firefox-and-thunderbird-including-beta-aurora-nightly-on-ubuntu/)

---

### Post by Vladlenin5000 on 2013-08-20
It won't fix it because the PPA that no longer exists will still be there. You can however purge the old PPA as instructed above - you might have to install ppa-purge first as already mentioned* - and then follow the instructions above in order to install the beta versions from the respective repositories. 
I'm using Firefox Aurora and so far so good, nice and smooth. I don't recommend doing the some for Thunderbird, i.e., installing the 'earlybird' version because, unlike Aurora a) it's quite unstable and b) doesn't have support for other languages.


* ```
sudo apt-get install ppa-purge
```

---

