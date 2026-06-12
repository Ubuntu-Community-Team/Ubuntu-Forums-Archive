---
title: "Nautilus crashes when I view a certain folder"
date: 2014-10-15
forum: New to Ubuntu
---

### Post by akoubu.9a on 2014-10-15
Using Nautilus, when I view a certain folder in my /home/, Nautilus crashes. How can I find out why? And how can I fix this?

---

### Post by akoubu.9a on 2014-10-15
UPDATE: When I use Google Chrome to view the folder/files in question, Chrome doesn't crash.

---

### Post by mc4man on 2014-10-15
Does it contain any 0 byte files?

---

### Post by yancek on 2014-10-15
Try opening nautilus from a terminal and if it crashes look at the output in the terminal, it might show a reason or at least give a clue.
What's in the folder?

---

### Post by akoubu.9a on 2014-10-15
What's the fastest way to  check if it has 0 byte files, without using Nautilus?

When I use Terminal to start Nautilus, Terminal has nothing after Nautilus crashes.

The folder contains photos and Picasa config files.

---

### Post by mc4man on 2014-10-15
cd to the folder in question in a terminal, ie. cd foldername
 then run 
Edit: wrong command - sorry
```
ls -l
```
If there are any files of 0 size **with an extension**, like .mp3, .pdf, ect.  then post names (size is 1st set of numbers after your user names

---

### Post by tgalati4 on 2014-10-16
Also:

```
nautilus --check
```

Check /var/log/syslog for any disk read/write errors.

---

### Post by glyczak on 2014-10-18
I've had a similar issue regarding privileges when sharing directories.

---

### Post by Vladlenin5000 on 2014-10-18
> **glyczak said:**
> I've had a similar issue regarding privileges when sharing directories.

This isn't a file(s) permissions issue.

---

### Post by mc4man on 2014-10-18
Well the Op has not returned nor ever posted what release of ubuntu. There was a limited time where if python-nautilus & certain nautilus-python scripts were installed then nautilus would crash if opening a folder that contained 0 byte files of certain types.
So it could have been the issue here..

(- [https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1203349](https://bugs.launchpad.net/ubuntu/+source/nautilus-python/+bug/1203349)

---

