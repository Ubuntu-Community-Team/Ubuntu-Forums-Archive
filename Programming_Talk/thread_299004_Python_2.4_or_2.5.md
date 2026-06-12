---
title: "Python 2.4 or 2.5??"
date: 2006-11-13
forum: Programming Talk
---

### Post by dannyboy79 on 2006-11-13
I was reading this thread here and would actually like to start to learn how to program. I would like to be able to make simple little programs instead of having to go out and find them. i am using this tut for beginers [http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/) and it tells me to download Python cause that's what I want to learn. Well, I noticed that Python 2.4 is in the repos (Dapper) but 2.5 is available in there website. Should I stick with 2.4 or go with 2.5. Python's website does state that 2.5 is the latest stable release. What do ya guys think. Then also, it's a tar ball or whatnot, where would I put it so that when I configure it and make check it and checkinstall it it goes in the place I want it to. That's one thing I am not sure about yet, if I install custom apps where do I want to put them or build them so they end up in the correct place? for example, I downloaded the source for gxiso, it was a python install script, I ran it and now my program is stored buired in a home folder so when I want to run it I have to cd to it first or enter the long *** location and command cd /home/daniel/300gb-ext3/downloaded/linux-programs/gxiso-1.5/build/scripts-2.4/gxiso.py. see what I mean, is there is way I can move the .py file and all it's libs or whatever and get it so I can just type in gxiso.py at the main command line like I can for other commands, like cp for example. or do I have to add some location to the source path or whatever they call it?? i just started learning linux this march and ubuntu is my first try so please correct me when I am wrong. I know I have asked 2 different things here but hopefully some1 can answer both. thanx.

---

### Post by cwaldbieser on 2006-11-13
> **dannyboy79 said:**
> I was reading this thread here and would actually like to start to learn how to program. I would like to be able to make simple little programs instead of having to go out and find them. i am using this tut for beginers [http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/) and it tells me to download Python cause that's what I want to learn. Well, I noticed that Python 2.4 is in the repos (Dapper) but 2.5 is available in there website. Should I stick with 2.4 or go with 2.5. Python's website does state that 2.5 is the latest stable release. What do ya guys think. Then also, it's a tar ball or whatnot, where would I put it so that when I configure it and make check it and checkinstall it it goes in the place I want it to. That's one thing I am not sure about yet, if I install custom apps where do I want to put them or build them so they end up in the correct place? for example, I downloaded the source for gxiso, it was a python install script, I ran it and now my program is stored buired in a home folder so when I want to run it I have to cd to it first or enter the long *** location and command cd /home/daniel/300gb-ext3/downloaded/linux-programs/gxiso-1.5/build/scripts-2.4/gxiso.py. see what I mean, is there is way I can move the .py file and all it's libs or whatever and get it so I can just type in gxiso.py at the main command line like I can for other commands, like cp for example. or do I have to add some location to the source path or whatever they call it?? i just started learning linux this march and ubuntu is my first try so please correct me when I am wrong. I know I have asked 2 different things here but hopefully some1 can answer both. thanx.

I'd start with 2.4 and get comfortable with that first.  Once you get the hang of it, you can install 2.5 and start exploring some of the new features.  Your 2.4 programs should still work.

---

### Post by dannyboy79 on 2006-11-13
> **cwaldbieser said:**
> I'd start with 2.4 and get comfortable with that first.  Once you get the hang of it, you can install 2.5 and start exploring some of the new features.  Your 2.4 programs should still work.

why would i not just start with 2.5? i just don't understand why I would install 2.4 when I can install 2.5? I haven't tried either so wouldn't it possibly cause confussion when I try to go from 2.4 to 2.5? i do appreciate you opinion I am simply trying to make an educated decision.

---

### Post by shining on 2006-11-13
> **dannyboy79 said:**
> why would i not just start with 2.5? i just don't understand why I would install 2.4 when I can install 2.5? I haven't tried either so wouldn't it possibly cause confussion when I try to go from 2.4 to 2.5? i do appreciate you opinion I am simply trying to make an educated decision.

Because, as you said, 2.4 is in the repos, and it's always much easier and cleaner to install softwares from the official repos. The second choice is unoffical repos, and then installing single .deb package. And the last choice is to compile, and install manually.
It's fine too, but it requires more work and experience, and it's most of the time just not needed.

---

### Post by skymt on 2006-11-13
Go with the default, 2.4. Most applications and libraries in the repos are still not updated for 2.5. Once they are, 2.5 will be the default, and you should get it as an update.

EDIT: shining: 2.5 is actually in edgy main. It's called "python2.5". The "python" package currently depends on "python2.4".

---

### Post by shining on 2006-11-13
> **skymt said:**
> 
EDIT: shining: 2.5 is actually in edgy main. It's called "python2.5". The "python" package currently depends on "python2.4".

dannyboy79 said he was using dapper though.

---

### Post by junglepeanut on 2006-11-14
Currently all my versions link to different libraries properly except 2.5. I can mess with paths and make it work, but if you are new to programming you do not need to be wondering why your program is not working when it should be, it is just that 2.5 is not perfect yet so I recommend the other versions for now.

---

### Post by dannyboy79 on 2006-11-14
thank you all for your help, i now will install 2.4 based on educated responces and experience. I appreciate everyone's help!! well, this should be fun to start learning how to program at the age 27. Here I go into the depths of code

---

### Post by zachtib on 2006-11-14
i guess you've decided on 2.4, and if you need another reason, consider this:

for my project, We've been using 2.4 even though 2.5 was released before we started coding.  The reason for this, as was stated earlier, is that Dapper still ships with 2.4, and 2.5 doesn't offer any particularly innovative features that we need.  By writing our program in py2.4, it is still able to run on Dapper systems, while if we had used 2.5, Dapper users would have to install a newer version of python

---

