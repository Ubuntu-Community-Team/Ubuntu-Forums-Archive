---
title: "Uninstalling programs"
date: 2018-06-06
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-06
how difficult or easy is it to remove the various apps that you do not need/want/like/use?  thank you.  ex.  the amazon app and the notes app and some media apps?

---

### Post by rsteinmetz70112 on 2018-06-06
It's usually pretty easy all you need to do is identify the package name and run "apt remove <package-name>" You might then also want to run "apt autoremove" and "apt autoclean"

---

### Post by oldfred on 2018-06-06
Often best not to uninstall, much if anything.

Some apps have multiple dependencies or are required.
Users that uninstall something simple like python, unusually end of having to totally reinstall and restore from backups.
And some other apps may uninstall the entire desktop and all its dependencies. 

You do have good backups? That is the first thing you need to do.

---

### Post by bodhin2 on 2018-06-06
removed apps i do not need or use or like - not python etc.....thanks!

---

### Post by oldos2er on 2018-06-06
Changed thread title to better reflect the question.

Use your favorite package manager front-end to add or remove programs: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by poorguy on 2018-06-07
When you installed Ubuntu 18.04 did you do a full install or minimal install.

I usually do the minimal install and that way only have the minimal software that is necessary at install.

After I update I install the software I want using Synaptic Package Manager and then other software as needed.

I've found removing software that is installed with the install can create some issues as it may also remove dependencies that other software uses.


I use these commands and have not had any problems.


sudo apt remove [COLOR=#ff0000]package name
[/COLOR]
sudo apt purge [COLOR=#ff0000]package name[/COLOR]

sudo apt autoremove

---

### Post by bodhin2 on 2018-06-07
i already did it and so far all is well - knock on woooooooood

---

### Post by deadflowr on 2018-06-07
> **bodhin2 said:**
> removed apps i do not need or use or like - not python etc.....thanks!

You need python.
Or rather the system needs python.

that a side: 
The amazon app should be part of the ubuntu-web-launchers package.
It's marked as a recommend of the ubuntu-desktop package, so it should be okay to remove.
(recommended packages are optional, as oppose to something that is required, like a dependency.)

Hint:
If it is unknown what will happen when you try to remove a package you can run the remove with a simulate flag like
```
sudo apt purge -s ubuntu-web-launchers
```
this runs the command but doesn't actually do it, but will leave the output of what would happen if it did run.
the -s means simulate, in case it wasn't clear.

---

### Post by bodhin2 on 2018-06-07
so removing firefox or to do or rhythmbox or calendar or whatever is going to break my system.... i kind of doubt it....   a lot of thegnome stuff i left due to to me it seems relevant.  i am not a geek but have run a number of distros and DE's to know about adding and deleting some of the stuff that is junk to me to keep a more lighter system as needed.

not being a wise guy.  just do not believe that some of what i trashed was not a big deal.

---

### Post by poorguy on 2018-06-07
> **deadflowr said:**
> 
Hint:
If it is unknown what will happen when you try to remove a package you can run the remove with a simulate flag like
```
sudo apt purge -s package name
```
this runs the command but doesn't actually do it, but will leave the output of what would happen if it did run.
the -s means simulate, in case it wasn't clear.

OK If I understand this, then you are saying it will show every related package to be removed if I chose to actually remove the software I'm wanting to remove.

Is this correct.

---

### Post by deadflowr on 2018-06-07
> so removing firefox or to do or rhythmbox or calendar or whatever is going to break my system.
neither firefox nor rythmnbox are dependencies of the desktop.
But the calendar partially is.
The calendar app isn't. (what you find looking in the menu)
But the calendar in the panel is a dependency.

---

### Post by bodhin2 on 2018-06-07
thank you.

---

### Post by deadflowr on 2018-06-07
> **poorguy said:**
> OK If I understand this, then you are saying it will show every related package to be removed if I chose to actually remove the software I'm wanting to remove.

Is this correct.

Yes, but only as related to command being run.
It won't show any packages that would be marked for autoremove.

Not sure if that adds confusion or clarity.

---

### Post by poorguy on 2018-06-07
> **deadflowr said:**
> Yes, but only as related to command being run.
It won't show any packages that would be marked for autoremove.

Not sure if that adds confusion or clarity.

Nope no confusion at all.

I did a test run for different software to see the output and it does what you explained.

***autoremove ***in my experience has always displayed exactly what was going to be removed prior to ***Y / N ***choice.



Thanks deadflower that's useful information I can add to my*** "******Linux How TO Do Guide".***


Thanks

---

### Post by danthonyd on 2018-06-08
It's super easy. Just go to the Software Center, find your program and click Remove.

---

