---
title: "Subversion checkout within existing working copy of another repository"
date: 2008-05-15
forum: Programming Talk
---

### Post by cdean on 2008-05-15
I'm working on a web site and have a desire to manage WordPress through Subversion within the working copy of this site.

Essentially, my site repo looks like this:

/tags
/branch
/trunk
--/images
--/styles
--/logos
--/blog

I want to checkout WordPress into /trunk/blog, then add it to my repo so it's checked in with the rest of the site.

I tested the dumb way of doing this by creating a test repo like my real one and checking out WordPress. When I tried to add it to my repo, svn said it was already under version control. This is true, because it is under control of the wordpress repo, but it is not under control of *my* repo, which is where I want it to be.

Any suggestions on how I might go about doing this? I've very new to svn and can't seem to find a document describing a solution to my problem.

---

### Post by WW on 2008-05-15
I'm not sure this is exactly what you want, but you can use the **svn export** command to put an unversioned copy of wordpress into /trunk/blog, and then use **svn add** to add it to your repository.

---

### Post by cdean on 2008-05-16
Hmm.

It seems that that would export the version, but it wouldn't allow me to simply do **svn sw [http://url/to/new/version/](http://url/to/new/version/)**. I wonder how well **svn export** works in copying over files in place.

I guess I'll play around with it a little tomorrow and see what I can find.

---

### Post by winch on 2008-05-16
Take a look at svn externals.

[http://svnbook.red-bean.com/en/1.0/ch07s03.html](http://svnbook.red-bean.com/en/1.0/ch07s03.html)

---

