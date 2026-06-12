---
title: "Hardware issues in Ubuntu installed using Wubi"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by madnag4u on 2011-09-16
Good evening folks!

This is the first time I am posting a thread on this forum. I am an Ubuntu fan and have recently re-partitioned my hdd to house both Windows and Ubuntu 11.04. Let me jump right to the problem...

I started using Ubuntu 10.04 by using the Wubi installer. That was about 1 year ago. Later when I was upgrading to 11.10 (inside the wubi created partition), my motherboard got damaged and a certain component had to be replaced. After the repairs, I re-partitioned my hdd and installed 10.10 and then successfully upgraded to 11.04.

This year, I convinced two friends of mine to use Ubuntu 11.04 and had it installed on their systems using Wubi. Approximately one month later, one of them burned his graphics card while the other's laptop would not work while charging. When diagnosed, both had hardware issues. Coincidentally, both were using Wubi-installed Ubuntu when the problem occurred. 

This made me wonder: **Was it Wubi-installed Ubuntu that was creating motherboard fryups?** Because, Ubuntu installed in partitions was not showing any issues...

Recently, I had re-partitioned another friend's system to dual boot windows and ubuntu. Both his and my systems are working perfectly fine, no issues at all.

Seeing this I had to **uninstall Wubi-installed Ubuntu** from all other systems of other friends.

So, my question is, **are the motherboard problems caused due to Wubi? Has anyone else experienced the same problem? If yes, I would like to contact the Ubuntu team regarding this.**

---

### Post by magic8ball on 2011-09-16
I don't think so.  The only reasonable link that I can think of between 3 different hardware problems on 3 different systems in 3 different locations is heat buildup, but even that's a stretch. My vote is that what you saw is strange coincidence.

---

### Post by Frogs Hair on 2011-09-16
I started with Wubi and have friends that have been using it with Win 7 since 10.04  doing clean installations of the newest versions. None have ever reported hardware related problems .  Here are two links that you could post a question .

[https://bugs.launchpad.net/wubi](https://bugs.launchpad.net/wubi)

[http://askubuntu.com/](http://askubuntu.com/)

---

### Post by 3rdalbum on 2011-09-16
There's no way can Ubuntu "burn" a graphics card; as far as I'm aware they have sensors that will automatically turn the GPU off if it reaches a critical temperature.

Ubuntu doesn't even interact directly with laptop charging hardware, so that's not a cause-and-effect either.

And the only difference between regular Ubuntu and one running with Wubi is that the Wubi one is a filesystem inside a filesystem. There's no other differences.

---

