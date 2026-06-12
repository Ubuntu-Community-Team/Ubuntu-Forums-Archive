---
title: "Help a git n00b grok git"
date: 2011-09-03
forum: Programming Talk
---

### Post by skullmunky on 2011-09-03
I'm working on a small project with 3 developers, and we thought we'd give git a try since it's so popular and cool.  It's driving me nuts and I'm 100% sure it's just because I don't understand it, despite reading the man pages and every Beginner's Guide to Git that I can find.  Perhaps I'm too steeped in Subversion to get it, but whatever it is I need help and deadlines loom! :D  

We're using the free hosting on ProjectLocker for the hosting.  Each of us uses a different OS (Ubuntu, OSX, and Windwos), so we're using the regular git client on Linux, Git-Gui on Windows, and GitX on OSX.  

The fundamental problem we're having is basic workflow: 

1. Alan edits a file
2. Alan commits changes:
```

git commit -m 'i edited this file'
git push

```
3. Betty wants to see Alan's changes
```

git pull origin master

```

right?

But: sometimes this works.  Other times, Alan's edits never appear in the Trac browser, so apparently 'push' never did anything, or it pushed them into some other mysterious place.

Sometimes Alan's edits DO show up in the repository, but when Betty pulls, they aren't downloaded, and git says the branch is already up to date. 

We're working very asynchronously, rarely at the same time, and on pretty well delineated parts of the project so barely even touch each other's files.

There's got to be some basic thing we're doing wrong, I'm sure of it.  

It also doesn't help that Git-Gui seems kind of unfinished and the menu commands are not named the same as the underlying git commands.  Meanwhile GitX shows us beautiful visualizations of branches but doesn't seem to get or push files reliably either.  

Heeeeelp!  I want to understand git!  

EDIT:

oh dear, I'm just digging myself deeper ... 

```

$ git branch
* (no branch)
  master

```
```

git checkout master
previous HEAD position was 0f84292... Added sounds (Bubbles8.py)
switched to branch master

```

Oh Nos!  A bunch of my files have suddenly disappeared! (Bubbles9.py, Bubbles10.py, two folders of sounds and graphics ... )

So I must have somehow ended up on another branch, which is why my changes weren't updating everyone else's branches ... but now that branch has vanished, how do I get those files back???!

---

### Post by JDShu on 2011-09-03
It sounds like you're treating git like a centralized version control system. I think it's possible to do this, but it really isn't how you're supposed to use it. Check out the link to see how git works conceptually.
[URL="http://www.eecs.harvard.edu/%7Ecduan/technical/git/"]
http://www.eecs.harvard.edu/~cduan/technical/git/[/URL]

---

