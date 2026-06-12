---
title: "On a clean re-install folders/directories dup names?"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2013-06-16
I made a clean re-installation of Ubuntu Precise Pangolin ver. 12.04 LTS. I used the "Custom" install to preserve my /sda5 or /home directory (or folder).

My username is "mark". The clean install shows, in the file manager Thunar, my username home folder with a house icon. It is unpopulated with the contents of my former /home or it's partition: /sda5 (which hold my files from the previous OS install.)

Does the System default application (package) "Backup" restore those files that I had backed up to the /home? What I'm trying to understand here is a few moments before posting this post, I tried to use "Backup" to restore the /home. After calling (or executing) "Backup", it ran, looking for a backup set. It found the most recent from June 6th, 2013 and offered to restore those files. I clicked the radio button "Continue", and the restore started, ran a while and quit, saying there wasn't enough storage space. That's incorrect. 

mark@Lexington:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
**/dev/sda3     18G   16G  1.3G  93%** /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           805M  968K  804M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  2.4M  2.0G   1% /run/shm
/dev/sdb1    299G  183G  116G  62% /media/TV
**/dev/sda5    342G   86G  239G  27%** /media/36cdd55c-9079-4455-8627-c3b8bfda3a45

The backup set is approximately 80 gig, as is the pre-reinstall size of my /home. Also problematic is the usage of /sda3, my boot partiton. After attempting a restore "Backup" has placed the /sda5 files or objects in /sda3. 

How can I safely remove the objects that "Backup" misplaced? Can "Backup" actually restore files to the proper location(s) in /sda5 and why was the former backup program "Déjà Dup" renamed: "Backup". That is such a common name that I cannot find a solution to my problem on the 'net and have to resort to taking UbuntuForum Member's time. Imagine using a "Tag" of backup, it returns way too much and makes the end user sift through too much spurious information.

Thanks for any response, whatsoever.

---

### Post by steeldriver on 2013-06-16
It looks like you preserved the contents of sda5, but did not actually select to mount it as the home partition in the new filesystem - so it went ahead and created a new (empty) home dir in / (i.e. on sda3)

Your old home on sda5 appears to be automounting in /media - have you navigated into that dir and checked for your old home files?

I don't fully understand what you did after that but likely the restored home files went into the new home which is why / (i.e. sda3) filled up

---

### Post by Mark_in_Hollywood on 2013-06-16
> **steeldriver said:**
> It looks like you preserved the contents of sda5, but did not actually select to mount it as the home partition in the new filesystem - so it went ahead and created a new (empty) home dir in / (i.e. on sda3) [COLOR="#FF0000"]At no point in time during the re-installation did the process stop, say: "Hey! I found your work in /sda5 (which is called /home) and do you want to mount it?" I haven't had to do a clean install for some years now. This failure of mine is an accident.[/COLOR]

Your old home on sda5 appears to be automounting in /media - have you navigated into that dir and checked for your old home files? [COLOR="#FF0000"]Yes, /media shows the /home objects.[/COLOR]

I don't fully understand what you did after that but likely the restored home files went into the new home which is why / (i.e. sda3) filled up

**[COLOR="#FF0000"]Why is there a /home on /sda3?[/COLOR]**. For inexperienced users, such as myself this is quite confusing and frustrating. The default package named: "Backup" ask me if I wanted the restore to put objects where they had come from. To me this meant, if the backup sees a folder or directory named: Genealogy, it finds /sda5 (or /home) and puts that it this way: /home/mark/Geanalogy in the partition /sda5.

Why is "Backup" not restoring to the original locations? And again, how do I know what files I can safely remove from the /home in /sda3 so as to not harm the brand new re-installation?

---

### Post by MidnightGrey on 2013-06-16
Hi Mark,

I am trying to interpret your post, let me see if i have this correct.
You have an old install of xubuntu in **sda5** which you've kept.
You created/formated a new partition **sda3** (of 18 Gb) which you've put on a fresh install of xubuntu.

**[COLOR=#FF0000]Why is there a /home on /sda3?[/COLOR]**
However, you did not create a seperate partition for **home**, so the install defaulted to creating home in your install partition (sda3).
Therefore, when DejaDup attempted to restore your 80Gb backup in home (located in sda3, consisting of 18Gb) it ran into the space issue.

[B][COLOR=#FF0000]Why is there a 2nd /home on /sda5?
[/COLOR][/B]Because you left your original install intact and did not delete it, this is essentially your old-home. The new install no longer recognises it as your HOME so it mearly acts as a normal folder now.

**[COLOR=#FF0000]Why was home in sda5 before and sda3 now?[/COLOR]**
Your original xubuntu install I believe was in **sda5**, assuming you did not assign a seperate partition for **home**, it would have defaulted home in sda5. Does this answer your question as to why home was previously in sda5 and is now located in sda3?

[COLOR=#ff0000]**Why is "Backup" not restoring to the original locations?**[/COLOR]
In fact DejaDup is attempting to restore to the original location. you backed up your Home folder previously, and in attempting to restore your home folder it tried to move everything to the newly located home in sda3. Imaging it as moving house, your mailing address used to be /sda3, and then you sent all your household items to storage, you since changed mailing address to sda5 and told the storage company to move everything to your (new) house, but your new house isn't big enough to store all your items.

Hope that helps.

---

### Post by MidnightGrey on 2013-06-16
Now regarding how to fix your home:

Firstly, the current partition of your home folder is too small to restore your 80Gb home backup, so you will have to point it to another partition. Once that is fixed, you can try DejaDup backup restore again.

---

### Post by Elfy on 2013-06-17
First things first - can we check to see that your new install is actually set up to use sda5 as /home

Give us the contents of /etc/fstab here

---

### Post by Mark_in_Hollywood on 2013-06-22
I apologize for the delay in my response. Immediately after my OP, the wifi modem router died and I have been unable to get online for a few days. Since I first posted, I had to do a clean install due to the mess I made. As the clean install made the purpose of this post unnecessary, this post is no longer in need of further review by the Linux-Ubuntu Community.

---

