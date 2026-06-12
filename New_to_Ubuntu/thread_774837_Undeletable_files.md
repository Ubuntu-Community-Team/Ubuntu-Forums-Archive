---
title: "Undeletable files"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-04-29
Hi folks, 

I have a file (or rather, a directory) in my trashcan which won't delete... even when logged in as sudo su. I keep getting a permissions error. How do I get rid of it? 

-'Mage

---

### Post by eapache on 2008-04-29
So you're running ```
gksudo nautilus
``` and navigating to the trash and trying to delete it, and it gives an error? What is the exact message?

---

### Post by Sh@m@n on 2008-04-29
By the way, where is thrash locaded in hardy?
In nautilus, it's mounted as thrash:///

---

### Post by UnWarierMage224 on 2008-04-29
apache: 

This is odd. under gksudo nautilus, navigating to the trash, the directory isn't there. 
HOWEVER, in my login account's trashcan a directory still shows up, and the trashcan appears to have an item in it even though under gksudo no such item exists in the trash.. 

odditties...

---

### Post by ConMan318 on 2008-04-29
I always thought you had to add the -rf tag to force a removal of a directory. I've done it a few times, but I won't encourage that since screwing that up can cause major problems.  So **DON'T DO THAT**, I don't want to get into trouble for encouraging dangerous code.  Plus, I'm pretty sure there are other ways to remove directories; I am very new to Linux.

So I am curious as well as to how to remove directories without the danger of the -rf.

What is nautilus?

---

### Post by bilal.17 on 2008-04-29
location of trash ```
~/.local/share/Trash 
```

---

### Post by Barrucadu on 2008-04-29
> **bilal.17 said:**
> location of trash ```
~/.local/share/Trash 
```

In that case, a simple...
```
rm -rf ~/.local/share/Trash/*
```
...should remove it.

---

### Post by ajgreeny on 2008-04-29
I think the files you are looking for are probably in root's trash, which is File System or /root/.Trash.  Your user trash is in ~/.Trash, not ~/.local/share/Trash, in fact, I don't really know what goes in there.  My user Trash has some files in it but the folders in ~/.local/share/Trash (files and info) are both empty.

---

### Post by gug@fnal.gov on 2008-04-29
Hi,
   If you want to remove a directory and the contents in it, "rmdir -r" <directory-name>" usually works well. If I am removing files in a directory I use rm, if I want to remove a directory I tend use rmdir. The only real reason is it forces me to at least know I am removing a directory or not. 
   However, I would caution against using the "-f" flag in almost all situations. You can do a lot of damage that way by accidentally running that in the wrong area and files you thought were read-only also disappear. Even more of a risk is to run it under sudo. Here is an illustration of the type of trouble you can generate for yourself. There was a product at work that hidden deep inside had a line "rm -rf $PATH1/$PATH2". Someone decided to run the script after unsetting PATH1 in their environment. What they did not know is that under certain conditions PATH2 would not be set, and those conditions existed when he ran the script. Now that line above became "rm -rf /". On the plus side the user did not have root permissions, on the minus side he had permission to wipe out a very large storage array attached to the system. The script was started and he left, coming back hours later and seeing it was still running he killed it (around midnight). I learned this in the morning when I came in and saw my boss and several others huddled around a screen with long faces and asked why. 
   If you need to use the -f flag, try -i also which should prompt you for every file. If that is too tedious, make sure you absolutely know what you are doing and don't walk away. Just my opinion.

---

### Post by UnWarierMage224 on 2008-04-29
So wait I'm confused as to what I have to do... 
Post #4 of this thread... 

Thanks, 

-'Mage

EDIT: Nevermind. Fixed it.

---

