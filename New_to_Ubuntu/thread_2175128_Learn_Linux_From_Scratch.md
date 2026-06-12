---
title: "Learn Linux From Scratch?"
date: 2013-09-17
forum: New to Ubuntu
---

### Post by jack21 on 2013-09-17
Hi, I would like to learn almost everything I can about Linux now but not entirly sure where to start. I've looked at many sites about learning Linux but now seem to be a bit overloaded with info and so not so sure where to start. 

I understand that there are a load of careers and jobs that can come about as a result of being experienced with Linux such as Linux Adiminstration for example. 

I did come across a site called "Linux from scratch" which is do do with teaching you about how to actually build your own distro. But I'm still not so sure if that's for me.

So do you guys have any suggestions for where you would recommend a complete beginner to learn Linux?

Thanks

---

### Post by tgalati4 on 2013-09-17
How do you learn best?  Reading, hands-on, watching a video, listening to a podcast?

Find some old PC's (2 or 3) and load a different distro on each.  Then spend some time on the forums to get answers to questions that will come up.

Load a server on one of those PC's and install a LAMP stack and some services like from here:  [http://bitnami.com/stacks](http://bitnami.com/stacks)

Linux is built on frameworks, so when you study a particular framework, your knowledge will increase.  But it will take time.  It might take years.

---

### Post by papibe on 2013-09-17
Hi jack21.

I would not recommend that. I'd say install a server edition on VM or an actual machine, star playing with it and doing some admin work.

For instance you could:
[LIST]
[*]Create other users.
[*]Create samba, and nfs shares.
[*]Grant different access to different users.
[*]Setup a backup schedule.
[*]Grant remote access
[*]Etc.
[/LIST]
This way you could actually get to do real useful tasks. 

Just my thoughts.
Regards.

---

### Post by jack21 on 2013-09-17
> **tgalati4 said:**
> How do you learn best?  Reading, hands-on, watching a video, listening to a podcast?

Find some old PC's (2 or 3) and load a different distro on each.  Then spend some time on the forums to get answers to questions that will come up.

Load a server on one of those PC's and install a LAMP stack and some services like from here:  [http://bitnami.com/stacks](http://bitnami.com/stacks)

Linux is built on frameworks, so when you study a particular framework, your knowledge will increase.  But it will take time.  It might take years.

I learn best with hands on, reading and videos. And not sure what you mean by server and lamp stack. But I think I should manage to pick it up quickly.

---

### Post by jack21 on 2013-09-17
> **papibe said:**
> Hi jack21.

I would not recommend that. I'd say install a server edition on VM or an actual machine, star playing with it and doing some admin work.

For instance you could:
[LIST]
[*]Create other users. 
[*]Create samba, and nfs shares. 
[*]Grant different access to different users. 
[*]Setup a backup schedule. 
[*]Grant remote access 
[*]Etc. 
[/LIST]
This way you could actually get to do real useful tasks. 

Just my thoughts.
Regards.

yeah, again not sure about server editions but am a little familiar with VM. However I'm still trying to get the hang of Virtual-Box.

---

### Post by buzzingrobot on 2013-09-17
Since you are just starting out, here's what I recommend:  Play.

The time to decide how -- or if -- to build a career in Linux will come later.

Right now, you don't need to worry about that, and the specialization and narrowing of focus it will inevitably require.

