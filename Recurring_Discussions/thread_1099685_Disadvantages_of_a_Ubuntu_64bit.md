---
title: "Disadvantages of a Ubuntu 64bit?"
date: 2009-03-18
forum: Recurring Discussions
---

### Post by kamitsukai on 2009-03-18
Are there any real disadvantages to Ubuntu 64bit anymore? as I know that Flash and Java have been sorted out now but is there anything which is kind of annoying?

I only ask as I'm building my new PC tomorrow and I intend to put Ubuntu 8.10 64bit on it 

Thanks in advance!:D

---

### Post by simtaalo on 2009-03-18
i've been using 64-bit nearly as long as i've been using linux and never had any problems.

---

### Post by squaregoldfish on 2009-03-18
I've been running 64-bit for a good while now. I can't think of anything that doesn't work.

Steve.

---

### Post by kamitsukai on 2009-03-18
Brilliant Thanks Very Much!

---

### Post by gn2 on 2009-03-18
No disadvantages with 64 that I've found.

However you can have both, after installing 64 with separate partitions for / and /home just create another 10gb or so / partition and install 32 into it sharing the existing /home partition.

Just set up different user names when installing 32 and 64, say for example Kamitsukai32 for the 32-bit and Kamitsukai64 for the 64.
This will keep all the configs in separate /home directories and you can dual-boot between 32 and 64 as you please.

---

### Post by stchman on 2009-03-18
> **kamitsukai said:**
> Are there any real disadvantages to Ubuntu 64bit anymore? as I know that Flash and Java have been sorted out now but is there anything which is kind of annoying?

I only ask as I'm building my new PC tomorrow and I intend to put Ubuntu 8.10 64bit on it 

Thanks in advance!:D

With Flash 10 64 bit and icedtea plugin I will say no.

If you install 3rd party debs you have to be sure they have 64 bit debs or build them from source.  I stay inside the repos so I have no problem.

---

### Post by squaregoldfish on 2009-03-18
> **stchman said:**
> 
If you install 3rd party debs you have to be sure they have 64 bit debs or build them from source.  I stay inside the repos so I have no problem.

It's entirely possible to install the 32-bit subsystem, so 32-bit debs will work just fine.

Steve.

---

### Post by LowSky on 2009-03-18
no problems using 64bit for a while now, and 32bit apps are eaisly used and supported

---

### Post by Weidbrewer on 2009-03-18
> **gn2 said:**
> 
Just set up different user names when installing 32 and 64, say for example Kamitsukai32 for the 32-bit and Kamitsukai64 for the 64.
This will keep all the configs in separate /home directories and you can dual-boot between 32 and 64 as you please.

That's more or less what I've got running myself right now.


Yeah, haven't found any major show-stoppers with 64 thus far.

---

### Post by fooman on 2009-03-18
> **stchman said:**
> With Flash 10 64 bit and icedtea plugin I will say no.

fyi,  i came across the following post a few days ago...installed the 64bit plugin as described in the post,  then uninstalled the icedtea plugin and it works great!  ....java pages load* much* faster then when i was using icedtea.

heres the post:

[http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

enjoy!  :)

---

### Post by presence1960 on 2009-03-18
> **kamitsukai said:**
> Are there any real disadvantages to Ubuntu 64bit anymore? as I know that Flash and Java have been sorted out now but is there anything which is kind of annoying?

I only ask as I'm building my new PC tomorrow and I intend to put Ubuntu 8.10 64bit on it 

Thanks in advance!:D

Here are the disdvantages of running 64 bit:

---

### Post by bodhi.zazen on 2009-03-18
> **kamitsukai said:**
> Are there any real disadvantages to Ubuntu 64bit anymore? as I know that Flash and Java have been sorted out now but is there anything which is kind of annoying?

I only ask as I'm building my new PC tomorrow and I intend to put Ubuntu 8.10 64bit on it 

Thanks in advance!:D

This is a recurring discussion so I moved your thread.

See : [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by stchman on 2009-03-18
> **squaregoldfish said:**
> It's entirely possible to install the 32-bit subsystem, so 32-bit debs will work just fine.

Steve.

Defeats the purpose of using 64 bit.

---

### Post by wolfen69 on 2009-03-18
> **stchman said:**
> Defeats the purpose of using 64 bit.

what is the purpose? i noticed no difference when i tried it.

---

### Post by stchman on 2009-03-19
> **wolfen69 said:**
> what is the purpose? i noticed no difference when i tried it.

I can use all of my 6GB RAM.  Apps do run a touch quicker in 64 bit.  Yes 64 bit uses a bit more RAM, but 64 bit can address a lot more.

Not to mention I paid for a 64 bit processor so I might as well use it.

---

### Post by gn2 on 2009-03-19
> **wolfen69 said:**
> what is the purpose? i noticed no difference when i tried it.

You need to do some encoding tasks and time them, Phoronix did, [here's the results]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=4").

In normal use, there's no appreciable difference between the two.

---

### Post by bodhi.zazen on 2009-03-19
> **gn2 said:**
> you need to do some encoding tasks and time them, phoronix did, [here's the results]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_810_vs_fedora_10&num=4").

In normal use, there's no appreciable difference between the two.

+1 ;)

---

### Post by Thelasko on 2009-03-20
The only disadvantage of 64-bit at the moment is that certain drivers don't work.  Most of them are proprietary printer drivers that don't work very well in 32-bit either.

---

### Post by dasunst3r on 2009-03-20
It used to be the case that the Flash and Java plugins did not have the 64-bit version.  This is no longer the case.  I've been using 64-bit since Intrepid Ibex (8.10), and I find no show-stoppers.  At the same time, my computer doesn't feel any faster.

---

### Post by kamitsukai on 2009-03-20
> **dasunst3r said:**
> It used to be the case that the Flash and Java plugins did not have the 64-bit version.  This is no longer the case.  I've been using 64-bit since Intrepid Ibex (8.10), and I find no show-stoppers.  At the same time, my computer doesn't feel any faster.

But why would it run faster? surely a 32bit Ubuntu and a 64bit Ubuntu with the same specs would be the same speed if not very similar? the only reason I'm considering 64bit Ubuntu is s that I have the option to install more ram as I've just bought 4gb of OCZ 1033mhz to go with my new Phenom II 940

Also Can someone elaborate a bit more on this "32-bit subsystem"? as I'm not quite sure what it is

Thanks so far:D

---

### Post by bodhi.zazen on 2009-03-20
Because most apps run by most users are not limited by RAM or CPU.

Most desktop users do not need more then 1, let alone 2 Gb RAM.

And most apps, like open office and firefox, sit waiting for user input.

---

### Post by Naiki Muliaina on 2009-03-20
> **wolfen69 said:**
> what is the purpose? i noticed no difference when i tried it.

The purpose in my case is 8gb of ram ^^ I like to use it ^^ But on the matter of things running faster, i only notice a difference when i have stuff like Savage 2, Prey, or Second Life ramped up to the max. My PC slows a bit on 32bit when i really ramp stuff up. If i only had 3-4gb in my PC, id prolly stick with 32 bit as there are more 32 bit debs, and when im using a 32 bit proggy on my 64 bit Xubuntu, it seems to take more ram to use. Theres a reason for it, prolly something to do with the 32 bit subsystem thingy. Im pretty sure its in the 64 bit FAQ in the Ubuntu forums 64 bit forum.

---

