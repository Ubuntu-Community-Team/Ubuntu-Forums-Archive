---
title: "Belarc Advisor Like Utility for Ubuntu?"
date: 2011-10-09
forum: New to Ubuntu
---

### Post by renewme on 2011-10-09
I have Ubuntu up and running on an older machine i had laying around. I am a layman and would really love a complete audit of my hardware including bios, chipsets, serial #'s the works like the Belarc Advisor will run you for free on a PC. Is there such a thing that will work on Ubuntu? Thanks for any help. Renewme.

---

### Post by love2learn on 2011-10-09
I love running Belarc for clients that have windows. I hope that someone has an answer to this as the last thing I have heard of is this:

[http://hardinfo.berlios.de/HomePage](http://hardinfo.berlios.de/HomePage)

good luck

---

### Post by stmiller on 2011-10-09
There are various things that do local security audits. One is tiger.

```
sudo apt-get install tiger
```

Then run:

```
sudo tiger
```

Otherwise, if you are just looking for hardware info:

```
lspci
```

```
lsusb
```

```
lscpu
```

```
cat /proc/cpu
```

---

### Post by duke.tim on 2011-10-09
+1

This is a great question. Taking a look at tiger!

A bit of a different tool but, nmap can be used to see how secure your computer is on a network. (pretty much the less information it can report the better)

---

### Post by anewguy on 2011-10-09
> **love2learn said:**
> I love running Belarc for clients that have windows. I hope that someone has an answer to this as the last thing I have heard of is this:

[http://hardinfo.berlios.de/HomePage](http://hardinfo.berlios.de/HomePage)

good luck

I just checked this out, as I know what the OP wants and this sounded more promising.  It looks like it hasn't been touched since 2009, and the page it points to for ubuntu and debian packages no longer exists.  I'm going to try getting the source code and see if it's possible to do anything from there.

Dave ;)

---

### Post by anewguy on 2011-10-10
.....EDITED OUT .....

EDIT:  FORGET DOING THE ABOVE.  IF YOU HAVE AN INTERNET CONNECTION JUST OPEN SYNAPTIC PACKAGE MANAGER, SEARCH FOR hardinfo, CHECK THE BOX NEXT TO IT AND APPLY - IT WILL JUST INSTALL IT FROM THERE - NO NEED TO DOWNLOAD SOURCE AND COMPILE IT.

NOTE TO ADMIN:  If we could get this installed by default, we could create a "check list" or skeleton post for people to use with, for example, network problems.  Someone wanting to know how to get their wireless working, etc., would not have to post, wait for someone to post back with several command lines, then run the commands and post all the output back.  In this example, using this tool, a command line of hardinfo -m network -r > mystuff.txt dumps all kinds of info about the networking for the PC.  Similarly, the "devices" module could provide the equivalent of lspci, lsusb, etc., all at once.  By directing the output to a file, we can simply tell the poster to run the command and attach the output in a post back here - everything we would need would be there to get started.  Since this is in the package manager, it would be nice if it was automatically installed.  With it auto-installed, the above network example could be run on a PC with no net access, the output file(s) copied to a removable media and taken to a PC with net access and posted.  Just an idea.

Dave ;)

---

### Post by Jay Car on 2011-10-10
> **renewme said:**
> I have Ubuntu up and running on an older machine i had laying around. I am a layman and would really love a complete audit of my hardware including bios, chipsets, serial #'s the works like the Belarc Advisor will run you for free on a PC. Is there such a thing that will work on Ubuntu? Thanks for any help. Renewme.

It's funny, Belarc was probably the utility I missed the most when I moved away from Windows.  But I never used it to look for security updates (though it would list the ones that were installed), but the hardware list was really useful when I worked on other people's Windows computers. 

Anyway, one of the first commands I learned here on the forums was this one to get a hardware inventory. It makes a nice list of everything on my computer (even some things I didn't want I wanted to know)  :):
```
sudo lshw -html > hardwareprofile.html
```

For software, the information here explains how to list all the programs that are installed on your system. : [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

I seem to remember that someone also wrote a script that would use that list on a new install and go get all the packages and install them for you. I never used that, and I can't seem to find any evidence of it now, so maybe I just dreamed it. 

Anyway, I found the hardware profile command, in particular, quite easy and useful, maybe it will be helpful for you, too.

---

### Post by anewguy on 2011-10-10
The previously mentioned hardinfo does that and more.  It can be run as a GUI as Belarc has, it can also be run from the command line and generate reports that way to a file.  These reports can be tailored by a few simple values at the command line.  While I didn't try it in the GUI outside of seeing it run, I'm sure the GUI allows for reports as well.  The GUI allows report generation, including output as HTML as well.

Very simple - install, run from the menus (Applications/System Tools/System Profiler and Benchmark, or run from the command line.

EDIT:  Just realized this sounds like I'm arguing or something, and nothing could be further from my mind.  I probably could have worded this better.  At any rate, the instruction you provided generates a good report and being HTML it is also easy to include as an attachment.  I was just basing this purely on something you could run like Belarc.  I apologize if I came across wrong.  ;)

And I still believe it should be installed by default.

Dave ;)

---

### Post by love2learn on 2011-10-11
yeah, 
 
I used to love hardinfo but I didnt like that it didnt have support anymore. I stopped using it last year and tried to forget about it. I wish someone would pick it back up and run with it but I am just not that guy right now.

---

### Post by anewguy on 2011-10-11
> **love2learn said:**
> yeah, 
 
I used to love hardinfo but I didnt like that it didnt have support anymore. I stopped using it last year and tried to forget about it. I wish someone would pick it back up and run with it but I am just not that guy right now.

I found it in synaptic package manager, so unless I added repository that I don't remember adding, I would think it must be being supported by someone now, even if not the original maintainers.  Since it seems to be open source I believe anyone can do what they want with it, so somebody could pick it up if they want to.  I may even take a look at the source code and see if it's too much for what I want to do right now or not.

Maybe someone else can tell us if someone else is supporting it now.

Have a good one!

Dave ;)

---

### Post by billshoff on 2012-12-19
"JUST OPEN SYNAPTIC PACKAGE MANAGER, SEARCH FOR hardinfo."

Still works!:razz:

---

