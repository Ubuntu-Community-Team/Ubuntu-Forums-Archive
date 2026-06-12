---
title: "Managing resources with Makefile"
date: 2009-03-18
forum: Programming Talk
---

### Post by jfbilodeau on 2009-03-18
Good day,

I'm hoping that someone with more experience can guide me. I'm getting fairly comfortable with autotool and creating Makefiles. My code compiles and runs. But I'm not sure how to manage resources associated with the application.

For instance, where should resources like text, xml, images, etc be stored (best practices) in relation to the project? How do you ensure that those resources are copied with the executable?

I did a bit of googling, but I haven't found anything satisfactory. Any pointers and tips are greatly appreciated!

Many thanks in advance!

J-F

---

### Post by rendon on 2009-03-18
Hello,

I've read about this before, and recently just started making *.deb files for installation (and they work! woohoo!).  Although I'm not a pro, I'll share my 2 cents of knowledge with you.  But this might be an arguable topic...

Number one, for all practical concerns, the most important thing is the file that gets called upon execution.  The one that the pros put in /usr/bin or /usr/sbin or whatever else is sure to be in your PATH variable.  If you're going to be brave enough to put something in here then you'd better make sure that the filename is unique to every other package in the linux world (or at least ubuntu).  I'm crazy, but I usually just do

```

apt-cache search desired_package_name

```

to see if it exists already...

Next, you might not have all of your program's tools and data in 1 file, so you're wondering where to put the rest of the stuff.  Try some of these commands:

```

#: ls -a /home/yourname

#: ls /usr/lib

#: ls /usr/share

#: ls /usr/local


```

and look at what's inside the different areas.  You'll notice that some areas are more popular than others, and if you 'ls' enough you'll notice that there are a ton of empty folders around the system as well.

You can see that the big dogs like python and firefox are more likely to be in some areas, while little guys like random plugins and silly games might show up in other areas.  I've heard people argue this matter, but the fact is that you can put this stuff almost anywhere besides the obvious no-no's such as /dev, /bin(s), /root, etc...

A lot of people seem to recommend /home/username for beginners.  I always put my personal programs in /home/me/bin and then add /home/me/bin to the PATH variable.  If I ever have a serious conflict I can just remove my personal /bin from the PATH variable until I figure out what's wrong.

This looks helpful:
[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

---

### Post by jfbilodeau on 2009-03-18
Thanks rendon,

The section on searchin for executable is very much appreciated. However, I'm wondering about the rest of the application's resources, like static config files, images for UIs, etc. How should I manage them with my makefiles and where should I store them?

Thanks!

---

### Post by rendon on 2009-03-18
That's actually exactly what I meant, the lib and share directories are paths to extra data needed for the executable, such as icons, button images, xml, misc data, etc...

have a look at this:
[http://packages.ubuntu.com/search?suite=intrepid&section=all&arch=any&searchon=contents&keywords=gimp]("http://packages.ubuntu.com/search?suite=intrepid&section=all&arch=any&searchon=contents&keywords=gimp")

That's the file tree for Gimp the image manipulation software.  On the top right of that page you should see an option to Search <by criteria>.  You should select "package contents" as the criteria and then search some popular softwares you know or use.

As for the Gimp, you can see how they put their binary executable in /usr/bin (of course).  Their plugins are in /usr/lib, and you can even see where they put their menu icons and so on...

That is an example of how you can organize your extra info.  Then your executable will have to be programmed to know the location of the info.  You choose where you want to put it, depending on what type of data it is, and then you tell your executable where it is.

For packaging, I'm a beginner, but I used this tutorial to get me going:  
[https://wiki.ubuntu.com/PackagingGuide/Python]("https://wiki.ubuntu.com/PackagingGuide/Python")

I recommend it because it's a very simple (although slow reading perhaps) example of *.deb package creation with a little python program.  The final product includes a manpage entry, icons, entry to the Applications menu, and Depends inclusion.

I took the example it makes and hacked it into my own package.

Here's the official Packaging Guide for Ubuntu as well:
[https://wiki.ubuntu.com/PackagingGuide/]("https://wiki.ubuntu.com/PackagingGuide/")

---

### Post by jfbilodeau on 2009-03-18
Thanks again. I've bookmarked your pages. Using your links, I managed to find the answer I was looking for.

Here's what I'm trying to do. I've got a simple autotools projects that compiles files.
```
$ mkdir build
$ cd build
$../project/configure
[...]
configure: creating ./config.status                                                         
config.status: creating Makefile                                                            
config.status: creating src/Makefile                                                        
config.status: creating config.h                                                            
config.status: executing depfiles commands                                                  
config.status: executing libtool commands
$ make
[...]
$
```

At that point, the executable is generated (yay!), but none of my resources follow the configure or make script. As of now, I manually copy the updated resources.

```
$ cp -r ../project/src/resources
```

What I'm hoping to do is about that last manual step using my makefile. The answer is to use the DATA primary in Makefile.am. Tried it and it did exactly what I was hoping it would do. Thanks very much for your help!

J-F

---

### Post by rendon on 2009-03-18
Glad to hear that you're on your way.  I believe that what you're looking for is a sort of automated Makefile process that organizes your data into the correct directories for you.  With the number of different distros for linux I don't know if that exists, and if it does, since linux is free and open I'm sure that you could change it anyway.  I don't see anything wrong with manually installing with the cp command as you where saying.  Just check to make sure the directories exist before you cp, and/or make the directories if they don't exist.

But in fact, the more unique the path to your data is, the less chance you have of a name conflict.  

Regardless, if you want to get into protocol, here is another very useful bookmark for you:

[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

---

