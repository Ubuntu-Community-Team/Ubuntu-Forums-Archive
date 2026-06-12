---
title: "[SOLVED] I did a sudo dpkg-reconfigure -a"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-11-15
i did a 

sudo dpkg-reconfigure -a

and it took hours to get it to finsh.

it just configures the whole entire OS right? 

because i wasn't sure if i config an option where it should write on the hard drive more. where it would constantly keeps writing in my whole SSD. which would damage the lifespan of my SSD.

there isn't an option in the whole the command line right? I feel like i am getting paranoid, like if i should do a reinstall or something cause i don't remember turning on that option or not.

---

### Post by nhasian on 2008-11-15
here is some information i found about running Ubuntu on a Solid State Disk:

[http://ubuntuforums.org/archive/index.php/t-806006.html](http://ubuntuforums.org/archive/index.php/t-806006.html)

---

### Post by 3rdalbum on 2008-11-15
The ideal configuration for SSDs and HDDs with Linux is this:

/ on the SSD
/home, /tmp and swap on an HDD.

When your system is running like this, the only files that will be routinely written to on the SSD are relatively small, and the wear-levelling hardware inside the SSD will make the writes not worth you worrying about.

Obviously you want to minimise the number of times you run a command like dpkg-reconfigure -a, not least because it takes a long time to complete, but your SSD can survive a lot of big writes like that.

---

