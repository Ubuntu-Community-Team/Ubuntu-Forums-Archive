---
title: "Where is my trash can?"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by User_1 on 2013-10-30
Hello all, 

I'm basically at or below the beginners level on Ubuntu.  I'm just not catching the bug on doing the switch over.  Believe me, I'd like to, but haven't gotten the bug yet.  I installed Lubuntu on my netbook and have devoted the whole disc, 64GB to the install.  Well I tried to do the OS upgrade today and it reported back that there's isn't enough space on the drive to do the install.  It stated I should empty the trash.  The thing is that they only thing I really did on this netbook was do the install, do updates and some surfing.  And that surfing was VERY minimal as I can't really do anything on it!  I was barely able to play youtube videos on it!  Forget about playing downloaded movies.  This I think is because I don't have Flash installed.  

So I need to find out where my trash can is so I can empty it and install Flash so I can watch movies downloaded.  The absents of Flash is what I think I need.  I don't really have a clue.  I thought I would have an operating computer after installing the OS.  That doesn't seem to be the case. 

Any help is greatly appreciated.

---

### Post by sudodus on 2013-10-30
Hello User_1

I think something is wrong. You should not have filled your 64 GB yet. Anyway, the trashcan is visible from the ***file browser*** 'pcmanfm'.

Install flash for ***Firefox*** with this terminal window command.

```
 sudo apt-get install flashplugin-installer
```

---

### Post by warp99 on 2013-10-30
You can clean out the old archive and cached files in apt-get. Those tend to take up some space.

```
sudo apt-get clean autoclean
```

After this operation check your disk space

```
df -h
```

If you like you can download Chrome from Google which has a built in flash player.

[https://www.google.com/intl/en/chrome/browser/?brand=CHMO#eula](https://www.google.com/intl/en/chrome/browser/?brand=CHMO#eula)

Just remember to remove any Chromium packages you may have installed first.

```
sudo apt-get remove chromium*
```

---

### Post by Bucky Ball on 2013-10-30
Forget the bonus points Flash fix on this thread. It confuses things asking two (totally unrelated) support questions on one thread and consequently diminishes your chances of getting help with either. For future reference: one thread a support question. Makes things easier for everyone. There's plenty of room here.

You also might like to do some research on both of these issues as, particularly with Flash installation, there is a lot of info already in existence ...

[https://duckduckgo.com/?q=install+flash+ubuntu](https://duckduckgo.com/?q=install+flash+ubuntu)

Easy to find by Sudodus seems to have filled in the dots for you. I have edited the title of the thread to reflect ONE issue and made it more descriptive to increase your chances of getting help. Good luck.

PS: It would help if you included which release you are using ... 12.04? 13.10? What? Also, sounds to me like you are attempting to upgrade from one release to another rather than doing a regular update/upgrade of you system. Please explain what exactly you are doing? A single installation does not fill 64Gb. Period.

---

### Post by Impavidus on 2013-10-31
For Flash, read sudodus's post. To recover your disk space, try some cleanup and **df -h**, as suggested by warp99. It may be that you installed in multiple partitions, with a boot partition already filling up. Also, try running the following commands:
```
du --max-depth=2 --human-readable /var/log | sort -h | tail
du --max-depth=2 --human-readable ~ | sort -h | tail
```Copy-paste them to your terminal. They will take some time to run. They will tell us whether you have any oversized files in the most likely places where they can occur, like overflowing log files.

For additional info on recovering lost disk space, read this: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by User_1 on 2013-11-09
I've try each and everyone of the suggestions.  Personally I thought the procedures went fairly rapidly.  So I'm not even sure they worked.  I tried doing an upgrade tonight and got the same message as before.  Hard drive does not have enough room to do the upgrade.  The upgrade is to 13.10.

Any other suggestions?

---

### Post by monkeybrain20122 on 2013-11-09
How did you install lubuntu? Please post the outputs of df -h. There is something wrong with your setup.

BTW, in pcmanfm (under preferences?) there is an option to just delete without going to the Trash can. I never understand the use of Trash Can, if I want to delete something I want it gone!

---

### Post by vasa1 on 2013-11-09
As suggested, why don't you start a thread purely about your hard drive not having enough space?

---

