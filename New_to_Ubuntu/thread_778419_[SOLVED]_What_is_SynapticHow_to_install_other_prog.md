---
title: "[SOLVED] What is Synaptic/How to install other programs?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by LillaEpsilon on 2008-05-02
How does the Synaptic Package manager work, and who decides what is in it? Can I add other packages to my own Synaptic package manager? 
How do I install programs which are not found there? 
Which are the different ways to do this?

Thank you!

---

### Post by Bubba64 on 2008-05-02
Here is a link to describe what synaptic is and does.
[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
You also have add remove in applications.

---

### Post by kpkeerthi on 2008-05-02
There is a good guide here [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) :)

---

### Post by iSplicer on 2008-05-02
Synaptic is as easy as it can get to use. Just start it using Administration -> Synaptic, search for the application you want to install, and then just simply, well install it! Everything is taken care for you.

---

### Post by rahulsharma on 2008-05-02
hey i won't be able to answer all your question but yeah a couple for sure i guess

In synaptic you have some package already available to you after the first install i believe the developer decides which package they should include.
When you do clean installation for the first time your ubuntu would be in basic form no extra effects and other stuff like compiz package you would have them in the synaptic but not installed it depends on you if you want them or not. Similarly it has lots of other stuff already available for which you don't have to make a search like codecs and other stuff

to use synaptic just open the synaptic and search for what you want and click apply and it will be installed.

Secondly if you need to install some software which is not in there then you can look for deb package online for the application if its there download it and double click it, it will get installed like exe's in windows another way to install debian package is using terminal "sudo apt-get install package.deb" or "sudo aptitude install package.deb". If its a different package like bin or something then you have to first change the mode using chmod command but as you seems to be newbie i would suggest look for tutorial before you use any command 

hope this helps a bit

---

### Post by PeterJS on 2008-05-02
> **LillaEpsilon said:**
> How does the Synaptic Package manager work
Synaptic is one of may front ends to [APT (the Advanced Packaging Tool)](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool)
> 
, and who decides what is in it?

The contents of Synaptic (as with all APT based tools) are controlled by what repositories you are subscribed to. The default repositories are controlled by Canonical, which is the company that manages and funds the Ubuntu project.
> 
Can I add other packages to my own Synaptic package manager? 

There are third party repositories you could subscribe to add more packages to Synaptic. In additions you can install stand alone .deb packages, which will show up in Synaptic after they are installed. Stand alone packages can be uninstalled with Synaptic, but they will not automatically update as synaptic will not know where to look for updates.
> 
How do I install programs which are not found there? 

The first thing to do is look for a stand alone .deb package, [www.getdeb.net](www.getdeb.net) and google are good places to try and find stand alone deb packages. After that you'll want to get a tarball (a .tar.gz, .tar.bz, or tar.bz2) from the authors. In the [Guide to installing anything in Ubuntu](http://monkeyblog.org/ubuntu/installing/) There is a section on installing from source/tarball, but it's a real pain in the back side and best avoided if at all possible.
> 
Which are the different ways to do this?

Thank you!

The above guide covers just about every install method there is, but you REALLY, REALLY want to stick to Synaptic and .deb packages if you can.

---

### Post by LillaEpsilon on 2008-05-02
Thanks guys! 

I think my question was a bit unclear; I understand how to use the Synaptic manager, but I would like to know what's under the user-friendly interface. I have also used the apt-get commands, but do they also only work with the same programs that are included in the Synaptic manager?

If I download my own file to install, does it have to be a debian file? Is this because Ubuntu is somehow "built on top of" Debian linux?

What is a repository? (Ok, I understand it is some kind of bundle of programs, but controlled by who?) and how do I subscribe to one?

---

### Post by PeterJS on 2008-05-02
> **LillaEpsilon said:**
> Thanks guys! 

I think my question was a bit unclear; I understand how to use the Synaptic manager, but I would like to know what's under the user-friendly interface. I have also used the apt-get commands, but do they also only work with the same programs that are included in the Synaptic manager?


It's all libapt under the hood, as with the rest of the APT family, have a look at the wiki page.

> 
If I download my own file to install, does it have to be a debian file? Is this because Ubuntu is somehow "built on top of" Debian linux?


You could also down load an .rpm and convert it to a .deb using a tool called alien, but that's hit or miss, some times it works well sometimes it doesn't. As for others their really aren't any, so yes you're constrained to tarballs, .debs, and .rpms, but that's because nothing else exists to be used. Ubuntu defaults to .debs because it's based on debian, and .deb/apt works so why break/change it.

> 
What is a repository? (Ok, I understand it is some kind of bundle of programs, but controlled by who?)

A repository is a specially designed website that stores and serves files using a known name and a known file structure. Here's the main mirror of the main repository, have a look around:
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

And as for who controls them, they're controlled by who ever hosts them. If I had anything worth publishing I could create my own repository right now.

> 
 and how do I subscribe to one?


The list of sources currently in use is stored at /etc/apt/sources.list. If you're looking for a graphical way of managing sources, have a look at System > Administration > Software Source. Repository descriptions take the form of:
```

type baseurl distname component1 component2 ... componentN

```
So for example the main ubuntu repository above is described as:
```

deb http://archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

```

---

### Post by Xiong Chiamiov on 2008-05-02
The link that kpkeerthi pointed out is an excellent one; give it a good read and keep it bookmarked somewhere.

Synaptic is merely a front-end for apt; anything you can do in apt, you can in Synaptic, and vice versa.  They both will install the same apps, etc.

If you absolutely cannot find something in the repository (get to that in a moment), then debian files (.deb) are the best, because they install very simply.  And yes, Ubuntu is based off of Debian.  However, you can also install things from source (usually .tar.gz).  There is also a way to install .rpm (which are packages for Red Hat), but I wouldn't recommend it.

A repository is a database off some number of applications.  When you run apt (or Synaptic, or adept), it downloads a list of what's available from each different repository you have specified in /etc/apt/sources.list (check it out - run sudo apt-get update).  By default, you'll have just the repos from Canonical (who sponsors Ubuntu), but you can add more just by adding them to that list.  You'll get specific instructions on how to do that when you come across one; [Wine]("http://winehq.org/site/download-deb") is a good example.

---

### Post by LillaEpsilon on 2008-05-02
Thanks a lot for the fast and thorough responses and links! This made me a lot wiser.

Now, here's a more elementary problem: I'd like to mark the thread as solved, but there is no such option under my thread tools, like there is in the link given in the bottom Xiong Chiamiov's post?

---

### Post by Xiong Chiamiov on 2008-05-02
Ah, well, that's because we just upgraded to a new version of the forum software a week or so ago, and they haven't gotten all the old modifications working yet.  It took a little while to get thanks going, now we're just waiting for "mark as solved" and the link to all the unanswered posts.

Short: don't worry about it, you can't at the moment.

---

