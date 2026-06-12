---
title: "Root only has 46 k or meg, What do I need to clear some space?"
date: 2012-03-11
forum: New to Ubuntu
---

### Post by mal1958 on 2012-03-11
Keep getting that message of root having only so much space left and it says that I should remove some programs.  To get some space back on root, what should I remove?  And how?

  I cannot find the root directory in the disk program that comes up when I click on the investigate button.  I am wondering if it is the extra kernals that are there.  In the Grub message it shows 5 or six of them for 10.04.  Is this the possible cause?  If so, how can I clear the out dated kernals and keep only the two newest?  I hope that you can help me, anybody.

---

### Post by sudodus on 2012-03-11
This tool is good in order to clean your system
```
sudo apt-get install ubuntu-tweak
```
But if it is too crowded, maybe you need to delete something manually to create space for it. It there something, that you know you can remove (or move to another partition or drive). Maybe some application program, that is easy to reinstall afterwards.

---

### Post by Elfy on 2012-03-11
Having extra kernels will add to the situation - but I'd not say it was the cause, you'll likely be able to gain enough space to boot properly by removing them. 

Boot into recovery mode (unless you are in a desktop) and then run a root terminal from there.

Run

```
sudo apt-get autoclean
```

first, that will remove any out of date packages in the cache.

If you find it removes a lot that might be sufficient to allow a normal boot, if not

```
dpkg -l linux-image* |grep ii
```

will list installed kernels

```
apt-get remove *name of package*
```

Make sure you don't remove the newer ones :)

Once you have got into a normal desktop

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

If you are running the desktop - justs earch in synaptic for linux-image and remove old ones

---

### Post by mal1958 on 2012-03-11
> **sudodus said:**
> This tool is good in order to clean your system
```
sudo apt-get install ubuntu-tweak
```
But if it is too crowded, maybe you need to delete something manually to create space for it. It there something, that you know you can remove (or move to another partition or drive). Maybe some application program, that is easy to reinstall afterwards.

Tryed the code you gave, and got a message that it couldn't find the package ubuntu-tweak.

---

### Post by sudodus on 2012-03-11
> **mal1958 said:**
> Tryed the code you gave, and got a message that it couldn't find the package ubuntu-tweak.
Sorry, I forgot that you need to add a repository:
```
sudo add-apt-repository ppa:tualatrix/ppa
```

---

### Post by westie457 on 2012-03-11
Hi, obvious (silly) question. Has the 'Trash' been emptied?

---

### Post by yetiman64 on 2012-03-11
As well as autoclean that forestpiskie suggests OP, you may want to use "sudo apt-get clean" (removes all downloaded package files from /var/cache/apt/archives, not just the unused ones) this will free up even more space, especially on an older install. If you wish, navigate to /var/cache/apt/archives in nautilus and visually check for yourself before running the clean command.

Also I would suggest you check root's trash with,
```
sudo ls -la /root/.local/share/Trash/files
``` If there are any files at all in here, you can delete them with,
```
sudo rm -r /root/.local/share/Trash/*
```This will remove all subfolders and files in root's trash, don't worry about this as next time root files are sent to trash the subfolders will be automatically regenerated.

At this stage OP I would advise against adding anything, considering you are already running out of space, however once you find the excess and get rid of it, utilities such as "Tweak" may be very useful to you.

Hope this helps, cheers.

---

### Post by ajgreeny on 2012-03-11
Can we  also see the output from command ```
df -h
``` run in terminal which will show the sizes of partitions on your machine, and their %age usage.

---

### Post by oldos2er on 2012-03-11
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by mal1958 on 2012-03-11
> **westie457 said:**
> Hi, obvious (silly) question. Has the 'Trash' been emptied?

;) That was the first thing I did, Just in  Case..

> **yetiman64 said:**
> As well as autoclean that forestpiskie suggests OP, you may want to use "sudo apt-get clean" (removes all downloaded package files from /var/cache/apt/archives, not just the unused ones) this will free up even more space, especially on an older install. If you wish, navigate to /var/cache/apt/archives in nautilus and visually check for yourself before running the clean command.

Hope this helps, cheers.[COLOR="Red"]<snip:  For brevity>[/COLOR]

The Clean code you suggested did the trick.  I checked the root cache and saw that is was nearly packed, so I did what you suggested, as well as removing 5 of the 7 kernal images, and got back a huge chunk of space.  The message is gone.  My thanks to you all for your suggestions and help.

---

