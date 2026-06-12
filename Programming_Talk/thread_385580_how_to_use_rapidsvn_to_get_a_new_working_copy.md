---
title: "how to use rapidsvn to get a new working copy"
date: 2007-03-15
forum: Programming Talk
---

### Post by nephish on 2007-03-15
hello there all

i am using rapidsvn on an ubuntu machine at work and another ubuntu machine at home. i am writing some scripts and using svn to do my revisioning.
Its really handy, i get a copy in the morning at work, make sure its all updated, and when i get home, i basically do the same thing.

The problem is, when i get home, i destroy my working directory so that i can create a new bookmark and get the most recent copy of everything to work on. 

is there a way that i can just sync them up somehow so that whatever is the latest on the server will overwrite anything different on my computer at home ?

thanks for any tips

---

### Post by blanky on 2007-03-15
**EDIT**: Sorry, I'm pretty confused about your post. At home, did you simply **checkout** the revision? If so, can't you easily run an **svn update**?

Well, I think what you want is a crontab. Crontabs let you execute commands at a specified time. Keep in mind I'm no expert at this, and I just first recently created my first crontab myself. I created a crontab on my server so that my site automatically packages my game's media content every midnight after getting the latest revision of my game's Subversion repository. I suggest you read about crontabs, here are some links:

[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)
[http://wiki.dreamhost.com/index.php/Crontab](http://wiki.dreamhost.com/index.php/Crontab)

For example, you could write a script that updates your subversion checkout every midnight. To do this, you could create a file called **ctab** or something, and have this in it:

```

0 0 * * * /usr/bin/svn update /home/yourname/where/your/checkout/is

```

This will update your checkout and synchronize it with the one at your work (*Oops, I'm assuming that the one at your work is your central repository. If it isn't, you **do** commit changes when at work, right?*)

You could change it so that it's at different times, for more information on that, read more up on crontab and the links I gave you, it's pretty straightforward.

If you would rather run a bash script that did this and more, you could easily do it with:

```

0 0 * * * /bin/sh /home/yourname/path/to/script/nameofscript.sh

```

That will run the script every midnight.

---

### Post by nephish on 2007-03-15
ok, yes, my question was not clear enough,
i don't know exactly what update does. when i ran it before, i though it would update my working copy with the latest revision, but what it did was put all these little marks in my code of what changed here and there.
So, i am kinda needing to understand how to have two working copies, one at work, one here, where i can always get the most recent version where ever i am at. The last thing i do before leaving work is commiting any changes i have left at the end of the day, but when i get home, my working copy is 10 hours old ( and many changes old ) i need to get my copy at home to be the same as the copy at the end of the day from work. 

thanks

---

### Post by blanky on 2007-03-16
Okay, again, I'm no expert in this, but I have a good feeling that the marks you get are because there are having change conflicts. For example, say you have a text file, you check it out from work, and you modify it at home, say you add one extra word. Well, you don't commit, and you go back to work and add some more stuff, then get back home and run an update, there will most likely be a conflict. To avoid this, I think what you should do is commit after making changes on your home computer (*If you have permissions*). Then continue to do as you always have, when you get to work, you'll have the latest revision (***Again**, assuming that the repository is at work, or do you also checkout the subversion at work?*).

If you can't commit, don't have permissions, or whatever, then you'll probably want to look into conflicts, I think you can do something like merging, but I'm not that advanced in subversion, so I can't really tell you.

Hopefully that solves your problem. For more information, read the [Subversion Book]("http://svnbook.red-bean.com"), not the whole thing if you don't like, but the relevant parts.

---

### Post by pmasiar on 2007-03-16
> **nephish said:**
> i don't know exactly what update does. when i ran it before, i though it would update my working copy with the latest revision, but what it did was put all these little marks in my code of what changed here and there.

At work you make checkout. Make changes, and commit them to repository. At home, you make another checkout. Make changes, commit them. At work, you update working copy first thing in the morning to get your changes from home to your work copy. Before leaving for home, commit them. At home, update your home copy first to get changes you made at work. 

It is simple: first update (to get most recent changes from repository), make changes, and commit them.

---

