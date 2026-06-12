---
title: "Deb Request: Ogre 1.25 for edgy"
date: 2007-03-29
forum: Programming Talk
---

### Post by lingnoi on 2007-03-29
I want to do some game programming on **edgy** in OGRE . The only version of Ogre3D is an out of date version. I can't compile it myself because its too much of a hassle.

Is there anyone who knows of a deb package available from anywhere? I am looking for version 1.25 but if there is the new release available I will take that. 

Thanks :)

---

### Post by denver on 2007-03-29
I dont know of any deb's for ogre...but if you're trying to compile it
```
apt-get build-dep ogre
```

might help. This will download all the lib's necesary for compilation. 

Good Luck!

---

### Post by lingnoi on 2007-04-01
If anyone has the time it would be extremely useful for me. :)

---

### Post by po0f on 2007-04-01
lingnoi,

I could be wrong, but this *isn't* a deb request forum.

It's really not that hard to compile your own library, just untar it and follow the directions in the README or INSTALL files.  You'll find that a lot of the people here will help you with any problems you may have getting Ogre installed.  :)

---

### Post by lingnoi on 2007-04-01
> I could be wrong, but this isn't a deb request forum.

Ok, I guess I will just wait till 7.04 is out and then start.. :(

---

### Post by WW on 2007-04-01
You could request a backport: [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

### Post by aprice2704 on 2007-04-09
I second that request!!!!!

I just spent 3 days trying to get Ogre installed. The packages on which Ogre depends, and Ogre itself, were quite nasty to get configured.  I have been mostly successful but it took way too much effort for most people I suspect and I still have a glXChooseFBConfig core dump to sort out -- hopefully with help from the Ogre folks.

Setting up kdevelop was not too bad, but only because of the instructions on the ogre site, it still required several manual tweaks.

This has been brutal and exasperating and I would strongly welcome anyone who might undertake package maintenance! I would be willing to help. 

The way to get 3D programs popular on Ubuntu is to make it make it easy to develop them. This is not easy.

Andy

---

### Post by lingnoi on 2007-04-16
I've pretty much given up on this and am just waiting for feisty to be released so I can upgrade and grab the deb package from there.

I do not feel great about this situation normally this community is a lot better then just "It's really not that hard to compile your own library". 

Yeah, right...

---

### Post by tribunal on 2007-04-27
I can help with OGRE
There is 1.2.5 for Feisty, but I need 1.4
And I can help with debs
But only for Feisty, cause I have Feisty
This community is not so bad :)

---

