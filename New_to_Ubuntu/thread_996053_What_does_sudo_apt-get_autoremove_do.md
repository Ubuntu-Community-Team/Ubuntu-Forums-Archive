---
title: "What does sudo apt-get autoremove do?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by dawiba on 2008-11-28
Title says it all.

I saw this in another post and assume it gets rid of junk.

I couldn't find it on linuxcommand.org.

Sorry for the basic nature of the question :oops:

---

### Post by PriceChild on 2008-11-28
From ```
man apt-get
```...>        autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.

---

### Post by Michael.Godawski on 2008-11-28
Have a look here:

[LIST]
[*][http://ubuntuforums.org/showthread.php?t=377542](http://ubuntuforums.org/showthread.php?t=377542)
[*][http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)
[/LIST]

 This command removes packages that were installed by other packages and are no longer needed.

---

### Post by cmnorton on 2008-11-28
I would not call it junk. It removes packages no longer needed. If you search just the Ubuntu forums, you'll see a lot of commentary on this. Before running this command, I suggest backing up your package area.

---

### Post by cariboo on 2008-11-28
From man apt-get
>  autoremove is used to remove packages that were automatically installed to satisfy dependencies for some package and that are no more needed.

If you want more info on a command check the man pages eg:

```
man apt-get
```

Jim

---

### Post by blackened on 2008-11-28
If you remove an application apt-get autoremove will remove the dependencies that were installed with that application and are no longer used by anything else on the system.

Edit:
Wow, lot of people paying attention today. :)

---

### Post by silkstone on 2008-11-28
If you'd like to free up drive space, a useful and safe command is...

sudo apt-get clean

That removes the aptitude cache in /var/cache/apt/archives

You'd be amazed how much is in there! You don't need to keep it, and the only drawback is that the packages would have to be downloaded again if you wanted to reinstall them.

---

### Post by mc4man on 2008-11-28
I would take the "that are no more needed." not so literally if your running 8.10 and happen to do some compiling of sources.

APT was patched to mark all packages installed with 'apt-get build-deb' as automatically installed which then includes them immediately in 'autoremove'. (and renders using aptitude useless

There's an option to prevent this but as of yet can't see how to apply.

---

### Post by dawiba on 2008-11-28
Thanks everyone, I've got the idea!

---

### Post by Godzeye on 2010-07-11
can sudo apt-get autoremove be undone without reinstalling the packages u  think u want to keep.

---

### Post by CharlesA on 2010-07-11
No.

Should have made a new thead instead of resing out two years old.

---

