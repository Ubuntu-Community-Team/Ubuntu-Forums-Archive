---
title: "Apt-get for local package installation should be easier"
date: 2006-08-06
forum: Other OS Talk
---

### Post by peabody on 2006-08-06
I've recently switched over from Fedora to Ubuntu and am loving it.  I was always a Debian fan but often felt both Debian testing and stable were far too behind the latest software and I never felt like running unstable.  Fedora was a pain, but I liked it for the fact that it was highly bleeding edge and stable.  Now with Ubuntu I feel I have the best of both worlds.

However, there were two things that I liked about yum.  It was easy to generate a list of available packages from the command line and it was easy to install packages on the file system with automatic dependency resolution.  In Fedora, this was all you had to do to install an rpm with depedency resolution:

```
[font="monospace"]sudo yum localinstall *.rpm.[/font]
```

I finally figured out how to do something similar with apt using the following document:

[http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html)

section 2.2 goes over how to setup filesystem repositories.  Something tells me there isn't a good reason that this should be so involved.  Sure it's necessary if you have a repository of packages on a CD or a network share, but it seems asinine to have to go through the same procedure for just one or two packages.


***[Edit: Disregard the below.  I've found my solution.  apt-cache search <name>.  Where have you been all my life?]***

I would also typically generate a list of packages by the following on fedora:

```
[FONT="monospace"]sudo yum list > packages[/FONT]
```

this would give me a text file called packages that I could grep through when I was looking for something.  I've done some research and this is the only equivalent I can find with apt; an ugly piece of shell magic:

```
[font="monospace"]cat `ls /var/lib/apt/lists/*_Packages` | grep "^Package:" | cut -d: -f 2[/font]
```

Perhaps there's a better way to do it?  I'm perfectly well aware of all the GUI tools at my disposal, but I'm a CLI kinda guy.  It's not that I won't use GUI's but I prefer a shell solution in the long term.

Anybody wish to enlighten me to a better solution I'm unaware of?

---

### Post by Dr. Nick on 2006-08-06
for installing a few packages via the terminal look at dpkg, It doesnt need a repo setup. I am 99.9% certain their is a command like

sudo dpkg -i *.deb

that will isntall all debs from a folder

---

### Post by TravisNewman on 2006-08-06
Dr. Nick, I use that all the time. I have all my updated debs in a single folder, and when I install a new system I copy over that folder, cd into it, and dpkg -i *.deb

Very handy.

---

### Post by Dr. Nick on 2006-08-07
Cool, im glad that was right. I recall having done a mass deb install before but forgot what exactly the syntax was.

---

### Post by peabody on 2006-08-07
I appreciate the replies, however, dpkg does not perform automatic dependency resolution.  ***IF*** you have all the packages you need (in other words, you're not missing any debs that any other debs depend on), sudo dpkg -i *.deb does indeed work.

I ask because I tried to install two debs for Ubuntu from the democracy tv project.  The debs required the boost library bindings for python as well as something else and so dpkg refused to install them.  I had to manually track down the dependencies myself.

---

### Post by 3rdalbum on 2006-08-07
I don't have a local .deb file to try this out on, but I'm pretty sure that you can invoke gdebi from a command-line and have it install the package, resolving dependencies as it goes.

```
gdebi package.deb
```

---

### Post by TravisNewman on 2006-08-07
Will gdebi install more than one at a time?
like this:
gdebi *.deb
???

---

### Post by Iandefor on 2006-08-07
You know that setting up local repositories was never intended as a solution to a one-off install, right? I mean, that solution is hardly the way to go if you download a promising .deb and don't want to handle dependencies on your own. It's about 50 times more work than just sudo dpkg -i and installing missing dependencies by hand. I remember when I futzed with democracytv. Both the missing dependencies were in the repos, and I just did a quick apt-get for those packages and voila! it installed without a hitch. 

That said, if it's worth it to you to go to the trouble of setting up a new repo to save the trouble of manually meeting dependencies for a downloaded .deb, it might also be worth using SMART, which lets you use something so primitive as a directory full of .debs as a repo.

---

