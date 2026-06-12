---
title: "Hard Drive Size Inconsistencies"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by ealrgrey on 2008-09-23
[[IMG]http://img528.imageshack.us/img528/9149/screenshotdiskusageanaluk5.png[/IMG]](http://imageshack.us)
[[IMG]http://img528.imageshack.us/img528/screenshotdiskusageanaluk5.png/1/w800.png[/IMG]](http://g.imageshack.us/img528/screenshotdiskusageanaluk5.png/1/)

Hi! Please take a look at the picture above. I installed Ubuntu 8 a couple of days ago. Since then I've installed a few progs from the Package Manager and moved 30-something Gigabytes of mp3 files into the home folder. Which means that 36.2GB is surely correct. Does anyone know why then it says at the top "used: 72.8 GB"?


Also, when I go to System>Administrator>Monitor System, I get told this :
[[IMG]http://img517.imageshack.us/img517/2890/screenshotsystemmonitorvw6.png[/IMG]](http://imageshack.us)
[[IMG]http://img517.imageshack.us/img517/screenshotsystemmonitorvw6.png/1/w215.png[/IMG]](http://g.imageshack.us/img517/screenshotsystemmonitorvw6.png/1/)

Any idea why that is?

Thanks very much!

P.S. I ran DBAN before install so there are no other partitions etc on my hard drive.

---

### Post by ealrgrey on 2008-09-23
Bump.

---

### Post by bumanie on 2008-09-23
look at the output of > df -h / and > df -h /homeThey will give you a better indication of usage than the graphical representation does.

---

### Post by ealrgrey on 2008-09-23
Thanks for the reply bumanie. Unfortunately that's only made things more confusing! This is what I get for df -h / :

me@my-laptop:~$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G   37G   99G  27% /

I should be using my entire hard drive of 200-and-something GB...?

---

### Post by ealrgrey on 2008-09-23
Btw when I do /home I get the exact same answer if that is significant...

me@my-laptop:~$ df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G   37G   99G  27% /
me@my-laptop:~$ df -h /home
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             143G   37G   99G  27% /

---

### Post by bumanie on 2008-09-23
You don't have a separate /home partition that is why / and /home are the same as they are in the same partition, never-the-less it is showing only 27% being used
I'm at a friends at the moment but this is what his output looks like and what I was expecting you would get, but he has a separate / and /home which you don't have.

david@david:~$ df -h /
Filesystem            Size Used Avail Use% Mounted on
/dev/sda2              12G  3.4G  7.2G  32% /
david@david:~$ df -h /home
Filesystem            Size Used Avail Use% Mounted on
/dev/sda3             276G  9.7G  252G   4% /home

Can you post a screeshot of gparted GUI?

---

### Post by ealrgrey on 2008-09-23
Just seen this in System Monitor, is it significant?

[IMG]http://img407.imageshack.us/img407/9653/screenshotsystemmonitorqp9.png[/IMG]

---

### Post by ealrgrey on 2008-09-23
> **bumanie said:**
> You don't have a separate /home partition that is why / and /home are the same as they are in the same partition, never-the-less it is showing only 27% being used

Am I supposed to have a separate partition for /home?

My hard drive is 240-280GB (can't remember) so it should be using a lot less than 27%... I've only put 30-something GB onto it.

---

### Post by bumanie on 2008-09-23
That is consistent with the terminal output. Try to send a screenshot of gparted. > sudo apt-get install gpartedFind gparted under System --> Administration --> Partition Editor. To get a screenshot Applications --> Accessories --> Screenshot and up load the screenshot to the forum.

---

### Post by ealrgrey on 2008-09-23
I've solved the problem, and I'm sorry to say you're not gonna like it. When I saw the 280GB number in the first screenshot my mind accepted as fact that that was correct. Unfortunately however after rummaging around for the paperwork I've discovered that this laptop is only supposed to have 160GB, so it's more or less correct. It is a different laptop that has 200-and-something GB. So yeah there is no problem to solve. Sorry.

Thanks for your help bumanie and sorry for wasting your time.

---

### Post by bumanie on 2008-09-23
Oh, well everyone makes mistakes sometimes. No worries.

---

