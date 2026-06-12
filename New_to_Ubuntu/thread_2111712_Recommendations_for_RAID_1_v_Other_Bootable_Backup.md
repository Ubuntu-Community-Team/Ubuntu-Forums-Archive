---
title: "Recommendations for RAID 1 v Other Bootable Backup"
date: 2013-02-02
forum: New to Ubuntu
---

### Post by n8henrie on 2013-02-02
Hi everyone, and thanks for all the great information in this forum. I've been learning a ton just reading old threads.

I'm pretty new to Linux but decided to go with a 12.04 server edition on my old PC hoping to use it to accomplish a few tasks around the house and improve my CLI skills.

One of the things I'm thinking of using it for is as a Time Machine backup destination for my Macbook Pro and possibly my girlfriend's as well. I have netatalk running fine and I think this should work out well. 

However, I'd also like to have a backup of the Ubuntu box itself. One of the things I was considering would be a (software) RAID 1 setup, which seems like it would work great. However, I'd want to exclude the Time Machine directory, because it seems like it would be a waste of space to RAID 1 a backup (meaning I'd have a triplicate copy of that data).

Instead of a RAID setup, I was also thinking I could probably do something with rsync, which would facilitate excluding that Time Machine directory, but I'm not sure if the result would be bootable. I'd just hate to lose all the time that goes into the details and config files if anything were to happen.

The other concern would be encryption. I have home directory encryption enabled with ecryptfs, but I'm not sure if the rsync backup would play nice with that (especially depending on whether or not I was logged in and therefore the home directory decrypted).

Do any of you have suggestions on my best bet for a bootable backup that could exclude a particular directory and would also work well with home directory encryption?

Many thanks.

---

### Post by mapes12 on 2013-02-03
Have a look at Remastersys for creating a bootable backup of your system. Once you have everything tweaked how you like it Remastersys creates a bootable iso file that you can use to reinstall it. You´ll need to make sure your system is less than 4GB. I keep all my personal data on a seperate partition and use Grysnc to back it up to another machine.

Time Machine likes to have a didicated drive partition to do it´s stuff. You probably know this anyway if you have a Mac.

Good luck.

Mark

---

### Post by n8henrie on 2013-02-03
Thanks for the tip on Remastersys, I'll check it out.

Yeah, that's one of the problems I was alluding to with the RAID and Time Machine. Say I set up a 500 GB partition dedicated to Time Machine for both my and my girlfriend's Macbooks, including that in the backup or RAID would be a full TB of wasted, triplicate information.

Remastersys might just be a good option, thanks again.

---

### Post by Cheesemill on 2013-02-03
You should bear in mind that RAID by itself is *not* a backup strategy.

RAID protects you against one thing and one thing only, it gives you continuity in case of drive failure. It doesn't protect you against hardware failure, user error, software bugs or any number of other situations which a proper backup strategy would handle.

---

### Post by n8henrie on 2013-02-04
> **Cheesemill said:**
> You should bear in mind that RAID by itself is *not* a backup strategy.

RAID protects you against one thing and one thing only, it gives you continuity in case of drive failure. It doesn't protect you against hardware failure, user error, software bugs or any number of other situations which a proper backup strategy would handle.

Thanks for your input. I'm a bit confused, how do you mean that it protects against drive failure, but not hardware failure? What other hardware?

By a "proper" backup strategy, I assume you mean something versioned, to allow restoration from a "pre-user-error" type problem?

---

### Post by Cheesemill on 2013-02-04
> **n8henrie said:**
> Thanks for your input. I'm a bit confused, how do you mean that it protects against drive failure, but not hardware failure? What other hardware?
A faulty drive controller or RAM could cause corrupt data to be written to the array, a PSU that blows could take out all of your drives in one go, there is always flood, fire and theft to consider.

> By a "proper" backup strategy, I assume you mean something versioned, to allow restoration from a "pre-user-error" type problem?
It doesn't have to be that complicated. Instead of a RAID1 I would just have an internal 1TB drive and an external 1TB drive, every week just connect the external and use rsync to update all of the changed files. Ideally you would keep this external drive off-site when it wasn't being used to protect against the aforementioned fire, flood and theft. I have a friend who lives in the same village as me and we store our backup drives at each others houses.

As I said in my earlier post RAID1 is next to useless as a backup strategy, the only situation where I use a RAID1 array is in servers at work, it allows for a single failed drive to be changed in a running server without any downtime. It is a business continuity strategy and has nothing to do with backup strategy.

---

### Post by n8henrie on 2013-02-04
That makes a lot of sense, thanks for the insight.

I guess by that criteria any backup that is not a remote backup is "not much of a backup." For my Mac, I currently have both a local Time Machine backup and a remote Crashplan. However, neither of those is bootable, so it would take me at least a little while to get back up and running.

I have Crashplan running on Ubuntu as well, which supports backing up to a friend's house for free, but again this would not back up my system files and configuration AFAIK, so not a good system.

The prospect of having to trade out the external drive manually seems less than ideal, but I can see why you do it that way.

---

