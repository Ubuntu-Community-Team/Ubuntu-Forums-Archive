---
title: "SVN: Only get the dir structure with svn checkout ?"
date: 2008-03-16
forum: Programming Talk
---

### Post by ekh on 2008-03-16
I have been using svn for a while with relatively small repositories.

Now I have a big repository, and an initial checkout take a looong time.

This is frustrating, as I would like to have a fast checkout of the directory structure only, and then pick and update the specific directory I need, so the files are downloaded from the repository for this sub dir only. It is also a matter of not wasting disk space for a lot of files you don't need right now.

It is possible to do today - if you know the names of the subdirectories, but I don't before I see the directory tree,

Is there a way to make a checkout of the directory structure only ?

---

### Post by supirman on 2008-03-16
You can specify --non-recursive to the checkout command, then it will only get the dir you directly requested.  From there, you could get the subdirs manually in the same fashion.

---

### Post by the_unforgiven on 2008-03-16
AFAIK, svn doesn't do what you expect.
However, there is ```
svn ls
``` that gives you listing of the directory structure - so you could checkout a particular directory manually (maybe with --non-recursive as specified by supirman).

For more info, do: ```
svn help ls
```

HTH ;)

---

### Post by ekh on 2008-03-16
Thanks for your fast replies :-)

I have used the command line with svn, but mostly I use RapidSVN.

I have just tried a combination of your advises.

svn co -N svn://server/rdir

Then the root directory rdir is created, but it only contains the .svn directory.

cd rdir
svn ls

then I get the subdirs.

svn co svn://server/rdir/b1

And I get all files in that directory seen with nautilus - but when I start RapidSVN and do

Bookmarks->Add existing working copy..

Then the subdir was shown as unversioned. I could only see the subdir, not its contents.

But then I found the solution next in the menu:

Bookmarks->Add existing Repository..

I made an extra bookmark and got the complete directory tree without the files in them (fast).

Now I can see the whole dir structure, but one problem solved a new shows up.

The update button is grey, so I can't update my subdir, as noted above its status is "unversioned", although it has just been checked  out with the "svn co" command.

Just for fun I tried to "add" the directory, and now RapidSVN complains it is alreadu under version control ( as expected ).

Is this an error, or have I missed something ?

---

### Post by ben.biddington on 2008-09-25
Hi, you can do this with an update like:

```
svn update --depth empty path/to/directory
```

and to get the list of all directories, try something like:

```
svn ls -R | tr -d '\15\32' | grep '/$'
```

<bb />

---

### Post by V-teq on 2009-08-09
I have used something like
```
svn ls | xargs svn up -N
```
to check-out svn directories (non-recursively) in current directory.

Afterwards, you should use ```
svn ls | xargs svn up
``` to check-out subdirectories recursively, because simple ```
svn up
``` command couldn't check-out it's subdirectories automatically at first.

---

