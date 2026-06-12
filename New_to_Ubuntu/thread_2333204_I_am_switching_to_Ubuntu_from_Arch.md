---
title: "I am switching to Ubuntu from Arch"
date: 2016-08-08
forum: New to Ubuntu
---

### Post by ziratul on 2016-08-08
I've been using Arch Linux for some time now, it is really great but bleeding edge software is not a good thing for regular productivity (software breaks).
I've choosen Ubuntu for the reason it has really big community and it's really stable.

However I am completely lost because I haven't been using debian-like distro before and I really
know nothing about Debian or Ubuntu.

1. Where can I find complete bzr and launchpad guide? (If there is a handbook or ebook, that would be awesome)
2. What is the name of community - managed repository for Ubuntu (Is there anything like AUR here)?
3. Where can I read more about Ubuntu apt, repositories in general?

Any other suggestions how to seamlessly transition from arch to ubuntu :S ?

P.S. (I Will eventually find this all by myself, but If any of you guys can save me some time.. that would be great)

Cheers

---

### Post by sudodus on 2016-08-08
Welcome to the Ubuntu Forums :-)

1. I don't know of any complete bzr and launchpad guide. There is information at [Launchpad itself](https://launchpad.net/). Let us wait for better tips from other people ...

2. It will probably be easy enough for you to read ***the man pages of apt and apt-get*** (considering that you come from Arch). But before you feel at home with the Debian and Ubuntu style of commands, you can also use the GUI tool ***synaptic***.

```
sudo apt-get install synaptic
```

3. Maybe PPAs (at Launchpad) correspond to what you want. For example, I maintain **ppa:mkusb/ppa** and **ppa:mkusb/unstable**, [described here](https://help.ubuntu.com/community/mkusb).

There is a lot of information at the Ubuntu wiki and Ubuntu help pages

[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by sudodus on 2016-08-08
When you visit the Ubuntu Forums you will soon find helpful posts by *oldfred*. This list, originally posted by him, may be useful for you

```
# Oldfred's command list for cleaning and repairing
 
#houseclean
sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

# Remove lock
# If you are absolutely sure you do not have another upgrade process running.
# Locked dpkg - only if sure you are not running another update.

sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a 

# added zika's tip for problems with hash sum mismatch

sudo rm /var/lib/apt/lists/*
sudo apt-get update

# added 2F4U's tips for Package Manager & Update Manager problems

Does executing these commands help?

cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update

This will rebuild the cache.
```

If it doesn't help, this forum post has additional suggestions:

[http://ubuntuforums.org/showthread.php?t=1869890](http://ubuntuforums.org/showthread.php?t=1869890)

-o-

I use the following commands to keep an Ubuntu based system up to date (or let the automatic GUI application ***update-manager*** to its job),

```
sudo apt-get update #resync package index
sudo apt-get dist-upgrade #newest versions of all packages including kernels, update must be run first
```

Use the following command in the rare instances, when you want to upgrade to a new release, for example 16.04.1 LTS to 18.04.1 LTS two years from now,

```
sudo do-release-upgrade
```

---

### Post by ziratul on 2016-08-08
Awesome @sudodus that is gonna help :)

---

### Post by coldraven on 2016-08-08
Hello and welcome to the forum!
This is a handy link for downloading all versions of ubuntu. After selecting one, scroll down the page for hash sums and download options. I usually use the torrent option, it's fast.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by grahammechanical on 2016-08-08
> Any other suggestions how to seamlessly transition from arch to ubuntu :S ?

Dual boot, for a start. From what I have heard Arch & Ubuntu are at opposite ends of the usability spectrum. Would a mountain climber have difficulty hill walking? Could a hill walker climb a mountain? The skills you learnt in Arch are still applicable in Ubuntu but with Ubuntu those of us who cannot climb a mountain can take a chair lift to the top. :)

I pre-fix my web searches with "wiki ubuntu" and that nearly always leads me to either an official or a community written wiki page. I even get links to the Arch wiki which I understand is very informative.

Regards

---

### Post by mastablasta on 2016-08-08
more like those that don't want to do the camping get a hotel and all the services available with it. and eventhough camping is tremendously fun, at least in my case (and for now and with limited time on my hands) hotel seems a better option.  :P

now back to repositories - there are a few types available. check the sowftare sources to enable them. there are official ones, then those with proprietary software, then external ones, PPAs... and ofcourse lately there are also snaps. i am not sure how widespread they are on the desktop OS, but hopefully we will see more and more of them. they owudl solve plenty of issues and make it easier to use a certain version of program.

edit: there are also .deb files available for installing certain apps.

---

### Post by tsjswimmer on 2016-08-14
Ubuntu doesn't have anything like AUR. The closest thing to AUR you'll find in Ubuntu would be third-party repositories, many of which can be found on Launchpad. I find that the Launchpad repositories, which are AKA "Personal Packages Archives", or "PPAs", are more useful than AUR, since they offer pre-built packages that are updated automatically (since they are added to APT's package repos).

BTW, if you wish to make package management easier, you should consider learning to use aptitude. What makes aptitude great (IMHO) is that, if you execute it without any arguments, it will open in a graphical mode, although it's still terminal-based. The fact that it runs in the terminal, instead of using X, makes it a very light program, which is something I like. Also aptitude's graphical-ness makes it a good choice for resolving package dependency issues. Or, you could try synaptic or muon, they're both quite nice (although I still like aptitude better).

---

