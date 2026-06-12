---
title: "Unable to parse package file"
date: 2013-07-04
forum: New to Ubuntu
---

### Post by GrayBaker on 2013-07-04
Hello. This is my first time here. I am new to Ubuntu. And new to using Terminal for everything. But I have seem to run into a snag. Every time I try to install or update anything, I get this notification,

> E: Unable to parse package file /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_raring_universe_i18n_Translation-en (1)



I can't install anything because of this, and it has been this way for a few days. Can anybody help? 
Cheers,
Gray

---

### Post by claracc on 2013-07-04
Here, [http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err) you have a link to fix your problem.

In a xterm, you have to run the following commands:

```
sudo rm /var/lib/apt/lists/* -vf

```

and then:

```
sudo apt-get update
```

After it, you will be allowed to install updates.

---

