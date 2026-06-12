---
title: "Linux noob."
date: 2008-07-11
forum: New to Ubuntu
---

### Post by munnyman5 on 2008-07-11
Hello

I am thinking of putting ubuntu on my laptop. I know it's all user friendly and all that, but the whole partitioning deal has me really nervous. When I set up ubuntu, will it make the hard disk one big partition with only ubuntu on it? Because I have an Acer 5920G laptop and it has 2 evenly sized partitions, one of which I can use and the other I have no idea what to do with. I want to reformat to have a Ubuntu/Vista dual boot (I have the reinstallation CD that came with the laptop). Is there some sort of noob-friendly step-by-step tutorial on how to go about this, because as much info as there is on the interwebz, I haven't actually found anything that was thorough enough to actually tell me what the heck partitions are and how I can control them,

Thanks in advance.

---

### Post by iaculallad on 2008-07-11
What else is left to write, This pages had it all:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by zenzizenzizenzic on 2008-07-11
First off, welcome to Ubuntu. :)

When you install Ubuntu, it will ask for a partition on which it can install.  If none are available, you will have options (guided or manual) for partitioning the disk yourself.  Rest assured that it won't just wipe out everything you already have and replace it with one big partition unless you want it to!  If you have an empty partition already, then I'd suggest you only use that and not touch your windows partition.

You should probably divide your empty partition into two more - a large one (ext3) and a smaller one (linux-swap) which usually should be about 1-2x the amount of RAM you have in size (mine's 2GB to match my 2GB of RAM).  The partition editor, called gparted, will guide you through this process with a nice graphical interface, so it's easy to see what will happen.

---

### Post by hyper_ch on 2008-07-11
it is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

and it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

---

