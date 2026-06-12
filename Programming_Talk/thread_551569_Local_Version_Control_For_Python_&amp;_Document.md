---
title: "Local Version Control For Python &amp; Document"
date: 2007-09-15
forum: Programming Talk
---

### Post by zero-9376 on 2007-09-15
Hi,
I have just started with programming python as a part of my thesis, thismay eventually lead to am part time job too. I am trying to find a version control system that i can use to keep track of the changes I make, mostly because at the moment im getting carried away and forgetting to make new versions (version 4 was ~150 lines version 5 ~400) as python is so much easier/productive than anything ive used before.
I only want to use this on local files/folders in my home directory, also I would like it to automatically create a new 'version' every time i save the file. (not entirely sure this is the default behaviour)

Finally I would like to find something that I can use easily from within gnome, i tried timevault but it doesnt show changes for me so its a non-starter (or i just cant work it). I dont want to have to use the terminal to save changes, i was thinking perhaps something that uses connect to server?

One last thing, I would also like to save my main thesis/project document in this way, although at the moment Im forced to use Office which saves in binary format i think (2003), so i know i wouldnt be able to look at differences but it would still be good for backups. If this works it means no more messing with autosave etc. in word / writer when i can eventually change to that.

Thanks for any suggestions

---

### Post by pmasiar on 2007-09-15
> **zero-9376 said:**
> I am trying to find a version control system 

Your university IT department might provide version control, but it might be something obsolete like CVS. Subversion is much better, it is deliberate replacement of CVS. You can install it locally (synaptic + reads docs), on a server provided your friendly sysdmin, or use public code repositories (if your code is supposed to be public later).

> as python is so much easier/productive than anything ive used before.

Glad to hear that - it matches my experience too! :-)

> I would like it to automatically create a new 'version' every time i save the file. (not entirely sure this is the default behaviour)

None of current OSes has this handy feature AFAIK - last time I used it it was on [http://en.wikipedia.org/wiki/RSX-11](http://en.wikipedia.org/wiki/RSX-11)

> Finally I would like to find something that I can use easily from within gnome, 

[http://pysvn.tigris.org/](http://pysvn.tigris.org/) - WorkBench - for subversion (SVN)

> One last thing, I would also like to save my main thesis/project document in this way,

you can save versions of any text file

---

### Post by zero-9376 on 2007-09-15
thanks for the reply, i actually had a look at local subversion + snv-workbench but it seems overly complicated, i was actaully chasing something with nautilus integration but i dont think ill have any luck, kde has kdesvn which would probably do the trick but i dont really want to use kde. on a brighter note i had another look at time machine starting with a fresh empty folder and it appears to be working, although it doesnt tell me that a file was deleted which would be nice. im just a little concerned with trusting the program with my thesis data considering its alpha still.

---

### Post by dwblas on 2007-09-15
> (I'm) just a little concerned with trusting the program with my thesis data considering its alpha still.Then you should write a simple Python program to copy the files to a backup dir and name them appropriately with a unique ID.  Then use cron to run the program daily or whenever.  We must definitely consider the "sleep at night" factor.  In today's world disk is cheap, so we want to keep as many copies as necessary so we can sleep well at night.  I did a search for a "simple subversion" about a year ago with no luck except for kdesvn.  I'm subscribed to this thread, so please post back if you find any good candidates.

---

### Post by zero-9376 on 2007-09-15
I am going to try out timevault for the time being, although there was another app linked to the timevault thread that you may be interested in, it was a nice wrapper for subversion that looked very simple, the author has stopped working on it for the time being though, but it seemed like a great idea.

I was going to look at writing a script (in bash probably as I'm still new to python) which would periodically check md5sums for files and if changed copy them to backup folder with timestamp appended to name, but then I found timevault and it has this functionality (although inotify is obviously better than polling/md5) and already has a GUI. There are a few things i would like to see added, like a snapshot now button that allowed me to add a description with the snapshot. Maybe I can help out once I'm more proficient.

Grammar is better this time ;)

---

### Post by winch on 2007-09-15
I know some poeple that use [Git](http://git.or.cz/). As it's a distributed version control system you don't need a server. Just enter a few commands and you have a repository.

Commiting automatically is something you perhaps don't want. You will end up with a massive number of revisions with no commit messages. This will make it hard to find a previous revision.

---

### Post by nanotube on 2007-09-15
you should consider "bzr".
i use it to keep version control of some latex docs on my local system.
using it is as simple as:

to initialize a repo, run the following in the dir you wish to keep track of:
```
bzr init
```

to add files
```
bzr add <filename>
```

to commit changes
```
bzr commit <filename>
```

and of course, "man bzr" or hit the web for more info. :)

edit: btw, bzr is available in the ubuntu repos, so installation is easy. :)

---

### Post by zero-9376 on 2007-09-16
looks like if i want to use a 'proper' VCS ill have to be a bit more disciplined with commiting the changes, this is why i like timevault because i dont have to do anything special jus save the work and if its changed within the time period it records the change and i have a backup of the old work. it would be nice though to have the ability to add a snapshot when i want with a comment which i guess these other solutions allow. for the moment im going to create a changelog, just a text file with the date/time so that i can add  a comment to what should be a particular version.

---

### Post by HermanAB on 2007-09-16
There are many different free version control systems to choose from.  The trick is to know when to use which one.  The simplest system is RCS, which is good for use by one or two people, but best for only one person.

CVS is good for groups of people and works fine up to about 20 users.  

Subversion is good for any size groups, but really shines in large groups where CVS becomes a burden.

Git is good for Linux kernel development and probably not all that good for anything else, since it is custom made to solve Linus' problem.

If you are working alone, then I suggest using RCS, since it is hyper simple: [http://aeronetworks.ca/rcs-howto.html](http://aeronetworks.ca/rcs-howto.html) and doesn't use a server client model at all.  No configuration is required, it just works.  It is so simple, that I think that you should try it first before bothering with anything else.

Cheers,

H.

---

### Post by nanotube on 2007-09-16
> **zero-9376 said:**
> looks like if i want to use a 'proper' VCS ill have to be a bit more disciplined with commiting the changes, this is why i like timevault because i dont have to do anything special jus save the work and if its changed within the time period it records the change and i have a backup of the old work. it would be nice though to have the ability to add a snapshot when i want with a comment which i guess these other solutions allow. for the moment im going to create a changelog, just a text file with the date/time so that i can add  a comment to what should be a particular version.

you know, you only have to do a bzr init and bzr add once. then every time you change a file, you just do a bzr commit, and it lets you enter a changelog and stuff. it seems easier than manually creating a changelog with dates and whatnot. 
give it a try. :)

although yes, automatic revision control like timevault is even better for some purposes.

---

### Post by zero-9376 on 2007-09-16
bzr doesnt really fit exactly with what i want to do because if i cant remember to make a new version every so often it is equally unlikely that ill remember to do the commit.

rcs looks very promising I wonder if there is a nice frontend (like that pevo project)- this would be ideal for single files or maybe small projects, an automated check/snapshot based on time and whether the file has changed (just like timevault) which maybe adds a default description based on the date/time/size of the change and then the ability to explicitly create a snapshot and add description.

---

