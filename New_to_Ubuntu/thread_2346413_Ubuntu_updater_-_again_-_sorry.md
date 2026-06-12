---
title: "Ubuntu updater - again - sorry"
date: 2016-12-14
forum: New to Ubuntu
---

### Post by Vaclav Vasek on 2016-12-14
Updater asks for more disk space and I like to comply.
**However disk "/" means nothing to me. **
**How do I identify which disk / partition to extend ? **

Here is the message from updater and cleanup did not resolve the issue. p. 

The upgrade needs a total of 119 M free space on disk '/'. Please free at least an additional 98.3 M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Thanks for your help.

---

### Post by &amp;KyT$0P# on 2016-12-14
Run this command in a Terminal -
```
df -hT
```

One of the listings should be mounted on /
That is the partition you're looking for.

---

### Post by deadflowr on 2016-12-14
please post the results of
```
df -h
```
and look at the partition scheme at hand, try
```
sudo parted -l
```
please post using code tags:[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by &amp;KyT$0P# on 2016-12-14
> **deadflowr said:**
> please post the results of
```
df -h
```
Just saw that [this]("https://ubuntuforums.org/showthread.php?t=2346201&p=13582747&viewfull=1#post13582747") is the same user.

Vaclav Vasek, your partition to extend is [FONT=Courier New]/dev/sda5[/FONT].

---

### Post by Vaclav Vasek on 2016-12-14
I have another issue - that WAS an extended partition I am unable to resize. 
The other partition WAS Linux swap which I have deleted since I have another swap elsewhere. 
So far my OS is still working. 

The partition is at the "end" of the drive and I cannot unmount it nor resize to unallocated space before the partition. 
On top of that I have unimplemented / unused "RAID" partition I am also unable to delete. 

It is just grand mess I need to clean up for both updater and backup. 
Appreciate all the help received so far.

---

