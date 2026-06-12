---
title: "How do I copy a package from the official repositories to a PPA?"
date: 2010-07-14
forum: Programming Talk
---

### Post by Ibidem on 2010-07-14
Background:
I'm trying to build a PPA with the old gtk1.2 applications and themes in it. 
So far, I've added [https://launchpad.net/~adamkoczur/+archive/gtk1.2](https://launchpad.net/~adamkoczur/+archive/gtk1.2) to my own system, added "deb-src ..." lines to sources.list, and then used apt-get source --compile to build what I wanted.
This has worked so well that I think most gtk1.2 stuff would easily build if the old source packages were copied into a PPA.

Problem:
I would like to copy  source packages over from the Universe repository (Dapper, Hardy, Jaunty) so that they will build for Lucid.  
I have read [https://help.launchpad.net/Packaging/PPA/Copying](https://help.launchpad.net/Packaging/PPA/Copying) , and it is exactly what I want to do.  However, I cannot find a similar method for copying packages from the official repositories.

I tried a few searches and reading through the forums, but have found no information.

Ibidem

---

### Post by Bachstelze on 2010-07-14
Download the source package with [font=monospace]apt-get source[/font] and upload it to the PPA as usual?

---

### Post by youngflower on 2010-07-14
Sorry, I cannot help you. 
Wish you solve the problem as soon as quickly.

---

### Post by nvteighen on 2010-07-14
> **youngflower said:**
> Sorry, I cannot help you. 
Wish you solve the problem as soon as quickly.

(Thinking on one of [Grice's Conversational Maxims]("http://en.wikipedia.org/wiki/Conversational_maxims#Maxim_of_Quantity")...)

I just can't think of any complexity on what Bachstelze said... which is kinda the obvious thing to do, isn't it?

---

### Post by Ibidem on 2010-07-17
Well, thanks everyone.  
I have not uploaded to a PPA before, so I wasn't quite sure how to do it.

Now XMMS has uploaded, and I'll see about some other things:
manedit
gtkedit
danpei
and a few more packages.

Here's my PPA: [https://launchpad.net/~ibid-ag/+archive/oldgtk1]("https://launchpad.net/%7Eibid-ag/+archive/oldgtk1")
(ppa:ibid-ag/oldgtk1)


Overview of my method:
```

#export PVT_KEY (your gpg key), $PACKAGE, & $PPA first

sudo vi /etc/apt/sources.list
#Add old repositories, deb-src only
sudo apt-get update
cd 
mkdir src
cd src
sudo apt-get build-dep $PACKAGE
apt-get source $PACKAGE                      #DO NOT COMPILE!
cd $PACKAGE*
debuild -S -s? -k$PVT_KEY                    #s? is sa|sd
cd ..
dput $PPA $PACKAGE*.source.changes

```

Ibidem

---

### Post by Ibidem on 2010-07-17
OK, not quite working that way--packages get rejected.
What works:
dch +i --force-distribution lucid 'Bump for the PPA'                   #Whatever you want in the changelog; must change version
debuild -S -sa -k$PVT_KEY                                                 #For whatever reason, it seems to work better this way; may not be  needed.

---

