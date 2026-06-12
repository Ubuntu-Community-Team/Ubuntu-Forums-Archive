---
title: "fresh install with keeping my files"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by akkad on 2008-05-08
i have upgraded to 8.04 but the system is somehow unstable after the upgrade so am thinking to format and reinstall 8.04, so am wondering if there is away to make a fresh new installation but keep my user folder (/home/MyUser) without any changes, is this possible with ubuntu ??

---

### Post by warbread on 2008-05-08
It's a good idea to keep your /home directory on a different partition for just such an occasion.  It's important to note that you will still need to do some reconfiguring, but your personal files and desktop theme(s) will be intact.

As for your current situation, you could just copy them all to a seperate hard drive or a DVD and copy the files back when you've installed.

---

### Post by akkad on 2008-05-08
is it possible to set the home folder into another partition other than the filesystem partition ???

---

### Post by hyper_ch on 2008-05-08
yes it is

---

### Post by warbread on 2008-05-08
It is, and is quite easy in fact.  First, go into live boot and then open up gparted (System -> Administration -> gParted).  It will take a minute or so (depending on the size of your filesystem) to scan your hard drive and then present you with options in the upper right hand corner (it's a pull down menu).  If you only have one hard drive, then you don't need to worry about it.  Resize your root ('/') partition to as small as you can make it, and then create a new partition from the free space, however big you want your /home partition to be.  I suggest making it fairly big.  I've never needed more than 15 gigs for a root partition, the rest has been my /home directory (and swap, of course).  Once you've got that situation how to like, press 'Apply' to finalize.  Then see the following link for instructions on how to do the actual move:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by hyper_ch on 2008-05-08
[http://www.psychocats.net](http://www.psychocats.net) --> good tutorials for basic stuff like that...

I used to have a seperate home... but I gave up on it... I didn't see much benefit for myself with it.

---

### Post by crashie on 2008-05-08
There's no need to create a separate partition for /home. You should be able to install Hardy and it will delete all system files but keep your files in /home.

---

### Post by sujoy on 2008-05-08
even then a separate /home is good in case you need to distro hop, or say in case of a bad upgrade. it keeps my data much more secure.

---

### Post by akkad on 2008-05-08
ok guys am 100% thankful for ur replies, but i still need more :) , actually i know my following questions are basics where i can search for some tutorials but actually i need suggestion from users experience, i need ur experience with the following:

i used to let ubuntu installation wizard to partion my disk where it produces the swap and the root partitions, i was happy with that cuz i thought that if i wanted to install new ubuntu version i will not need to format as there is upgrade option, but as i tried the upgrade i realized that my system is not in a good health after the upgrade, so i decided to make fresh installation every time for new versions, and am thinking to create a partition for my data (music, docs, ...) and leave the /home directory (themes, config, ...) at the root partiton.

so what is the best partioning u suggest me?? and from ur experience plz take a look at following:
- do u think i will need just 3 partitions one for root one for swap and one for data?? if so what is the suggested size for the swap and for the root(it depends, but what is the possible maximum ).

- i believe that in ubuntu everything is a file even configurations (unlike windows and registry keys, correct me if there is a misunderstand in this) so is that mean that in such a way i can backup my installed programs and then restore them after new ubuntu installation??  if so do i need to create a partion for programs or it is a must to install the packages on the root partition???

- also is there away to backup/restore the system settings??

sorry for the long message but i hate not to know all linux capabilities and with ur experience i am still experiencing, thnx anyway ...

---

### Post by warbread on 2008-05-08
> **akkad said:**
> 

so what is the best partioning u suggest me?? and from ur experience plz take a look at following:
- do u think i will need just 3 partitions one for root one for swap and one for data?? if so what is the suggested size for the swap and for the root(it depends, but what is the possible maximum ).


The exact numbers here depend on a lot.  It's normally suggested that for swap, you have twice as much partitioned as you have system RAM.  So, if you have 2 gigs of RAM, partition out 2 gigs of swap.  However, if you have 8 gigs of nice, fast RAM (squee!!), you probably don't need any swap space at all.  For /root, I partition out 12-15 gigs, depending on what I'm going to do.  If you have a big hard drive, go for 20.  Why not?  The rest, in my opinion, should be /home.

> 
- i believe that in ubuntu everything is a file even configurations (unlike windows and registry keys, correct me if there is a misunderstand in this) so is that mean that in such a way i can backup my installed programs and then restore them after new ubuntu installation??  if so do i need to create a partion for programs or it is a must to install the packages on the root partition???


The Linux filesystem does not make it convenient to back up individual programs.  However, since it is a multi-user system from the ground up, you will find that the configuration settings that you make while logged in as you (as opposed to root user, or your grandma's account, or whatever other accounts there are) are saved in your home directory.  Want to see them?  Go into terminal and while in your user's directory, type

```
:-$ ls -al 
```

Notice all those with a '.' in front of the name?  They are hidden directories and files.  You may recognize many of the names as programs you use.  For instance, there should be one named '.mozilla', which has any and all of your preferences, themes, history, bookmarks and settings in Mozilla prodcuts (like Firefox).  

Configurations stored in your /home folder in this way will restore.  This is why I like having a separate /home partition (though I guess Hardy now does not require this).  Most, if not all, of your settings will be saved as long as you keep your /home directory and mount it.  

> 

- also is there away to backup/restore the system settings??

sorry for the long message but i hate not to know all linux capabilities and with ur experience i am still experiencing, thnx anyway ...

Backing up and restoring system settings is harder, but if you can be more specific about what settings you want to keep, someone here can find the file you need to save.  Desktop and icon themes, as well as desktop backgrounds and sounds get saved in /home/****, so you shouldn't need to worry about that.

---

### Post by akkad on 2008-05-08
thnx warbread, u r da best, i think am gonna give a try to relocate /home directory into a new partition, so i'll try ur solution, but dont be that glad cuz once am stuck in some where then i'll be here requesting ur ubuntu beans, thnx ...

---

### Post by akkad on 2008-05-10
guys i created 3 partitions, one for root / with ext3 file system(primary), one for my data where the mount point is "/Data" also ext3 file system(logical), the last one is the swap(logical), now i can see that the Data partition appears under the root (as it is mounted there), does this means if later i wanted to format the root it will affect the Data partition ??

---

### Post by crgutierrez on 2008-08-17
I did upgrade to 8.04 but the new version does not recognize the previous 4 users. If I want to activate them the program tells me the directories are already in use...........how do I use the old user accounts that remianed in the /home directory???? pls help

---

