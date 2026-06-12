---
title: "question about svn use"
date: 2009-05-24
forum: Programming Talk
---

### Post by nbv4 on 2009-05-24
I have a django project that I work on on my home computer. I decided to set of a SVN repository on my webspace so I can more easily make backups.

I have everything set up, and the repository is woeking fine. When I go to [http://svn.example.com](http://svn.example.com) I see "/ - Revision 1: /", and then the files of my project.

What I don't understand is exactly how this is all supposed to work. Do I continue development from the directory I project is in now, or am I supposed to make a new one, then use "svn co http://svn...."? Or am I supposed to do this stuff from within the svn directory on my webspace via SSH? All the tutorials seem to skip this kind of thing...

---

### Post by geirha on 2009-05-24
First you import it. ```
svn import your-project/ http://svn.example.com/trunk
```

[http://svnbook.red-bean.com/en/1.4/svn-book.html#svn.tour.importing](http://svnbook.red-bean.com/en/1.4/svn-book.html#svn.tour.importing)

Then you check out a copy:
```
mv your-project/ your-project.old/
svn co http://www.example.com/trunk your-project
```

And start editing.

---

