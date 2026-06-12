---
title: "GUI or CL tool to do compare/diff of remote/local folders"
date: 2007-11-13
forum: Programming Talk
---

### Post by pixelterra on 2007-11-13
Looking for an open source tool to compare local and remote folders. My favorite to date is Beyond Compare, which unfortunately doesn't run on linux (yet?).

Any suggestions

This is pretty crucial for my full switch to linux as I'm a web developer, and essentially do this all day long.

---

### Post by smartbei on 2007-11-13
What exactly do you want the program to compare?
I am not sure if you want the program you are looking for to compare the:
[list]
[*]filenames in the two directories, or
[*]file contents of similarly named files in the two directories, or
[*]size of the directories, etc.
[/list]

BTW - Checking the WINE AppDB; Beyond Compare was given a platinum rating on wine version 0.9.47. See [http://appdb.winehq.org/objectManager.php?sClass=version&iId=9611](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9611)

That is probably your best option.

---

### Post by pixelterra on 2007-11-13
I want the following info shown as nicely as possible (color):

[LIST]
[*]which files exist only locally
[*]which files exist only remotely
[*]which files that exist on L and R are exact copies
[*]which files that exist on L and R are different
[*]a diff/merge tool to reconcile different files
[/LIST]

I frequently am forced to work on sites where they insist that a staff member alter files on a shared host server (read:no version control). This helps me see what they've done and not overwrite.

---

### Post by smartbei on 2007-11-13
Hmmm...This is pretty simple to do using the command line, without the nice display.

Have you tried running Beyond Compare with Wine? As I said above, that is supposed to work (platinum rating means it works flawlessly), and you could have everything you want.

---

### Post by pixelterra on 2007-11-13
I checked out the wine post. I've never used Wine yet, perhaps this is a good oportunity.

Also, how would this be easy on the command line? If it is, i'll do it. 

Take a look at a screenshot from Beyond Compare: [http://www.scootersoftware.com/en/shot7w.png](http://www.scootersoftware.com/en/shot7w.png)

It seems like it wound't be easy from the CL. Would be nice though.

---

### Post by pmasiar on 2007-11-13
mc - midnight commander. It can do this, and much much more, for more than 25 years - in previous incarnation as beloved Norton Commander.

---

### Post by pixelterra on 2007-11-13
I thought I tried out MC a couple of years ago and it didn't do what I needed. Can't really remember though. It can really do local/remote compare and merge?

I'll check into that....

---

### Post by smartbei on 2007-11-13
pixelterra - When I said it would be easy to do on the commandline, I specifically added that that would be without the nice display.

It would not be too difficult to make a small comamnd-line program that merely checks two dirs and returns the differences between them - but this is obviously not as useful/neat as what Beyond Compare/Midnight Commander.

---

### Post by pmasiar on 2007-11-14
> **pixelterra said:**
> [MC] can really do local/remote compare and merge?
You can compare files and directories - MC is file manager after all. To merge changes in, you need different tool.

---

### Post by geirha on 2007-11-14
I don't know exactly what you need this for, but to me it sounds like you should use subversion for this task ...

---

### Post by RaySeys on 2008-01-25
What about Meld (apt-get install meld)  you will need to smbmount the remote server first though

---

