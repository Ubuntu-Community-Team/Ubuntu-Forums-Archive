---
title: "Merging partitions without losing data"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by Muditha Jayath on 2012-02-14
How do I merge partitions after installing Ubuntu on a hard disk which was formerly used to have Windows installed and currently data on its partitions? I really need those data and no way of backing up them. (I don't have any external storage devices to meet the size of data.) There are no data on the partition where Windows were installed and I'm thinking of installing Ubuntu on it. So, after that I want to merge all other partitions as one.
:confused::confused::confused:

---

### Post by josephmills on 2012-02-14
> **Muditha Jayath said:**
> How do I merge partitions after installing Ubuntu on a hard disk which was formerly used to have Windows installed and currently data on its partitions? I really need those data and no way of backing up them. (I don't have any external storage devices to meet the size of data.) There are no data on the partition where Windows were installed and I'm thinking of installing Ubuntu on it. So, after that I want to merge all other partitions as one.
:confused::confused::confused:

There is a thing called ubuntu one that gives you 5 gigs of online storage. if you like you could back up there. [https://one.ubuntu.com/](https://one.ubuntu.com/)

but there are mny of ways of doing this could you please open your terminal (ctrl+alt+t) then enter ```
sudo fdisk -l
``` and paste here ? thanks

---

### Post by perspectoff on 2012-02-14
cp -a

will copy all (including permissions).

Here are my tips:

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric_System_Backup#cp](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_System_Backup#cp)

---

### Post by tommyleinen on 2012-02-14
You could try gparted from a usb drive if you are desperate. I would be very reluctant without backing up first though as you may hose the lot.
I did this on a smaller scale, I had an 8gb usb with fat32 4gb storage partition followed by 1gb Linux swap,followed by 3gb ext3 partition with ubuntu on it. I made sure no data on storage, swap was labelled as none used already, and obviously the system partition had data on it. I was able to reduce storage to 2gb, dragged the swap over but kept at 1gb and expanded the system partition making sure the new ones were linux-swap / ext3. The system booted first time afterwards. I was expecting to have to do a fresh install as the boot files are likely to be affected.
I hope this helps but please don't do that thinking you will have the same outcome, i dont know what order your partitions are in and in my case, I was quite prepared to lose it all. Good luck in resolving it!

---

### Post by Bartender on 2012-02-14
> **Muditha Jayath said:**
> I really need those data and no way of backing up them.

I'm not saying this to be mean, but it's pretty clear that you don't have a lot of experience at this.  If you can't back up the data externally, you should not take on any high-risk experiments.  It's as simple as that.

Can you scrounge up a small HDD that you could plug in to your PC as the master?  You could unplug your Windows drive, then install Ubuntu, then reconnect the Windows drive.  That's not a final solution, but it would at least allow you to access your Windows data safely until you can come up with a better solution.

---

### Post by tommyleinen on 2012-02-15
> **Bartender said:**
> I'm not saying this to be mean, but it's pretty clear that you don't have a lot of experience at this.  If you can't back up the data externally, you should not take on any high-risk experiments.  It's as simple as that.

Can you scrounge up a small HDD that you could plug in to your PC as the master?  You could unplug your Windows drive, then install Ubuntu, then reconnect the Windows drive.  That's not a final solution, but it would at least allow you to access your Windows data safely until you can come up with a better solution.

I have to agree, if the data means this much to you, you will not risk it and find a way. I once used an old drive from my PVR and a couple of mp3 players to back up before sending my lappy for repair ;)

---

### Post by Bartender on 2012-02-15
I've installed Ub/Xub/Kubuntu/PCLOS/Mepis/Fedora/Mint/OpenSUSE at least 50X by now to more than a dozen different PC's.  I'm pretty comfortable with partitioning, making CD's, etc.

So for me, installing Ubuntu to a drive that has important data on it would be a calculated risk.  I could weigh the relatively high chances of success against the horror of losing the data for good.  Which means I'd back up the data.

These kinds of threads are the ones that come just before the "Ubuntu wiped out my Windows data!!:mad::mad:" posts.

---

### Post by Muditha Jayath on 2012-02-24
> **Bartender said:**
> I'm not saying this to be mean, but it's pretty clear that you don't have a lot of experience at this.  If you can't back up the data externally, you should not take on any high-risk experiments.  It's as simple as that.

Can you scrounge up a small HDD that you could plug in to your PC as the master?  You could unplug your Windows drive, then install Ubuntu, then reconnect the Windows drive.  That's not a final solution, but it would at least allow you to access your Windows data safely until you can come up with a better solution.

Yes Bartender, I'm quite new to Linux. Except for basic works, I have not much of advance knowledge of Linux as much as I have of Windows. I don't like to pay much money on Windows licensing and for other software when I can get a free OS with bunch of free software. That's why I thought of moving to Linux. Haha, don't worry friend, I didn't do anything stupid to lose data before I post this. I'll find a way to backup my data then. I thought there might be a way of merging partitions without losing any data as I did on Windows using PartitionMagic. :):) Thank you and every other members very much for your kind concern about the matter. :D

---

