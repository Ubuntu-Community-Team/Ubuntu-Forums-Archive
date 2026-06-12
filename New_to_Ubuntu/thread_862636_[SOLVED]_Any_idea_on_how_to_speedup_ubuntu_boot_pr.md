---
title: "[SOLVED] Any idea on how to speedup ubuntu boot process and other overall tweaks?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by bhadotia on 2008-07-17
I was  reading a magazine article at the hostel at a friend's room about 'how to speed up linux(part 1): installing linux the smart way' (the title is not exact- can't recall properly:)). There I found many good tips on how to speed up ubuntu (as ubuntu was the chosen example distro in that article). Unfortunately, I did not take my laptop to the hostel this time. And now I am at home and also forgot to borrow that magazine from my friend . I tried some google search but all the articles (mainly forum threads ) I came across were outdated (dated around 2005).

I can remember some parts of that article and I would repeat them out here. I would be highly thankful if someone can kindly complete/correct them:

1. The first tip was to use the "noatime" (correct me if the name is wrong) option for the partitions in the fstab (actually ,this option was selected when preparing the partitions for the install in that article). This option, as I can remember , disables logging of the file access instances (or something like that). I these are mainly redundant for the common user and thus this saves disk space. I just need to know can "noatime" (please correct the name if wrong)and "relatime" be placed simultaneously in /etc/fstab.
2. Another tip which I found worth trying was related to speeding up boot process. Ubuntu (initramfs- I think- can't remember) by default assumes the processor to be single core. If we have a multi-core/hyperthreading processor ,than the speed of the boot process can be increased drastically. Now, we need to edit a file to let ubuntu know that we use a multi-core/hyperthreading processor, but the problem is, I have completely lost the idea of what the name of the file is:).


Other tweaks I  remember and have already applied include: Disabling services which we don't use in System>Administration>Services (blue-tooth and printer in my case); and Disabling unnecessary desktop effects (water effect, fire effect, 3D windows etc.).


All help will be highly appreciated.
Many thanks in advance.

---

### Post by oldsoundguy on 2008-07-17
Eliminating most of the splash screens (except the sign in) is another tweak.  But the biggest is a nice fast processor with a fast FSB, lots of memory and a nice big and fast hard drive.

You can also go to all of your menus on the top line and decide what you are using and what you will never use.  Using add/remove or Synaptic Package Manager, you can remove or un-check the items and they will not load.  You can ALWAYS go back and re-install if need be.

---

### Post by carandraug on 2008-07-17
For tweaking more than speeding up, give "[Ubuntu tweak]("http://ubuntu-tweak.com/downloads")" a go. I found it very useful. It's not in the repositories, just follow the link.

---

### Post by bhadotia on 2008-07-17
Thanks for the reply guys . But I would appreciate if someone would be nice enough to complete the above incomplete tweaks rather than give more tweaking suggestion- let us take one thing at a time(Of-course, I can always go and buy the magazine but why waste money if I already have a copy at the hostel with a friend).

---

### Post by nowshining on 2008-07-17
example for attime and relatime
```

/dev/sdb1 /media/disk auto nouser,noatime,relatime,noauto,rw,nodev,noexec,nosuid 0 0
```

---

### Post by bhadotia on 2008-07-17
> **nowshining said:**
> example for attime and relatime
```

/dev/sdb1 /media/disk auto nouser,noatime,relatime,noauto,rw,nodev,noexec,nosuid 0 0
```
Whats attime?

---

### Post by nowshining on 2008-07-17
it's the same at relatime but an older one - ie: timestamps - relatime has performance increases over attime..

---

### Post by bhadotia on 2008-07-17
> **nowshining said:**
> it's the same at relatime but an older one - ie: timestamps - relatime has performance increases over attime..

Ok, so I can use relatime along with noatime as a mount option in fstab, correct?
And this will disable the time stamp or whatever and save a little disk space?

---

### Post by nowshining on 2008-07-17
no it will not disable attime but replace it so u can keep the timestamps but not have the performance hit as attime.

As for the space - it just updates the times on files, etc..that's what attime does everytime you access a file..

---

### Post by bhadotia on 2008-07-17
> **nowshining said:**
> no it will not disable attime but replace it so u can keep the timestamps but not have the performance hit as attime.

As for the space - it just updates the times on files, etc..that's what attime does everytime you access a file..
K....


Any suggestions on which file needs to be edited to tell ubuntu to use dual-core cpu on start-up and thus decrease start-up time?

---

### Post by bhadotia on 2008-07-17
[SIZE=4][/SIZE]The name of the article is:Optimising Performance on Linux Desktops—Part 1 Install Linux the Smart Way!
And the magazine is:LINUX for you **(July  2008**   **Issue                                           Vol. 6  No. 5)**

So has any one got it?

---

### Post by nowshining on 2008-07-17
nope sorry, all I know is that you can compile ur own custom kernel from kernel.org and optimize it for your CPU only, etc.. 

for the concurrent boot thing - i don't remember what file - sorry. :/ however if you search on the forums u should find out how to do that..

---

### Post by bhadotia on 2008-07-17
Ok.. thanks for the reply.

I will now try searching the forum (Heck.. why didn't I think of that earlier!:))

---

### Post by nowshining on 2008-07-17
hehe, ur welcome:
> 
Ok.. thanks for the reply.

I will now try searching the forum (Heck.. why didn't I think of that earlier!)

---

### Post by seagullplayer77 on 2008-07-17
There's a utility called Prefetch, and that'll speed up your machine some. I think you can install it through Synaptic if you add the repo for it...Anyway, it makes a list of the most commonly used programs and processes and it'll take a few seconds off the startup times for the stored applications. I don't really think it makes the machine boot any faster, but it runs a little quicker once you're logged in. I've been using it for a few months and I've never had a problem.

---

### Post by bhadotia on 2008-07-17
> **seagullplayer77 said:**
> There's a utility called Prefetch, and that'll speed up your machine some. I think you can install it through Synaptic if you add the repo for it...Anyway, it makes a list of the most commonly used programs and processes and it'll take a few seconds off the startup times for the stored applications. I don't really think it makes the machine boot any faster, but it runs a little quicker once you're logged in. I've been using it for a few months and I've never had a problem.
I also have something similar - its called 'preload' and its in the repos.

---

### Post by oldos2er on 2008-07-18
You might be thinking of this:

 "Concurrency is another tweak should speed things up, although at 1Ghz the change was minor. However, this is one setting where faster machines might see an improvement as well.
 
 The tradeoff for speed is a slightly less organized boot sequence, particularly if you remove the "quiet" flag from your Grub kernel boot line. It's a very small sacrifice, really.
 
 The concurrency variable is inside /etc/init.d/rc. Edit that file like this:
 
sudo nano -w /etc/init.d/rc

 Find the CONCURRENCY variable and set it to "shell", like this:
 
CONCURRENCY=shell

 You should see a solid improvement in start times now. For more information about that variable, try ...
 
[http://ubuntuforums.org/showthread.php?t=292961](http://ubuntuforums.org/showthread.php?t=292961)
 http://www.debian-administration.org/articles/199"

---

### Post by bhadotia on 2008-07-18
> **oldos2er said:**
> You might be thinking of this:

 "Concurrency is another tweak should speed things up, although at 1Ghz the change was minor. However, this is one setting where faster machines might see an improvement as well.
 
 The tradeoff for speed is a slightly less organized boot sequence, particularly if you remove the "quiet" flag from your Grub kernel boot line. It's a very small sacrifice, really.
 
 The concurrency variable is inside /etc/init.d/rc. Edit that file like this:
 
sudo nano -w /etc/init.d/rc

 Find the CONCURRENCY variable and set it to "shell", like this:
 
CONCURRENCY=shell

 You should see a solid improvement in start times now. For more information about that variable, try ...
 
[http://ubuntuforums.org/showthread.php?t=292961](http://ubuntuforums.org/showthread.php?t=292961)
 http://www.debian-administration.org/articles/199"
Thanks this is just what I was looking for - that article gave the exact same thing.
Cheers!:)

---

