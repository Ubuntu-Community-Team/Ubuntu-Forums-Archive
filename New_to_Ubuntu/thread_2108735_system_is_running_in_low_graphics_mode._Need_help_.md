---
title: "system is running in low graphics mode. Need help deleting files"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by fishman35 on 2013-01-25
Hello all. I think I have read just about every forum I can and none of the suggestions have worked. I cannot reinstall Unbuntu because it took me forever to get DRBL working correctly. Here are a couple of things I need help with:

[LIST]
[*]No network connection to get computer janitor or autoclean. We are behind a proxy and cannot get out, unleass there is a way to set the proxy from the terminal.
[*]I have check my space and my hard drive is full, but I cannot find what is taking up all of the space. I am back on this now, but I remember trying to delete the PROC cache from another forum post and I get "access denied". I am logged into my standard login, which may not have root capabilty. I have ran sudo to no avail.
[/LIST]Is there any way to clear files from the CTRL+ALT+F1 terminal? How to I get full rooth access? I had deleted image files that were in gigibytes from the /home/partimag directory, but the drive still shows full. 
 
Please help! Thanks so much for any assistance.

---

### Post by SlugSlug on 2013-01-25
Start with emptying Trash

```
sudo find / -name ".Trash*" -exec rm -rf {} \;
```

---

### Post by fishman35 on 2013-01-25
I emptied the trash. Looks like only 986MB. I created the log, put in a USB key and it mounts as sdb. How do I copy the file over to the key? 
 
Somewhere I have GB's of data that is either cached or not truly deleted.

---

### Post by SlugSlug on 2013-01-25
post output of

```
du / -sch
```

and ```
df -h
```

---

### Post by fishman35 on 2013-01-25
So I typed that, and it gives a list. How do I get it to the key to post here? Remember, I am a beginner. I think the Proc directory is the one that is killing me, but I cannot delete anything. Access denied. I run sudo. Nogo. I try su and it states authentication failed.

---

### Post by mcduck on 2013-01-25
> **fishman35 said:**
> So I typed that, and it gives a list. How do I get it to the key to post here? Remember, I am a beginner. I think the Proc directory is the one that is killing me, but I cannot delete anything. Access denied. I run sudo. Nogo. I try su and it states authentication failed.
/proc is a virtual filesystem which doesn't exist on your disk, so there's no need to worry about it. It doesn't use any disk space at all.

(In Linux everything is a file, including every system process and everything that's going on in the computer. And those files appear in /proc. So it's definitely not a place where you'd want to delete anything even if you could)

Anyway, if you want to free some space you could try running "*sudo apt-get clean*" to remove the package management's cached packages. After that it's usually just a question of taking a look at things stored in user's own home directories...

---

### Post by fishman35 on 2013-01-25
So I mounted the drive into another working Ubuntu system. It states 117.6 of 120.00 GB used on that drive. I can use Nautilus and access the drive, but none of the folders add up to 117.6GB total. It is like there are images that I deleted, but they are not really gone.
 
Once again, no access to internet to download utilities, and I already emptied the trash from the terminal. There is no way an install of Ubuntu is 120GB.

---

### Post by mcduck on 2013-01-25
You don't need to install anything, "sudo apt-get clean" will work as long as you have apt-get installed (which you will, on any Ubuntu system).

...and same goes for the *du* and *df* commands. And if you aren't able to copy the outputs here, that's fine, just take a  look yourself to see where the space is used. If it's anything inside /home, you can safely remove it yourself, and for everything else you should ask for more instructions (as deleting wrong things from any system directory might break your system).

---

### Post by fishman35 on 2013-01-25
I ran "sudo apt-get clean" both in the terminal when this hard drive was in the original system that would not boot, and now as a mounted drive through the terminal. Still shows 117GB used. I deleted everything in Home, still 117GB used. I checked every folder size, still does not add up to 117GB used. 
 
 
 
Could this be that it is an SSD drive and needs TRIM?

---

### Post by mcduck on 2013-01-25
Shouldn't have any effect on *file system level* which is where most tools will report the available space.

I'd still recommend taking a second look with the "du / -sch" command SlugSlug suggested, it should tell you exactly where the space is being used. (And if you want, you can then cd into that directory, run "du -sch" to check the sizes of it's contents, find the largest, cd there & repeat again until you've found the problem.)

---

### Post by fishman35 on 2013-01-25
I did the "du / -sch" from a terminal window.So many pages fly by I cannot see all of it, nor can I scroll up to the top. It only goes so far. I used the du -sch in each directory. Nothing showing that is even close to 117GB.
 
I hate to use the W word, but in Windows, you have things like the _hiberfil.sys that can take up GB's of space, as well as System Restore. Does Ubuntu have any kind of caching system that would fill the drive like that? 
 
I sent at least 80GB of Clonezilla images to the Trash. Do you think they are REALLY deleted, becaused this would have more than solved the problem I would think. Maybe just send to trash does not delete it? I emptied the trash through the terminal. 
 
Thanks for all of your help guys.

---

