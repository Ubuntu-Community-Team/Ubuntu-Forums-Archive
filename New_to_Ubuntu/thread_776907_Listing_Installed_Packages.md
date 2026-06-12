---
title: "Listing Installed Packages?"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Kissell on 2008-05-01
So, like any newbie, I had to play with the Synaptic Package Manager.  I've always installed programs I need from the CLI with apt-get, but every so often I browse the GUI package manager for things i may be interested in.  

What I've realized, is that I always assumed after I installed stuff I'd find and play with it later...  but it turns out most things aren't creating an icon.

Now, if I know what I installed, I can run it from a command line...  but there is so much in the package manager...  is there a way to have it display the things I've installed?  If not, I have no way of knowing what I've installed without going through and looking for green boxes in the GUI.

---

### Post by SunnyRabbiera on 2008-05-01
Well in synaptic you can go to the status button and look under "installed"
also if you need to you can also make synaptic tell you where things installed to by going up to "settings" then "preferences"
and click on the first box listed, it will give you details on each package.

---

### Post by Aelfric5578 on 2008-05-01
In the left hand panel of Synaptic, there is a selection box and several buttons.  If you click the Staus button and then in the selection box choose Installed, you will see all the packages currently installed on the system.

---

### Post by Kissell on 2008-05-01
I have 1668 packages in my list when I got to STATUS - INSTALLED.

It would be really nice if there were a column there in which I could sort the results by the timestamp of when they were installed...  

I installed the OS weeks ago on this machine, so the new stuff I don't really use yet but wanted to check out should be been the stuff installed in the past few days.

---

### Post by daimaru on 2008-05-01
```
dpkg -l |less
```or 
```
ls /usr/bin
```
or hit tabulator twice

---

### Post by MobiusNZ on 2008-05-01
Well, you can use dpkg to list all the installed packages on your system. check out dpkg's man page for more info on that (i'm not in my linux boot right now so i can't help there sorry).

But to be honest, thats just going to put out a hell of a lot of info that you'll struggle to work with (its probably easier to look through your synaptic lists - you can do all sorts of sorting and filtering there).

You can do tricky stuff with dpkg, like show all the stuff installed in the last x days, but you need to have pretty good knowledge of the command line...

---

### Post by agim on 2008-05-01
or, if you want to write it to a file, so you can browse at your leisure...

dpkg -l > installedPackages.txt

And this is one of my favorites: This will list each according to its size

dpkg-query -W --showformat='${Installed-Size} ${Package}\n' | sort -nr | less

---

### Post by agim on 2008-05-01
Of course, you could just open synaptic, and on the bottom left, there are a few buttons, click on Status, and then hit installed in the text box above :)

---

### Post by Kissell on 2008-05-01
I like that dpkg-query command, because space is limited on my laptop.  But when I uninstalled a program then ran it again, the program still showed up taking up as much space...  So this is off topic, but I added the Tag line, because that showed me that it really wasn't taking up 100MB, that Tag had changed from "Installed" to "Config Files".

> dpkg-query -W --showformat='${Installed-Size} ${Tag} ${Package}\n' | sort -nr | less

Still, what I originally meant to convey that I wanted, was a list sorted by date of installation.  I looked at the man pages on dpkg-query and dpkg and don't see how to do that.

---

### Post by daimaru on 2008-05-01
> **Kissell said:**
> So this is off topic, but I added the Tag line, because that showed me that it really wasn't taking up 100MB, that Tag had changed from "Installed" to "Config Files".
If you want to delete everything of a program (including config files) use the -purge option in apt-get | aptitude | "mark for complete removal" in synaptic

---

### Post by Kissell on 2008-05-01
Great..  except, now that I've removed it, it's too late to purge it from the command line without reinstalling it?

> apt-get remove evolution-common purge

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package evolution-common is not installed, so not removed
E: Couldn't find package purge


---

### Post by Monicker on 2008-05-01
> **Kissell said:**
> I like that dpkg-query command, because space is limited on my laptop.  But when I uninstalled a program then ran it again, the program still showed up taking up as much space...  So this is off topic, but I added the Tag line, because that showed me that it really wasn't taking up 100MB, that Tag had changed from "Installed" to "Config Files".



Still, what I originally meant to convey that I wanted, was a list sorted by date of installation.  I looked at the man pages on dpkg-query and dpkg and don't see how to do that.

So far I  have seen 2 different places where package information is kept, depending on whether you used synaptic or apt-get to install.

```

/root/.synaptic/log/
/var/log/apt/term.log
```


The formatting is not all that great, but it might be useful to look at those 2.

---

### Post by Kissell on 2008-05-01
Okay, awesome.

I originally had the issue enough times to ask, because this time I was looking through synaptic for a good on-screen keyboard program when I realized I didn't know where to start them after I'd installed them.

Those log files really got me what I was looking for.

> vi /root/.synaptic/log/2008-05-01.010158.log

> Commit Log for Thu May  1 01:01:58 2008
Installed the following packages:
gtkeyboard (1.1.7-5build1)
hotkeys (0.5.7.4-0.1)
libfakekey0 (0.1-1)
matchbox-keyboard (0.1+svn20070815-0ubuntu5)


Don't have the option to mark the threat as [SOLVED] though...  weird...

---

### Post by agim on 2008-05-01
Also, this is the form

sudo apt-get remove --purge <package name>

---

### Post by Kissell on 2008-05-01
Yeah, but it's not working...  maybe time for a new thread.

When I do the dpkg list it shows up with this name "evolution-common" which is the name I used with apt-get to remove it without the purge, and it still shows up in dpkg, but --purge won't completely remove it.

> sudo apt-get remove --purge evolution-common

Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package evolution-common is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by zvacet on 2008-05-01
To see list of all installed packages run in terminal

```
dpkg --get-selections > installed-software
```

and you will find text file in your home directory.

---

