---
title: "[SOLVED] Its always Windows that gives me problems"
date: 2007-12-21
forum: Pennsylvania Team - US
---

### Post by Sabar on 2007-12-21
Hia guys. well tonight I am starting the reformatting and general clean up of my Alien. 

I have been running a duel boot computer for almost a year now and I can honestly say I have been real happy with Ubuntu. In fact I even got my hands on an old dell just so I could run a totally Linux system. 

Unfortunately I have to admit on my main computer I have to duel boot even though I only ever go to windows on very rare occasions.

Now here is my problem. 

Last time I reformatted I did just as I was told to do. put in windows followed by Ubuntu.

Everything went great until I noticed that windows didn't see my second hard drive. ( which in windows speak was always D:) 

Ubuntu of course worked perfect.

Now here I am upgrading to Gutsy and I figured I would try to fix windows by reformatting. I have two drives C and D. how ever now D is called H 

the only options I have on my resource CD are to delete partition and install can I delete partition of H to make it D again? any ideas how to fix this? 

If my ramble is making no sence please let me know thank you

Sabar

---

### Post by lamalex on 2007-12-21
You probably need to install the ext2fs drivers for windows. Do a google search, that might do the trick.

---

### Post by Ceemee on 2007-12-22
In windows*, you should be able to use the Computer Management to re-assign the drive letter in windows.

(I'm assuming since your saying you have the H: drive, you just prefer it to be D: )

Control Panel >> Adminstrative Tools >> Computer Management

Once this is open, you should be able to click on the "Storage >> Disk Management" in the tree view to the left, then right click on the disk, and there should be an option to re-assign the drive letter.

This is of course assuming you just want to change the drive letter assignment...

However if your looking to see your Linux Partition in windows, Iamalex is correct, you will need to install drivers to be able to read your Linux Partition.

* - You didnt specify which windows version you where using, I did this using Windows XP, I dont have access to Vista since I refuse to pay that amount of money for what I veiw as an inferior product compared to both windows XP and Ubuntu (7.04 / 7.10)

---

### Post by Sabar on 2007-12-22
Well I got the problem fixed. I hope.

What I ended up doing was going to disk management, rename disk was not an option but delete was. so I ended up deleting it there.

Then I placed my resource Cd into the drive and deleted that partition. repartitioned the whole drive ( which then came up as D ) 

Got back on windows then and the drive was actually listed under my computer so I tried to open it. I then got an error that the drive need formatted well I let it format my drive and now everything seems good. 

you know I have never had this kind of problems putting Ubuntu on my computer

thanks for the responces every one
Sabar

---

