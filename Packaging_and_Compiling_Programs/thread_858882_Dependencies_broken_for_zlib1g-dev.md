---
title: "Dependencies broken for zlib1g-dev"
date: 2008-07-14
forum: Packaging and Compiling Programs
---

### Post by pmj005 on 2008-07-14
I am running gutsy 7.10 and my sources.list file does not refer to any non-gutsy repositories.

I need zlib.h to compile another software and so using Adept Manager I tried to install zlib1g-dev. I already had zlib1g installed previously.
After choosing "Request install", Adept manager shows "BREAK (install)"
In /usr/lib I have libz.so.1.2.3.3 (which is part of the package zlib1g) so that makes me think my zlib1g version is 1.2.3.3. Is there a more reliable way to check version of zlib1g library?

I ran
sudo apt-get install zlib1g-dev
and it gave this error :
The following packages have unmet dependencies:
  zlib1g-dev: Depends: zlib1g (= 1:1.2.3.3.dfsg-5ubuntu2) but 1:1.2.3.3.dfsg-7ubuntu1 is to be installed
E: Broken packages

What does this mean (-5ubuntu2 versus -7ubuntu1)? 
Can any of you help with this? If not, is there another way to get zlib.h and associated library so I can compile the package that needs zlib? 
Thanks

---

### Post by WW on 2008-07-14
You appear to have the version of zlib1g from hardy, not gutsy; take a look at [this search result](http://packages.ubuntu.com/search?keywords=zlib1&searchon=names&suite=all&section=all).  The hardy version of zlib1g ends with -7ubuntu1.

Did you previously have a hardy repository in sources.list?

---

### Post by pmj005 on 2008-07-14
Hey WW! 
You are absolutely right. I was originally on feisty. I probably hardy in my sources.list when I was trying to upgrade to hardy which did not work. Eventually, I changed everything to gutsy and did upgrade to gutsy. 

How do I undo this mess? I thought removing zlib1g may not be a good idea as many things depend on it.

---

### Post by WW on 2008-07-14
Sorry, I don't know much about fixing a mixed install like that. Try to remove zlib1g and see what happens.  Whatever tool you use to remove it, it will probably ask the equivalent of "Are you sure?" before actually doing it.  You may have to reinstall more than just zlib1g to get back to a pure gutsy installation.

---

