---
title: "Tried Edubuntu - how do I uninstall?"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by daytonageeks on 2008-09-07
Can I uninstall Edubuntu without disturbing or losing my Ubuntu Hardy?
Thanks and Blessings,
                     daytonageeks

---

### Post by tangibleorange on 2008-09-07
> **daytonageeks said:**
> Can I uninstall Edubuntu without disturbing or losing my Ubuntu Hardy?
Thanks and Blessings,
                     daytonageeks

do you mean you installed edubuntu alongside an existing ubuntu installation? if so, you should be able to use this command:

```
sudo aptitude remove edubuntu-desktop
```

---

### Post by egalvan on 2008-09-07
> **daytonageeks said:**
> Can I uninstall Edubuntu without disturbing or losing my Ubuntu Hardy?
Thanks and Blessings,
                     daytonageeks

*HOW* did you install Edubuntu?

That will tell us how to un-install

And why do you want to uninstall it?
Didn't like it?
Didn't work?
Not want you needed?

I'm asking because I am getting ready to install Edubuntu for a six-year-old girl, and her mother wants "educational" stuff on the computer.

---

### Post by daytonageeks on 2008-09-09
Installed edubuntu over an existing installation of hardy for purpose of testing it out for my purposes - I maintain computers for my church and the church school. edubuntu will be great for the school, but I'd rather have my old settings back for my personal computer.
Truth told, as far as I could see, the only changes it made to ubuntu hardy that you couldn't install yourself, manually, were graphics (but I may have overlooked something).
I do think it would be a great addition for kids and will use it in the school computers.
Thanks for the interest!
Blessings,
           daytonageeks

---

### Post by daytonageeks on 2008-09-10
> **tangibleorange said:**
> do you mean you installed edubuntu alongside an existing ubuntu installation? if so, you should be able to use this command:

```
sudo aptitude remove edubuntu-desktop
```

Thanks = did this and Ubuntu went down hard and fast with no way to retrieve. Lost years of bookmarks and mail addresses.
[SIZE="7"][SIZE="6"]MODERATOR??????[/SIZE][/SIZE]

---

### Post by starcannon on 2008-09-10
First, don't panic.

You have only removed a desktop environment, your /home/username directory is still there, and that is important because thats where your bookmarks and emails are located.

**Back up your system**, yeah I know its broken, but the good stuff is still there, and in case of further mishap, we want it to be able to be brought back from the grave. Use this post:
[http://ge.ubuntuforums.com/showpost.php?p=4521323&postcount=4](http://ge.ubuntuforums.com/showpost.php?p=4521323&postcount=4)

Okay now then **reinstall gnome:**
```
sudo apt-get install --reinstall ubuntu-desktop
```

This will be computer time consuming, in particular the backup will take time, but its the safest way to do anything computer related, backup, then move forward.

GL, and again, don't panic, breathe, relax, and know that all you've done is hosed your desktop manager, not your personal files, they are still there.

---

### Post by tangibleorange on 2008-09-11
yeah your files are still there. all i did was provide you with the command to remove your edubuntu desktop - that's what you wanted isn't it?

simply run the command provided above, or boot into a live CD and copy your files to an external HDD or something...

relax - your files are safe :)

---

### Post by daytonageeks on 2008-09-21
Nope, all was lost. No way to reach terminal. tried a live disk approach and files were corrupted throughout.
reinstalled.
spent hours.
upside, gained experience.
downside, lost a ton of data.

---

### Post by waspbr on 2008-09-21
don't you have a recovery boot option? you can reach a terminal from there

---

### Post by JadenRosen on 2009-01-06
For future reference using Symantic and clicking the Uninstall for the Edubuntu desktop, AND the install function for the Ubuntu Desktop is an immediate replacement and doesn't require Terminal...

Just so you all know for next time.

I know from personal experience that it works.

---

### Post by efexD on 2009-01-06
> **daytonageeks said:**
> Nope, all was lost. No way to reach terminal. tried a live disk approach and files were corrupted throughout.
reinstalled.
spent hours.
upside, gained experience.
downside, lost a ton of data.

From uninstalling a desktop environment?!

---

### Post by MrKlean on 2009-01-07
I'm wondering what ya did....unless you did a format/install....yer stuff should have been there.  I've done it with Kubuntu and didn't have a problem ; (

---

