---
title: "Thunar suddenly very slow first time"
date: 2014-02-04
forum: New to Ubuntu
---

### Post by iowamv on 2014-02-04
In the last day or so I've noticed that Thunar is taking 20-30 seconds to start, but only the first time I run it. I've searched the web for solutions, and have found dozens of threads about this. I'm confused, because there are many, many solutions offered (eliminating thumbnails, changing permissions within Thunar, editing various files, removing thumbnail cache, references to samba...). In many cases, the threads are marked "solved," or seem to reassure that the problem has been fixed in the current version. I'm using version 1.6.3, with XFCE. I'm new to Linux, and this has me baffled. Can anyone help?

---

### Post by Tristan_Williams on 2014-02-05
There are a few things you could try. However, no method of fixing anything is garunteed to work, no matter what you are fixing or how you are fixing it.

Suggestion 1:
Try reinstalling it.
To reinstall it, open a terminal, and run the following command:
```

sudo apt-get install --reinstall thunar

```


Suggestion 2:
Free up some disk space.
The first time thunar runs, it has to look through all the directories on your system (the main ones at least) and remember 'sort-of' what's in there, so it doesn't take
as long to open when you decide to browse the filesystem.

Note: This probably won't make much of a difference in thunar, but will help your overall system performance, which in turn helps thunar:
Run the following commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install -f
sudo apt-get autoclean        # This is one of the main ones we are needing for increased performance
sudo apt-get autoremove     # This is also a main one... The others just make sure everything is good and updated

```


Suggestion 3:
Rebuild Thunar from source:
Building an application from source means that it is build specifically for YOUR computer. No extra crap from other architectures.
First, make sure you have "apt-build" installed:
```

sudo apt-get update
sudo apt-get install apt-build

```
During the installation, apt-build will ask you for configuration options. Use the following options:

- Directory used by apt-build to download and build packages:                /var/cache/apt-build/build
- Directory used to store packages built by apt-build:                             /var/cache/apt-build/repository
- Add apt-build repository to sources.list?                                             YES
- Optimization Level:                                                                           Medium (strong produces unstable code)
- Options to add to gcc:                                                                       [DON'T ADD ANYTHING HERE]
- Options to add to make:                                                                    See the next section, labeled "make options"
- Architecture:                                                                                    Select your processor

MAKE OPTIONS:
Find out how many cores your processor has. Let's pretend I have 2 cores.
Add 1 to the number of cores you have. For example, 2 + 1 = 3
In the section labeled "Options to add to make", I would use "-j3" (without quotation marks)
If you have 1 core, use  -j2
If you have 4 cores use -j5
You should get it by now...

Now the screen will close, and everything is back to normal.
We need to build thunar, so issue the following commands:
```

sudo apt-build update
sudo apt-build install thunar thuna-data thunar-archive-plugin
sudo apt-build clean-build
sudo apt-build clean-repository
sudo apt-build clean-sources

```

---

### Post by Bucky Ball on 2014-02-05
Sorry, Tristan_Williams, but I think you're on the wrong track. This is a known issue with Thunar and there are bug reports and pages about it all over. The fix has nothing to do with reinstalling, cleaning packages or anything like that. ;) 

Try point #2 here:

[http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

Read all about it here:

[https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117](https://bugs.launchpad.net/ubuntu/+source/thunar/+bug/775117)

The bug's been around for ages. To do with gvfs. I fixed this myself not less than a week ago, but not sure if this was my exact method. I'll check that computer and see if I have it archived.

(PS: OP, a search for 'thunar slow xubuntu' will turn up hundreds of pages about this, along with the fix.)

---

### Post by iowamv on 2014-02-05
Thanks to both of you. I did spend the better part of a couple of hours searching and reading (I've thus far been able to solve virtually all of my beginner Linux questions by searching the web), and those solutions were among the ones I saw. But after having read about several others solutions and having tried them at least 3 of them unsuccessfully, I decided it might be unwise to continue making seemingly random changes to my computer based on all of those earlier "slow Thunar" threads. Since many of the threads were several years old (this really is a well-worn topic), I was hoping that some kind of consensus had finally shaken out about the cause and solution-- and that I was simply not seeing the forest for the trees. By the looks of your response, it seems that might be the case. 

I just made the change to network.mount and the problem seems fixed. Hallelujah! Thunar snapped to life the first time I ran it.

Thanks again for taking the time to help.

---

### Post by Bucky Ball on 2014-02-05
All good. Let us know if it stays fixed after a couple of reboots then mark the thread as solved to help others. ;)

---

