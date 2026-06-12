---
title: "setting up PYTHONDOCS env variable !!"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by kitcha on 2011-09-14
im a newbie to linux environment and hence have a doubt:  

I am at an early step in learning python where I want to set the PYTHONDOCS env.  variable properly so I can view things like help ('print') at the  interpreter prompt.

The problem is that the tutorial suggests this step (for Fedora):

     Code:
     $ env PYTHONDOCS=/usr/share/doc/python-docs-2.3.4/html/ python Python 2.3.4 (#1, Oct 26 2004, 16:42:40)... 
but, when I go to /usr/share/doc... there is not "python-docs"  folder for Python 2.7.1(im currently using ubuntu 11.04). I am wondering what folder I need to set the  environment variable to in order to gain said functionality.

can someone help out....thanks !!

---

### Post by gmargo on 2011-09-14
You need to install the **python2.7-doc** package, and then the proper path will be **/usr/share/doc/python2.7/html/**.

[http://packages.ubuntu.com/natty/python2.7-doc](http://packages.ubuntu.com/natty/python2.7-doc)

---

### Post by kitcha on 2011-09-17
thanks gmargo...cheers !! :)

---

