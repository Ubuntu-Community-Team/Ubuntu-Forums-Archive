---
title: "Need help in partitioning!"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Godsendkilla on 2008-07-10
now this is the story
I'm using windows XP SP2 and i want to duel boot with Ubuntu.
i have a empty partition in my harddisk I:\ it is about 20GB
can you please tell me in partitioning which file system should i choose in the menu?

(i saw a video in youtube and in it the person partitioned it as Ext 3 journaling filesystem, but when i select it thers a prob saying "no swap space" or something) ples help

---

### Post by DGortze380 on 2008-07-10
> **Godsendkilla said:**
> now this is the story
I'm using windows XP SP2 and i want to duel boot with Ubuntu.
i have a empty drive in my harddisk I:\ it is about 20GB
can you please tell me in partitioning which file system should i choose in the menu?

(i saw a video in youtube and in it the person partitioned it as Ext 3 journaling filesystem, but when i select it thers a prob saying "no swap space" or something) ples help

First, make sure you select the correct drive in the top right. Don't delete your Windows partition!
On the empty drive you need at least two partitions. One ext3 (for the root file system and your home directory), and one swap (at least 512mb... this acts like windows virtual memory). You can add another ext3 for your home directory if you like, this makes for easier backups.

---

### Post by kansasnoob on 2008-07-10
> i have a empty drive in my harddisk I:\ it is about 20GB
can you please tell me in partitioning which file system should i choose in the menu?

Short answer = "none". Seriously, if you're installing 8.04 Hardy Heron and you have a totally empty partition on the drive (I assume you have only one hard drive?) you can simply select "Guided - use the largest continuous free space" and the installer will take care of Swap and the whole works. I suggest no less than 10gb overall, nearly 20gb should be fine.

---

### Post by kansasnoob on 2008-07-10
> i have a empty drive in my harddisk I:\ it is about 20GB

This really should be clarified!

An empty drive or an empty partition?

You say "harddisk" so I assume you have one hard drive with a 20gb free partition?

---

### Post by Godsendkilla on 2008-07-10
> **DGortze380 said:**
> First, make sure you select the correct drive in the top right. Don't delete your Windows partition!
On the empty drive you need at least two partitions. One ext3 (for the root file system and your home directory), and one swap (at least 512mb... this acts like windows virtual memory). You can add another ext3 for your home directory if you like, this makes for easier backups.

Actually i have one harddisk and 5 partitions the one i'm going to install Ubuntu is I:\ so how do i make a ext3 and swap ???

---

### Post by Godsendkilla on 2008-07-10
> **kansasnoob said:**
> This really should be clarified!

An empty drive or an empty partition?

You say "harddisk" so I assume you have one hard drive with a 20gb free partition?

i mean empty partition sorry my bad!

---

### Post by kansasnoob on 2008-07-10
> Actually i have one harddisk and 5 partitions the one i'm going to install Ubuntu is I:\ so how do i make a ext3 and swap ???

If the 20gb space you speak of is the largest (or only) free space on the drive you can just use "Guided - use largest continuous free space" ......... if you're installing 8.04 Hardy.

Otherwise do just what  DGortze380 is saying. Hold on a minute and I'll try to find you the perfect tutorial.

Thanks for planning ahead! We wish more people would!!!

---

### Post by Godsendkilla on 2008-07-10
> **kansasnoob said:**
> If the 20gb space you speak of is the largest (or only) free space on the drive you can just use "Guided - use largest continuous free space" ......... if you're installing 8.04 Hardy.

Otherwise do just what  DGortze380 is saying. Hold on a minute and I'll try to find you the perfect tutorial.

Thanks for planning ahead! We wish more people would!!!

thanks for reply 
still have the problem  :confused:

---

### Post by kansasnoob on 2008-07-10
Go here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Down about 1/3 of the way you'll see: "NEW: Choose one of three different Ubuntu 'Desktop CD' graphical installations"

Check out all three.

If you're planning on using the Alternate CD for some reason it's discussed prior to that.

Planning is everything!

---

### Post by Godsendkilla on 2008-07-10
> **kansasnoob said:**
> Go here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Down about 1/3 of the way you'll see: "NEW: Choose one of three different Ubuntu 'Desktop CD' graphical installations"

Check out all three.

If you're planning on using the Alternate CD for some reason it's discussed prior to that.

Planning is everything!

thanks i'll check it out and if i had a problem i'll post here!

---

### Post by kansasnoob on 2008-07-10
> thanks i'll check it out and if i had a problem i'll post here!

Please do! Many here are willing to help, just be patient, doing it right will make your Ubuntu experience totally pleasant!

Anytime you're in doubt about anything ask a new question!

One thing that would help me, if you've already been able to navigate the Live CD and have internet thru the Live CD, is a screenshot of Gparted (aka partition editor). Like here's mine:

[ATTACH]77170[/ATTACH]

(Very, very simple right now, I just built this and I store nearly all data on external drives)

You can take a screenshot by going to Accessories > Take Screenshot.

Many others can deal with it by seeing text output following CLI commands, but I'm a gui guy! Nothing wrong with either!

Ubuntu is all about choices! You can have it your way!

---

