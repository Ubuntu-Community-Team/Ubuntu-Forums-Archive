---
title: "How to remove ms dos extended partition sda2"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by salezd on 2013-12-27
Hi, I install Lubuntu 12.04. alongside windows xp and now I want to delete xp partition.I delete NTFS partition which was my windows xp(sda1),and now I want to delete an extended partition(sda2) which has the name container for logical partition but I can't do it. Would that harm my system?I get this error "/dev/sda2 is an MS-DOS extended partition and one or more logical partitions are busy".I install gparted but I am not quite familiar with it so if anyone can explain me.

---

### Post by newb85 on 2013-12-27
More than likely, that extended partition houses your Ubuntu partitions, and removing it would take out Ubuntu.   Lucky for you, Ubuntu doesn't let you make changes to partitions it currently has mounted.

---

### Post by coffeecat on 2013-12-27
> **salezd said:**
> Would that harm my system?

Probably.

An extended partition is a container for logical partitions, and the message "one or more logical partitions are busy" suggests that your Ubuntu partitions are logical ones inside the extended partition. So that we can see what your setup is like, post a screenshot of the Gparted window (Alt+PrtScr) and the output of this terminal command:

```
mount
```

Don't try to do anything with Gparted - just open it to get a screenshot.

What are you trying to do? Why do you want to delete the extended partition?

---

### Post by salezd on 2013-12-27
I was trying to delete extended partiton because I thought it is windows partition and I thought I wouldn"t harm my system.But if it contains Linux I will not delete it.By the way that partition has 11 GB and it is not mounted.I"m sorry I am new in Ubuntu,what to do after I type mount in the terminal?

---

### Post by salezd on 2013-12-27
Alright this is my screenshot..
[I fi/home/sasha/2013-12-27-190823_924x742_scrot.png]("http://ubuntuforums.org/home/sasha/2013-12-27-190823_924x742_scrot.png")

---

### Post by coffeecat on 2013-12-27
> **salezd said:**
> I"m sorry I am new in Ubuntu,what to do after I type mount in the terminal?

Open a terminal, type "mount" (without the quotes) and then press enter. A few lines will appear below your mount command. You need to copy and paste them into your post. I'm not familiar with the Lubuntu terminal, but I hope it allows copy and paste the same way as the Ubuntu terminal. Highlight the output you wish to copy and paste, right-click and choose copy. You should then be able to paste it into your post with the standard ctrl-v shortcut.

> **salezd said:**
> Alright this is my screenshot..
[I fi/home/sasha/2013-12-27-190823_924x742_scrot.png]("http://ubuntuforums.org/home/sasha/2013-12-27-190823_924x742_scrot.png")

That doesn't work. You've simply posted the path to the screenshot in your home folder. Click on the "Reply to thread" orange button, or the Go Advanced button below the quick reply message box to get to the advanced message editor. You then need to upload your screenshot by clicking on the Manage Attachments button below the message editor or the paperclip icon in the toolbar. Upload your image with the Add Files button and then insert it into the post with the Insert Inline button.

---

### Post by salezd on 2013-12-27
[ATTACH=CONFIG]248953[/ATTACH]

I done it,there it is.

---

### Post by coffeecat on 2013-12-27
That tells us that your two Ubuntu partitions are indeed logical partitions inside your extended partition. You have a root partition formatted ext4 which is 8.92GiB in size and a swap partition of 1.22 GiB. Your root partition is roughly analogous to your C: drive in Windows. The separate swap partition is the usual arrangement with Linux based installations, unlike Windows which has a swap file inside the C: partition.

Your root partition is small and you have nearly 139GiB now unallocated on that drive. What were you hoping to do? Did you want to use the whole of that drive for Ubuntu?

---

### Post by salezd on 2013-12-27
Yes,I want to install another operating system in that unallocated space but I am not quite sure which one to choose.I want operating system that is similar to xp,fast and good for the beginners.I have a computer about 8 or 9 years old.Do you have any recommendations?

---

### Post by coffeecat on 2013-12-27
I think you've already got what you want in Lubuntu - fast and good for beginners. Perhaps others will have other suggestions.

---

### Post by salezd on 2013-12-27
Yes,it"s very fast and good for beginners.I like it so far.Thank you very much,you've been very kind and helpful and I learn something new.

---

### Post by newb85 on 2013-12-28
If you continue using Lubuntu, it is not unlikely that you will eventually find that 8GB is a bit small.  This will depend, of course, on how you use it, but it looks like you have plenty of unallocated space right now.  If you're going to install something else, now would be a really good time to expand your extended partition and the root partition for Lubuntu.  Boot from the installation media you used to install Lubuntu.  (If you're going to install another Linux, the installation media for that should work, too.)  Open Gparted.  Make sure the /root partition and the /swap partition are both unmounted.  Then it should allow you to proceed.

---

### Post by monkeybrain20122 on 2013-12-28
> **newb85 said:**
> If you continue using Lubuntu, it is not unlikely that you will eventually find that 8GB is a bit small.  This will depend, of course, on how you use it, but it looks like you have plenty of unallocated space right now.  If you're going to install something else, now would be a really good time to expand your extended partition and the root partition for Lubuntu.  Boot from the installation media you used to install Lubuntu.  (If you're going to install another Linux, the installation media for that should work, too.)  Open Gparted.  Make sure the /root partition and the /swap partition are both unmounted.  Then it should allow you to proceed.

I don't know about that. It is tricky to expand the root partition to the left side. Since the whole things is only 8 G I would suggest just delete it, do a repartition and reinstall it with separate / and /home (plus swap of course)

---

### Post by newb85 on 2013-12-28
You're right, moving the / partition is risky.  Let's scrap that idea.


8GB is indeed small, but it doesn't mean the OP doesn't have a good deal of time invested in configuring things to their liking.  Perhaps we could suggest a more conservative approach.  For example, couldn't the OP add another Ext partition to the left of the / partition, and then move their /home directory there, using it as their /home partition?

---

### Post by salezd on 2013-12-30
I am sorry you need to be more precise because I am new in Linux and I don"t know all the terms you talking about.What do the if I want to install one more Linux beside the one I already have.I want to install it in that unallocated space,but do I need to create one more partition to install it or what?And what to do with the root partition,should I leave it just the way it is?Can you explain me on the example of screenshot of Gparted that I post it.

---