A lot of skills and talents go into Linux:  building and running servers and networks; developing; graphic design; behavioral patterns (think GUI's), and more.

So, for the time being, let your curiosity lead you. When something piques your interest, research it and dig deep into it, until it starts to feel like work and gets boring. Then, go have some fun doing something else until something comes along that makes you want to find out how it works.

In the end, you will have a broader understanding and appreciation for Linux, and a better awareness of your own talents and interests, and where they do, and do not, intersect.

Linux From Scratch has a good reputation.  Remember, though, that it will teach you how to compile and build a whole lot of software and put it together as a Linux distribution.  Since you are just beginning, you will learn many things.  But, odds are very high that no employer will ever ask you to create a Linux distribution from the bottom up.

Linux is a version of Unix. As such, it incorporates a number of fundamental concepts that have been part of Unix from the beginning. I won't make recommendations here, but the creators of Unix were also pretty good writers.  Check into the history of Unix, especially the beginnings, and check out some of the books its creators have written. Sometimes people in Linux toss around the phrase "On the shoulders of giants...".  These guys are the original giants.

[More free advice:  Once upon a time, my job had me intervewing would-be sys admins and making hiring decisions.  Most rejected applicants were weak on networking, not maintaining server uptimes. Servers that can't talk to other servers are useless.  They do that talking over networks. And there are Windows and Apple and all sorts of machines on those networks.]

---

### Post by pbpersson on 2013-09-17
What are your goals?  Do you want to learn about the internals of how everything fits together?  Do you want to learn how to troubleshoot issues and fix a desktop/server that will not boot up?  Do you want to create file servers?  Print servers?  MythTV machines?  Do you want to host web sites?  Do you want to create new software for Linux?  Do you want to explore the similarities and differences between Fedora, Debian, OpenSUSE, Ubuntu, and Mint?

Your journey could follow very different paths depending upon your ultimate destination.

---

### Post by tgalati4 on 2013-09-17
OK, so let's say that you enjoy photography as a hobby.  You take pictures with a digital camera and you want to edit them.  How would you do that in Linux?

You install Ubuntu on spare machine and you load the *gimp* and you go to [http://youtube.com](http://youtube.com) and you type *gimp tutorials* in the search bar.  A bunch of videos will show up.  Watch a few of those.

Then do some reading:  [https://help.ubuntu.com/community/TheGIMP](https://help.ubuntu.com/community/TheGIMP)

Then go to your Ubuntu machine, load up some digital pictures and edit them with the *gimp*.  

So you have watched some videos, done some reading, then done some hands-on work.  

Pick any Linux topic and do the same 3 steps.  There are thousands of things to learn in Linux.  

So now you have to ask yourself, what am I interested in right now?

---

### Post by newb85 on 2013-09-18
tgalati4, I like your photography illustration.  To the specific example of gimp, though, I will throw out the warning that there are a lot of *really outdated* tutorials on gimp floating around the internet, which do more harm than good.

---

### Post by NT4usB on 2013-09-18
I started learning Linux back in 2006.
I wanted to record TV and didn't want to rent a cable box/DVR, so I set out to build one.
Did a lot of googling and settled on Ubuntu 6.06 and MythTV 0.17 (or was it 0.19?).
So I was going to learn Linux while I built the PVR.

In the early days MythTV and all the ancillary bits had to be compiled from scratch. No repository installs for any of it.

I spent a solid month, into the wee hours every night, and pretty much around the clock weekends... compiling, googling, recompiling, regoogling.
After one month, I finally had a working MythTV install. 

Then I go to format the large chunk of free space I had left on the HDD to use for storing recordings, only to discover I had screwed up the partitioning and there were no more partitions available.
Reformat* the HDD and start over... AAARRRRG!

This go round it took me about four hours to format, reinstall, and get back to a working MythTV install. Guess I learned a little something along the way.

The point of all this is: while "playing" with Linux (or anything, for that matter) to try and learn it might be productive, actually doing something with it will force you to learn.
As others have stated, pick some apps and learn how they work. Find a program that is not native to Ubuntu and make it run. 
Chose a project that has a starting point, a process to complete, and a result and see it through.
There are a ton of Linux apps that aren't quite ready for prime time yet, and oh so delightfully frustrating to try and make work.

(* I learned later that I could have simply used a live CD of gparted and fixed the partitioning without having to flatline it and start over.)

ct@dapperpvr:~$ uptime
 21:50:43 up 328 days, 22:27,  3 users,  load average: 0.85, 1.54, 1.43

---

### Post by jack21 on 2013-09-22
> **pbpersson said:**
> What are your goals?  Do you want to learn about the internals of how everything fits together?  Do you want to learn how to troubleshoot issues and fix a desktop/server that will not boot up?  Do you want to create file servers?  Print servers?  MythTV machines?  Do you want to host web sites?  Do you want to create new software for Linux?  Do you want to explore the similarities and differences between Fedora, Debian, OpenSUSE, Ubuntu, and Mint?

Your journey could follow very different paths depending upon your ultimate destination.

I want to learn about the internals as well as how to fix issues. And I'd like to a certain degree learn a bit more about differences.

But mostly however I'd like to learn how to administer a linux operating system competently.

---

### Post by jack21 on 2013-09-22
PS thanks to every one for their helpful replies and sorry for my late reply; I have been bogged down with a lot of studdying lately.

---

### Post by JonasDeMoor on 2013-09-28
I started using Linux back in the day with Ubuntu 10.10. Then I started exploring other distro's (Fedora, openSUSE, ...). But what really taught me how Linux works, was Arch Linux ([www.archlinux.org](www.archlinux.org)). 

It's a distro for more advanced Linux users, it can be daunting to set up. But you'll end up with a much faster and cleaner system and you learn somehting about Linux along the way. 
I recommend that you use beginner-friendly distro's like Ubuntu for several months first and that you're comfortable with the Terminal. Then go and try Arch in a virtual machine or on a spare computer. 

Another distro which is a good learning school is Gentoo ([www.gentoo.org](www.gentoo.org)). But that's more complicated than Arch.


Anyway, it's up to you. There are many ways you can learn more about Linux. I also read a lot and I watched many videos on YouTube. Some good channels are:
[LIST]
[*]Quidsup: most videos are Ubuntu-related: [www.youtube.com/user/quidsup](www.youtube.com/user/quidsup)
[*]Spatry: He mainly helps people with the transition from Windows to Linux: [www.youtube.com/user/linuxspatry](www.youtube.com/user/linuxspatry)
[*]InfinitelyGalactic: High quality reviews of Linux distros, apps, hardware,... Uploads video once a week: [http://www.youtube.com/user/InfinitelyGalactic](http://www.youtube.com/user/InfinitelyGalactic)
[/LIST]

Good Luck ! :D

(P.S. Sorry for bad English)

---

