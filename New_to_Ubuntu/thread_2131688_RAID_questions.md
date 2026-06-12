---
title: "RAID questions"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by kc5hwb on 2013-04-02
I've searched the forum for this answer, and found little information about my exact setup, so I wanted to post this question here.

**Reconnecting a RAID:**
What I've done is setup a RAID1 array with Ubuntu 12.04 using MDADM.  I currently have 3-HDDs in the box, the C:\ drive runs the OS and the other 2 drives are SATA connections, both raided using MDADM in Ubuntu.  
What I want to know is... if my C:\drive fails and I have to replace it, or simply reformat and reinstall Ubuntu, how can I get the new Ubuntu OS to recognize the existing RAID without losing any data?  Or is this possible at all?  I'm sure its possible, just want to know how to do it.

**Opinions on the usage of a RAID:**
As I was searching for the answer above, I read a forum member post about RAIDs saying that he didn't like RAIDs for data-loss protection purposes.  He suggested using a regular drive and running GRSYNC or something similar to perform routine backups instead of messing with a RAID.  I've always read that RAIDs were great for redundancy and protection against loss of data, but I'd like to hear opinions on this too.  My main purpose for setting up this RAID was to protect against data loss.  I have this setup on my personal home network, and its just my wife and I accessing it, so not alot of traffic at all.

Thanks for the help.

---

### Post by Cheesemill on 2013-04-02
> **kc5hwb said:**
> What I want to know is... if my C:\drive fails and I have to replace it, or simply reformat and reinstall Ubuntu, how can I get the new Ubuntu OS to recognize the existing RAID without losing any data?  Or is this possible at all?  I'm sure its possible, just want to know how to do it.
Once mdadm is installed on the new OS, it should automatically pick up the existing array and reassemble it.
The only thing you should have to do is add an entry in your fstab to mount the array.

> I've always read that RAIDs were great for redundancy and protection against loss of data, but I'd like to hear opinions on this too.  My main purpose for setting up this RAID was to protect against data loss.

RAID isn't designed to protect against data loss at all, the only thing RAID should be used for is to provide continuous access to your data in case of drive failure.

RAID in no way is a backup strategy, all it protects against is hard drive failure. By only having RAID your data is still vulnerable to hardware failure, buggy software, user error or other situations (fire/flood/theft).

For a proper backup you should have a copy of your data that is separate from the main storage, preferably in an off-site location. Although this sounds extreme it doesn't have to be expensive, me and a friend who live in the same village keep an external drive at each others house and once a week or so I will grab my external and use rsync to get my backup up to date. If backup isn't taken seriously it can provide you with a false sense of security, I ***know*** that all my family photos and important documents are safe, but if you only use a RAID array and you mistype a command you can lose everything.

That's not to say that RAID doesn't have its place, it's great for large storage pools and improving performance of your drives and I use it myself for large media collections.
All I'm trying to get across is that RAID is not a backup strategy, it never has been and it never should be.

---

### Post by kc5hwb on 2013-04-02
> **Cheesemill said:**
> 
For a proper backup you should have a copy of your data that is separate from the main storage, preferably in an off-site location. Although this sounds extreme it doesn't have to be expensive, me and a friend who live in the same village keep an external drive at each others house and once a week or so I will grab my external and use rsync to get my backup up to date. If backup isn't taken seriously it can provide you with a false sense of security, I ***know*** that all my family photos and important documents are safe, but if you only use a RAID array and you mistype a command you can lose everything.

This is a good idea, I hadn't thought about trading with a friend.  I will have to look into doing this, thanks.

> **Cheesemill said:**
> 
That's not to say that RAID doesn't have its place, it's great for large storage pools and improving performance of your drives and I use it myself for large media collections.
All I'm trying to get across is that RAID is not a backup strategy, it never has been and it never should be.

I actually use both RAID and Grsync also, although I always thought a RAID was a safer solution for storing files.  Perhaps "backup solution" is a misnomer. Basically what I meant was, I just wanted a safer place to store my files so that if 1 drive failed, I wouldn't lose everything.

---

