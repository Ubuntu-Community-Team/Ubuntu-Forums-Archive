---
title: "Problems installing &quot;libwxgtk2.6-0&quot;"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by march1291 on 2008-06-19
Hello.

I'm having no luck installing the package 'libwxgtk2.6-0'. The install screen says that all dependencies are met, but once the install finishes, [_this error message_]("http://img146.imageshack.us/img146/5734/screenshotgdebigtk1lm8.png") appears. I would take this to mean that I should uninstall 'libgtk2.0-0', but there's a long list of packages that would be affect, so I'm wary.

Also, I should add that I don't have an Internet connection on my Ubuntu computer. I install packages by downloading the deb files on this computer, transferring them to the Ubuntu computer, running "install <file> -t <destination folder>" from root in terminal, then installing the products with GDebi Package Installer.

Thanks,
Zech

---

### Post by phidia on 2008-06-19
You might want or need to create a local repository take a look at [this]("http://ubuntuforums.org/showthread.php?t=20217").
BTW what version and arch of Ubuntu are you using? (32 or 64 bit)

---

### Post by march1291 on 2008-06-19
Thanks for the quick response. I wish I'd seen that thread a few days ago.

However, most of the answers given in that thread are for people who have Ubuntu on both their connected and disconnected computers. I should've been more clear: The computer I'm on now (the connected one) is Windows XP, and the other computer is Ubuntu.

One fellow seems to be in the same situation:
> **chrisblack said:**
> However I've no ubuntu at work, and no chance of installing it, so is there anyway I can download and burn the repositories to CD, so I can add the CD at home?
...and someone suggests he download the packages then undergo some process involving "loopback" (which I don't understand at all) to establish a local repository by mounting the packages in an ISO. I would try, but the link ([http://cargol.net/~ramon/ubuntu-dvd-en](http://cargol.net/~ramon/ubuntu-dvd-en)) no longer works. 

I should also note that getting packages the way I do has been quite smooth if a bit tedious. My problem, I think, is more a question of figuring out how to reconcile 'libwxgtk' with 'libgtk'.

The ultimate goal--the reason why I need this package in the first place--is to install VLC Player, and this is the last depended-upon package left.

Finally, I'm on Hardy Heron (8.04), 32 bit, i386.

Thanks again,
Zech

---

### Post by phidia on 2008-06-19
march1291, maybe that is the last package you need but it's hard to say that for sure because once you actually got to installing that package that "last" package could have dependencies, so in fact it wouldn't be the last. 

I say that because people who used to install "by hand" would go through this huge dependency nightmare of hunting for package after package. So apt/synaptic/the package manager resolves that mostly.

And you certainly can try to do it the way you are. I wonder if you could share your internet connection with the ubuntu computer? Other than that I am stumped to help you-sorry.

Another thought I had was that the line from the output you gave the screenshot of > libgtk2.0-0 conflicts with libwxgtk2.6.0 (<<2.6.3.2.2-) could be telling us that you need a later version of libwxgtk. I'm not sure though it's just a guess.

---

### Post by march1291 on 2008-06-19
yeah, you're right about the dependency mazes. soon i'll run through one of those howtos and try to set up a local repository.

as for trying a later version of libwxgtk, the funny thing is, I can install the package 'libwxgtk2._8_-0' just fine, but vlc is somehow unsatisfied.

zech

---

### Post by mc4man on 2008-06-20
I think your problem (or one of) is not that libgtk2.0-0 has to be removed, it has to be updated. (Your ver. is 2.6.1.2.)  libgtk2.0-0 is a _dependency_ of libwxgtk2.6-0.  You want ver. 2.12.9-3ubuntu4  (link shows .....2 which will work)
Whether that affects other packages remains to be seen.
Did you upgrade or do a fresh install of Hardy?

[http://packages.ubuntu.com/hardy/libgtk2.0-0](http://packages.ubuntu.com/hardy/libgtk2.0-0)
[http://packages.ubuntu.com/hardy/libwxgtk2.6-0](http://packages.ubuntu.com/hardy/libwxgtk2.6-0)

don't remove libgtk2.0, just install the deb. Before that you may want to remove libwxgtk2.8-0 (and gpac if needed). It may work with the ver. you just installed, may not, libwxgtk2.6-0 will work

---

### Post by march1291 on 2008-06-26
Thanks for the suggestion mc4, and it was a fresh install of Heron.

After finally making the effort to download the Ubuntu package ISOs and create local repositories, I've managed, by downloading the newest version of VLC and somehow skirting the problem of 'libwxgtk' altogether. It was a job getting all the repos in place, but now I feel much more comfortable in Linux, and I can finally watch DVDS!!!!

As for the specific problem I had, I ran into a few other packages that did basically the same. Generally, the problem comes up when an older version is interfering with the installation of a newer version (not exactly the problem with libwxgtk, but close). Any possibility that libwxgtk was either too new to work with libgtk or relied on a later version of gtk (basically the inverse of your suggestion, mc4man)?

Thanks again, both of you.

---

### Post by mc4man on 2008-06-26
> basically the inverse
Your 100% right,I spaced out and flipped things around.
The ver. of libwxgtk2.6-0 you were trying to install was from dapper

---

