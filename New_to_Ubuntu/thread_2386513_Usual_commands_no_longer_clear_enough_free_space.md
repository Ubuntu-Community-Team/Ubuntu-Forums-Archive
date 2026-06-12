---
title: "Usual commands no longer clear enough free space"
date: 2018-03-07
forum: New to Ubuntu
---

### Post by steve169 on 2018-03-07
I boot Lubuntu 16.04 from an encrypted 16-Gb thumb drive to do my online banking. Works fine.

When I've updated (security updates only), I've used the **autoremove** and **clean** commands to clear sufficient free space, and they have always done the job.

But not this time. When I try to update, it says there still isn't enough free space.

Any suggestions?

Here is some information about the thumb drive.

After running the **ls** command:

[ATTACH=CONFIG]278833[/ATTACH]

After running **Gparted**:

[ATTACH=CONFIG]278832[/ATTACH]

---

### Post by blade4 on 2018-03-07
A few questions: 
[LIST]
[*]Are you certain the build-up is due to system updates and not something else ? Maybe try running disk usage analyzer with root to see which files are taking up all the space ?
[*]Is your swap file set on your USB drive ? If yes, how big is it ?
[/LIST]

---

### Post by wyliecoyoteuk on 2018-03-07
try:

df -h

---

### Post by steve169 on 2018-03-07
Here's what I got by running **df**:

[ATTACH=CONFIG]278837[/ATTACH]

I ran **Gparted** (see first post) but see no separate partition for a swap file. I thought one was there when I orginally installed Lubuntu.

---

### Post by monkeybrain20122 on 2018-03-07
Do you store data in your drive? Since you don't have a separate /home it is hard to know what is eating up your space from df -h output. autoremove and clean only clean system files, it doesn't remove junks in  your home directory (e.g cache from browser, which can grow pretty fast especially if you watch videos. You can easily recover  > 1 G from there) You can also recover ~ 1 G by removing unused language packs

---

### Post by thehipho on 2018-03-07
```
du /home -hs
```

To find size of /home dir. Also bleachbit has nice gui to clean out junk files.

---

### Post by wyliecoyoteuk on 2018-03-07
or try
 du /var -hs
 /var is where all the logs are stored, if you have a runaway problem it can often fill up the /var/log directory

du /var -h will show you the size of all the dirs in var

---

