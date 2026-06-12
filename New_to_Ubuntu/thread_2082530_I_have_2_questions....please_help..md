---
title: "I have 2 questions....please help."
date: 2012-11-09
forum: New to Ubuntu
---

### Post by SweetGAPeach on 2012-11-09
I am having several issues.  I am unsure if I should ask both questions here or ask two separate questions, so I guess I'll start with both questions.  I'm sure someone will correct me.

1.  When I update my system, click restart, and attempt to log on I get the following error messages on reboot:
can't read file
-or-
hd0
out of disk
grub rescue
-or-
can't find kernal
************What does this mean?


2.  My Java updates are not working.  I am restricted from loading site that require Java.  I have upgraded manually as well as performed the system prompted updates.  How can I fix this problem?

I have no clue what I am doing and playing around with it myself.....probably made things worse!:frown::frown:

Thanks for any help.

---

### Post by lykwydchykyn on 2012-11-09
I take it the system boots in spite of the error you're seeing?

---

### Post by SweetGAPeach on 2012-11-09
It does eventually.  I have to hard reset like 10 times, and then come in under an older version of Linux.  I can't access the current version at all.  Haven't been able to for nearly 3 months now.

---

### Post by dannyboy79 on 2012-11-09
if the / folder containing your linux install is full, you won't be able to log into it. If I were you, I would boot to a live cd or usb stick, then mount the partition and remove some files. probably your trash is full or you have files within the Downloads folder.

---

### Post by SweetGAPeach on 2012-11-09
Thank you.  I have no clue how to perform that tasks you described.  Well clearing the downloads work?  I'll try that first.  Thanks again.

---

### Post by lykwydchykyn on 2012-11-09
Based on what I can tell from your posts, your hard drive is probably bad, or your partition with the current Ubuntu is full.

I would recommend booting to the live cd and running a bad blocks check in a terminal with this command:

```

sudo badblocks -v /dev/sda

```

If that doesn't find any errors, maybe try checking the partitions to see if they're full.  Boot to whatever linux install you can, run these commands, and post the output here:

```

sudo fdisk -l
df -lh

```

---

### Post by SweetGAPeach on 2012-11-09
Thank you.  I have tried the first code to search for errors.  It is going veryyyyyyyyyyyy slow, so as soon as the results load...I will post.  Thanks again!

---

### Post by SweetGAPeach on 2012-11-09
Ok, after trying the first option, the system indicated there were no bad sectors.

Next I entered the code:  ```
 sudo fdisk  -l
```

And got the following response:
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007671e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30157   242233344   83  Linux
/dev/sda2           30157       30402     1963009    5  Extended
/dev/sda5           30157       30402     1963008   82  Linux swap / Solaris
```

And then I entered the second part of the code: ```
df - lh
```

And got this:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             228G   13G  204G   6% /
none                  933M  676K  933M   1% /dev
none                  943M  356K  942M   1% /dev/shm
none                  943M  220K  943M   1% /var/run
none                  943M     0  943M   0% /var/loc

```
Please advise...thanks for your help.

---

### Post by Elfy on 2012-11-09
please do not bump your thread as often lest it be closed for 24 hours ;)

this issue is of no more importance than any others, volunteers will answer as they wish to ;)

---

### Post by BertN45 on 2012-11-09
You have strange looking errors, it could be caused by hardware or a corrupted installation.
Your disk seems OK, to be sure start the "Disk Utility" from the dash or menu and select the disk and check whether the light "SMART Status" is green and whether it says that the disk is OK.

Run the memory test from the boot menu and check if your memory is OK, it will run for some time (an hour or so) and it will loop so watch the test numbers. By the way do you have enough memory for the OS?

If both are OK, your latest linux installation has probably been corrupted, the easiest solution is to save the data you want to keep to DVD or USB stick/disk and to re-install the system from scratch and allowing it to use the whole disk.

If the disk is NOK, save the data you want to keep and get a new disk.

If the memory is NOK, remove the memory cards/strips one by one to find and remove the faulty one or get new memory. The memory error could disappear by cleaning the contacts and re-inserting the cards, if the problem has been dust or some grease.

---

### Post by SweetGAPeach on 2012-11-09
> **Elfy said:**
> please do not bump your thread as often lest it be closed for 24 hours ;)

this issue is of no more importance than any others, volunteers will answer as they wish to ;)


I don't know what you mean by bump, but I would like for you to know that I do not feel my post is more important than others.  I was simply responding to the person that asked me to try something.  Don't worry I will not come here anymore.  Please delete my account.  ....assuming is tacky...you should ask my intentions before wrongfully assuming them.

Thank you,

---

### Post by dannyboy79 on 2012-11-10
> **SweetGAPeach said:**
> I don't know what you mean by bump, but I would like for you to know that I do not feel my post is more important than others.  I was simply responding to the person that asked me to try something.  Don't worry I will not come here anymore.  Please delete my account.  ....assuming is tacky...you should ask my intentions before wrongfully assuming them.

Thank you,
I don't know why that mod said you were bumping your thread, he was wrong! I hope you stick around as this community is very helpful.

The errors you have are very weird, when booting can you hit shift so you are presented with the grub boot menu and see if you can boot to an earlier kernel?

It's also possible you're grub install got hosed and grub can't find your kernel. You could give Boot Repair a try, it's here:
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
and how to use it here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You may just want to back up your important stuff and do a fresh install if you don't have too many modifications done from a new install. It's your choice obviously.

BUT please stick around, don't be intimidated by one persons actions that do NOT represent Ubuntu community as a whole.

---

### Post by lykwydchykyn on 2012-11-10
When you say you end up on an "older version of Ubuntu", what does that mean?  An older kernel, an older desktop environment?   What are you seeing that leads you to that conclusion?

I'm curious because you only seem to have one partition, so it's not as if you could have two parallel installs on separate partitions.

---

