---
title: "Subversion help"
date: 2007-11-12
forum: Programming Talk
---

### Post by aquavitae on 2007-11-12
I've never used a vcs before so I don't really have any idea what I'm doing.  What I'm trying to do is to set up a project on google code.  I've created the project on the google code website and now I'm trying to add existing code to it using pysvn in eric4.  

Can anyone tell me how to do this?  I've tried experimenting with some of the menu options under 'project' but I'm not getting anywhere.

---

### Post by pmasiar on 2007-11-12
Not sure about Eric -  I use pysvn workbench client.
What you need to do is to "checkout" empty project into some directory, copy your files there, tell svn you want to track them, and commit them.

RedBeans has excellent book about using SVN, with good guide to everyday tasks.

---

### Post by geirha on 2007-11-12
I would highly recommend reading at least chapter two of the svn book at [http://svnbook.red-bean.com/](http://svnbook.red-bean.com/)

It should give you a basic understanding of subversion, and using any subversion client after that should be like a walk in the park.

---

### Post by aquavitae on 2007-11-13
Thanks for the replies.  I'll give the pysvn workbench a try.  I actually found the red-bean book through google a couple of hours after my post, I'm reading it right now.  Its really good!

---

### Post by melopsittacus on 2008-01-02
Hi!

I was checking out a very large project and as I had no time left, I closed the SVN client (I am using RapidSVN), so not everything got downloaded. 
Now I would like to download the remaining files but when I use the update command it aborts because the working copy is locked. I tried unlocking the working copy with ```
svn cleanup
```, but it says that a specific file is not under version control. 
I tried to delete this file, but it does not exist, so this must mean that it is registered in the .svn file of the local copy, but has not been downloaded yet.

Is there a way of downloading the remaining source code without having to wipe what I have already downloaded and starting over again?

---

