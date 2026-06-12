---
title: "trying to install sunbird 0.8"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-04-30
Yes, I've searched the forums. Still haven't a clue. 

Tried the steps here: [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
... no luck. 

The tar.gz file is on my desktop. 

-'Mage

EDIT: Fixed.

---

### Post by jw5801 on 2008-05-08
> **UnWarierMage224 said:**
> Yes, I've searched the forums. Still haven't a clue. 

Tried the steps here: [http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)
... no luck. 

The tar.gz file is on my desktop. 

-'Mage

EDIT: Fixed.

Sunbird 0.8 is in the hardy repositories. ```
sudo apt-get install sunbird
```

---

### Post by hongleong on 2008-06-16
@jw5801 :

```
$ apt-cache policy sunbird
sunbird:
  Installed: (none)
  Candidate: 0.7+nobinonly-0ubuntu2
  Version table:
     0.7+nobinonly-0ubuntu2 0
        500 http://tw.archive.ubuntu.com hardy/universe Packages
```
The hardy repo has 0.7 instead of the latest 0.8. jw5801, do you know which repo has 0.8? Thanks.

---

### Post by jw5801 on 2008-06-16
Hmm... you are correct. I wouldn't have said that without a valid reason though. Perhaps they regressed? I had a look in hardy-proposed and it isn't there either. It is in the Intrepid repository though. Take a look [here](http://packages.ubuntu.com/intrepid/sunbird) and you should be able to get the .deb for it. I'm not sure if it'll install however, may be compiled against newer versions of some libraries.

**EDIT:** Yeah, you'll struggle to install the version in the Intrepid repositories without updating a lot of other things to their current unstable versions. Compiling it from the source would be a better option.

---

