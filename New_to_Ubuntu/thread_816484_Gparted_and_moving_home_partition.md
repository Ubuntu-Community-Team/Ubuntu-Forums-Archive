---
title: "Gparted and moving /home partition"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Nordmoen on 2008-06-02
Well I'm thinking of using this guide :[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome") but before I do I'm pondering two things:

1) I'm using Ndswrapper because of my broadcom wireless card, will it work when using the Live Cd or do I have to connect with a cable?

2) The guide is talking about an empty /home folder, but I have some minor things in my /home/(user name) folder which I want to keep. Could I just copy it over to an external HDD and the just move it back to the new /home folder on the new partition? I have also done som minor changes to apperance and other stuff, will that change or is there just things in the /home/(user name) folder which will be lost in the transfer process?

Thanks for any replies :)
(Excuse my bad english, it's not my first language)

---

### Post by ibuclaw on 2008-06-02
1) GParted is on the LiveCD under "**System>Administration>Partition Editor**", no internet connection is required.

2) Once the filesystem is created, you'll have to copy the **contents** of your /home folder to the new partition. (Don't move them just yet)

Then when you reboot and load up Ubuntu. You'll have to edit your fstab file to change the location of you /home folder.

I don't yet know anything about what your hard-drives look like, (or what they will look like after you've created the partition). So I can comment no further.

Regards
Iain

---

### Post by Nordmoen on 2008-06-02
So what you are saying is just make the new partition, then boot up normaly, then copy the home folder, then edit fstab? 

Or copy home folder when inside the live cd?

Will it help if I make the new partition the post fstab once booted normaly?

---

### Post by Bruce M. on 2008-06-02
> **Nordmoen said:**
> Well I'm thinking of using this guide :[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome") but before I do I'm pondering two things:

1) I'm using Ndswrapper because of my broadcom wireless card, will it work when using the Live Cd or do I have to connect with a cable?

Since it is the LIVE CD, you can try it and see without interfering at all with your system.  That should tell you if it will see your wireless card or not.

> **Nordmoen said:**
> 2) The guide is talking about an empty /home folder, but I have some minor things in my /home/(user name) folder which I want to keep. Could I just copy it over to an external HDD and the just move it back to the new /home folder on the new partition? I have also done som minor changes to apperance and other stuff, will that change or is there just things in the /home/(user name) folder which will be lost in the transfer process?

I think you misunderstood the guide. The guide you referred to is if you have your **/home** directory in the same partition that you have for your [SIZE="5"]**/**[/SIZE] (root) partition.  It's probably isn't empty, there are hidden files there as well, like your bookmarks and configuration files for Firefox for one example.

> (i.e., /home is just a folder inside your [SIZE="5"]**/**[/SIZE] partition).

There is a wonderful program: QuickStart (see my signature) that will backup your [SIZE="5"]**/**[/SIZE] directory, your **/home** directory and your config files for you.  It is very important to do this before trying to create a separate partition for your /home directory.

Just make sure you move or store those files in another area, an empty partition, a CD or DVD along with the QS startup file. Or you can always re-download it from the forum.

Just so you know, I used the same guide to do what you want to do and it worked very well. It's a very good idea to have **/home** separated from the [SIZE="5"]**/**[/SIZE] directory.


> **Nordmoen said:**
> Thanks for any replies :)
(Excuse my bad english, it's not my first language)

Your English is just fine, no need to excuse yourself at all.

If you have more questions just ask.
Bruce

**EDIT: I agree with the guide here:**

> Requirements
You must use a live CD for this process, for two reasons:

   1. In order to resize your existing / partition, it needs to be unmounted. The only way to unmount it is for it not to be in use, which means you can't boot to your regular Ubuntu installation while resizing it... which means you need a live CD
   2. If you screw up your installation by accident, you can use the live CD to restore your old settings and, in the worst situation, at least recover your important files.

---

### Post by ibuclaw on 2008-06-02
> **Nordmoen said:**
> So what you are saying is just make the new partition, then boot up normaly, then copy the home folder, then edit fstab? 

Or copy home folder when inside the live cd?

Will it help if I make the new partition the post fstab once booted normaly?

Yes, if you have the space. You can go off and create the new partition right now.

Then when you reboot back into your system, paste the output of these commands in the terminal:
```
sudo fdisk -l
```
and
```
df -h
```

Regards
Iain

---

### Post by Nordmoen on 2008-06-02
> **Bruce M. said:**
> Since it is the LIVE CD, you can try it and see without interfering at all with your system.  That should tell you if it will see your wireless card or not.



I think you misunderstood the guide. The guide you referred to is if you have your **/home** directory in the same partition that you have for your [SIZE="5"]**/**[/SIZE] (root) partition.  It's probably isn't empty, there are hidden files there as well, like your bookmarks and configuration files for Firefox for one example.



There is a wonderful program: QuickStart (see my signature) that will backup your [SIZE="5"]**/**[/SIZE] directory, your **/home** directory and your config files for you.  It is very important to do this before trying to create a separate partition for your /home directory.

Just make sure you move or store those files in another area, an empty partition, a CD or DVD along with the QS startup file. Or you can always re-download it from the forum.

Just so you know, I used the same guide to do what you want to do and it worked very well. It's a very good idea to have **/home** separated from the [SIZE="5"]**/**[/SIZE] directory.




Your English is just fine, no need to excuse yourself at all.

If you have more questions just ask.
Bruce

**EDIT: I agree with the guide here:**
Ok I think I understand what the guide intendes to do, and that is what I want(so its easier to install a new Os, or upgrade ubuntu from cd in the future). But what I don't quite understand is, will moving my /home folder(if I follow the guide down to every step) loose any data(if every thing goes according to plan)? I understand the need for backup(thanks for the tip about QuickStart) but in theory is it necessary?

---

### Post by avtolle on 2008-06-02
I've used the same guide >5 times to create a separate home partition without data loss; but, I've always backed up "just in case", too. While I've not had a problem to date, that doesn't mean someone else will have my experience, or that the next time I do this, I will have the same good fortune. So, backing up is a "cheap" insurance policy, if you will. Good luck, and following the guide precisely step by step gives the best result.

---

### Post by Aelfric5578 on 2008-06-02
If you follow the steps on that tutorial exactly, there is a backup process built into the tutorial.

```
cd /old/home
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
sudo mv /old/home /old/home_backup
sudo mkdir /old/home
```

The second line which the tutorial writer doesn't really explain takes every file, hidden or otherwise in your home directory and copies it to the new partition.  Then you rename the old home directory so nothing is lost.  If you wanted to backup to an external before resizing the partition though, it's not a bad idea by any means.

---

### Post by Bruce M. on 2008-06-02
> **Nordmoen said:**
> Ok I think I understand what the guide intendes to do, and that is what I want(so its easier to install a new Os, or upgrade ubuntu from cd in the future). But what I don't quite understand is, will moving my /home folder(if I follow the guide down to every step) loose any data(if every thing goes according to plan)? I understand the need for backup(thanks for the tip about QuickStart) but in theory is it necessary?

That's the key; those words you said: ***in theory***!

And in theory it isn't necessary.

But real life isn't *a theory*, backup just to be safe.  :)

When I did it, it worked without a problem.

**EDIT:** After I moved my /home I have always done a clean install with the ALT CD, as it allows you to put /home in a separate partition during set-up.

Bruce

---

