---
title: "Setting up CVS"
date: 2006-06-02
forum: Programming Talk
---

### Post by brickbat on 2006-06-02
Hi,

I've installed CVS.

I want to use it to keep track of different versions of websites I hope to develop.

I want everything in my home directory for easy backup.

I have setup apache to use ~/www as my document root.

I created a repo at ~/cvsrepo in my home directory.  I checked it.  Its there and it has a CVSROOT directory in it.

when I type CVSROOT=~/cvsrepo then export CVSROOT and echo CVSROOT I get CVSROOT as a reply instead of ~/cvsrepo

I tried it with sudo thinking perhaps it was a permissions thing but it said command not found (I replaced ~ with /home/brickbat/

---

### Post by hod139 on 2006-06-02
Try 
```
echo $CVSROOT
```
You need to prepend the environement variable with a $.

---

### Post by brickbat on 2006-06-03
Ah-ha! Thankyou. I didn't know that.  So why don't you need the $ with the "export CVSROOT"?

Works like a charm now

I have just imported my first project...A blank index.html and a directory!

---

### Post by daneel_olivaw on 2006-06-03
The '$' before a variable produces an expansion of the environment variable, is you write
```
Var="helow"
export $Var
```

it's like you write
```
export "helow"
```

which makes no sense to bash as it expects a variable name after export.

Cheers :)

---

### Post by brickbat on 2006-06-03
I see.  Thank you.

---

