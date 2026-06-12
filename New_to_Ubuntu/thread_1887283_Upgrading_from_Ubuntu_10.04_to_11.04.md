---
title: "Upgrading from Ubuntu 10.04 to 11.04"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by kuckunniwi on 2011-11-26
Hi!

I'm thinking of upgrading my Mom's netbook from Lucid to Natty, as I've tried the LiveCD, and Natty seems to natively support the WLAN adapter, which Lucid didn't (was having some trouble with the driver I've been using). Oneric is out of the question, as my mom is 60+, and there's no way she's going to be able to handle the switch-over to Unity, and Natty, from what I've seen, allows the option to choose between unity and our beloved old gnome2.

**My question is:**

(I have separate partitions for *root* and */home*)

- Is it worth it, to save time, to make a new install, _leaving */home* partition untouched_, or am I going to have tons of software issues due to all the *left-over* files from previous versions? Or is it better just to make a clean install, and then restore all files? (the only reason I'm considering the first option is 'cause she has tons of music and movies that are fairly time-consuming to back-up & restore...)

Either way, I've made a backup of her entire hard drive, for in case...

Thanks!!!

---

### Post by Frogs Hair on 2011-11-26
If you wanted to upgrade the path would be 10.04 > 10.10 > 11.04 . Since you have a backup I think a clean installation would be easier than two upgrades .

---

### Post by kuckunniwi on 2011-11-26
> **Frogs Hair said:**
> If you wanted to upgrade the path would be 10.04 > 10.10 > 11.04 . Since you have a backup I think a clean installation would be easier than two upgrades .

Thanks! Although what I actually meant to ask was:

Do you think I can make a clean install, but leave my /home partition intact during installation? Or will that cause issues in 11.04, due to *remnants* in home folder from 10.04 software?

---

### Post by Frogs Hair on 2011-11-26
You would have to move home to its own partition , which many people do . I have not tried that, but I do move my backed up files from one installation to the other every 6 months via Ubuntu One .

Files , such as pictures and documents should not cause any problems . I did try to transfer a backup from a " Back in Time " image as an experiment and it didn't work .

Here is a tutorial and there are others . [http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

---

### Post by kuckunniwi on 2011-11-26
> **Frogs Hair said:**
> You would have to move home to its own partition , which many people do . I have not tried that, but I do move my backed up files from one installation to the other every 6 months via Ubuntu One .

Files , such as pictures and documents should not cause any problems . I did try to transfer a backup from a " Back in Time " image as an experiment and it didn't work .

Here is a tutorial and there are others . [http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

Frogs Hair, I appreciate your help, but I don't think you've actually read my first post, hence, my original question in still unanswered...(no offence intended, but if you read the post, you'll see why I'm saying this...)

- I already have a separate partition for home
- I intend on making a clean install, leaving the /home partition the way it is
- What I'd like to know, is if **I might have software problems due to software data (from Lucid) stored in /home conflicting with new software from Natty**

Thanks!

---

### Post by lswb on 2011-11-26
As an alternative, if the only problem is with your wireless adapter, it's possible there's a backported driver for 10.4, or sometimes using a later kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) can help.

---

### Post by bluexrider on 2011-11-26
The answer is NO!

You have 2 partitions 1 for root and 1 for home--GOT IT.
 
Those files in your home folder can remain there. They will not interfere with the upgrade.

---

### Post by kuckunniwi on 2011-11-26
Thanks, guys!

---

### Post by NT4usB on 2011-11-26
> **kuckunniwi said:**
> Hi!...(I have separate partitions for *root* and */home*)...

I have one box that has used the same /home since Dapper 6.06. (currently 10.04)
I format all the other partitions and install fresh, recycling /home each time.
Really makes upgrades painless since all the apps I use retain their settings.

---

### Post by kuckunniwi on 2011-11-26
> **NT4usB said:**
> I have one box that has used the same /home since Dapper 6.06. (currently 10.04)
I format all the other partitions and install fresh, recycling /home each time.
Really makes upgrades painless since all the apps I use retain their settings.

Now THAT is nice to know! I have a back-up just for in case, but hearing that, I'll be happily proceeding with a fresh install of Natty, with a recycled /home! Many, many thanks, NT4usB !!! :D

---

### Post by Miljet on 2011-11-26
The only thing is, you may end up with some "orphan" configuration files. For instance, if Ubuntu has changed the default photo viewer, the config files for the old viewer will still be in your home directory. They won't cause any problems, they just will not be used.

---

### Post by Frogs Hair on 2011-11-26
> **kuckunniwi said:**
> Frogs Hair, I appreciate your help, but I don't think you've actually read my first post, hence, my original question in still unanswered...(no offence intended, but if you read the post, you'll see why I'm saying this...)

- I already have a separate partition for home
- I intend on making a clean install, leaving the /home partition the way it is
- What I'd like to know, is if **I might have software problems due to software data (from Lucid) stored in /home conflicting with new software from Natty**

Thanks!

> (I have separate partitions for root and /home) Sorry I don't know how i missed that !!!:oops:

---

### Post by beew on 2011-11-26
Don't upgrade.  Backup your data and do a clean install, and since you have a /home that is easy, just remove all your configuration files that you don't need. Aside from taking up space some *may* cause you problem, say Compiz, the old configuration and settings probably won't work with Unity. So it is true that if you install something different the old config files will not cause troubles other than taking up space, but what if you install the same program which nevertheless has changed quite a bit?

---

### Post by lolpenguin on 2011-11-26
> **beew said:**
> Don't upgrade.  Backup your data and do a clean install, and since you have a /home that is easy, just remove all your configuration files that you don't need. Aside from taking up space some *may* cause you problem, say Compiz, the old configuration and settings probably won't work with Unity. So it is true that if you install something different the old config files will not cause troubles other than taking up space, but what if you install the same program which nevertheless has changed quite a bit?

Especially when upgrading Ubuntu Netbook Edition 10.10 to Natty. ubuntu-desktop isn't installed so the upgrade will be carried out incorrectly (since natty doesn't have an ubuntu-netbook package)

---

### Post by NT4usB on 2011-11-27
> **beew said:**
> Don't upgrade.  Backup your data and do a clean install, and since you have a /home that is easy, just remove all your configuration files that you don't need. Aside from taking up space some *may* cause you problem, say Compiz, the old configuration and settings probably won't work with Unity. So it is true that if you install something different the old config files will not cause troubles other than taking up space, but what if you install the same program which nevertheless has changed quite a bit?

I don't try to remove any config files before upgrading. I run the commands I'm used to using and simply install the programs for which the commands don't work after the install.
I've never had use for Compiz, and likely will never use Unity so those aren't an issue.
I have even used the same old /home for brand new builds. Saves much configuring and copying for things like Firefox and Thunderbird. 
Sure, I could copy individual config folders. Trying to remember what all that entails vs running commands that have long since been committed to muscle memory and installing as required is easier, for me...

---

