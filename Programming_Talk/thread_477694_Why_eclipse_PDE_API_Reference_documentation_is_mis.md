---
title: "Why eclipse PDE API Reference documentation is missing in 3.2.2-0ubuntu3"
date: 2007-06-18
forum: Programming Talk
---

### Post by codybuntu on 2007-06-18
I am working on some Eclipse plug-in development and decided to switch on Linux (Ubuntu). However after installing Eclipse noticed that "Plug-in Development Environment Guide" API Reference is not viewable using eclipse "Help Contents". Opened the org.eclipse.pde.doc.user_3.2.1.v20060816-0800.jar and noticed that folder /reference/api/ was empty. So to make sure I downloaded form eclipse.org  the same file org.eclipse.pde.doc.user_3.2.1.v20060816-0800.jar and  the folder was filled with files. After replacing the file file with the one from eclipse.org all the documentation was in place.

The same is with "Platform Plug-in Developer Guide" and "JDT Plug-in Developer Guide"

I was about to post this as a bug but could not access the "https://launchpad.net/distros/ubuntu/+bugs" looks like the site is down like the "https://help.ubuntu.com/".

So is this a bug or what? :D
Why the documentation was omitted?

---

### Post by mkro on 2007-10-28
Bumpetybump. This seems to be still a valid problem on Gutsy. The start screen of Eclipse gives among other things the option "Workbench basics - Learn about basic Eclipse workbench concepts", but selecting it gives an empty help window. Can't seem to find a separate "eclipse-docs" package either.

---

### Post by zeevb on 2008-03-01
Here is a workaround for this bug

[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/158461/comments/4](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/158461/comments/4)

Start Eclipse as root
sudo eclipse

Go to Help > Software Updates > Find and Install...

Select Search for new features to install and click Next

Select The Eclipse Project Updates and click Finish

Select Eclipse 3.2.2 > Eclipse Project SDK

And install

---

### Post by DocForbin on 2008-05-17
> **zeevb said:**
> Here is a workaround for this bug

[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/158461/comments/4](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/158461/comments/4)

Start Eclipse as root
sudo eclipse

Go to Help > Software Updates > Find and Install...

Select Search for new features to install and click Next

Select The Eclipse Project Updates and click Finish

Select Eclipse 3.2.2 > Eclipse Project SDK

And install

I get the following error trying this:

Eclipse Java Development Tools 3.2.1 performance patch (bug:159325) (1.0.0) requires feature "org.eclipse.jdt (3.2.1.r321_v20060905R4CM1Znkvre9wC-)".

---

