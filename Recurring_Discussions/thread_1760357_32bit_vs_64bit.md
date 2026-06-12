---
title: "32bit vs 64bit"
date: 2011-05-16
forum: Recurring Discussions
---

### Post by chikara99 on 2011-05-16
I have many thought about using 64bit ubuntu but don't know if there is any difference to the packages that can be installed, is it worth under powering my system capabilities, and even what kinds of problems do 64bit users face over 32bit. 

I have a Alienware m11x R2 with an i7, 8GB of Ram and want to install ubuntu, what would be the best version to install.

---

### Post by tgm4883 on 2011-05-16
> **chikara99 said:**
> I have many thought about using 64bit ubuntu but don't know if there is any difference to the packages that can be installed, is it worth under powering my system capabilities, and even what kinds of problems do 64bit users face over 32bit. 

I have a Alienware m11x R2 with an i7, 8GB of Ram and want to install ubuntu, what would be the best version to install.

Install 64-bit. You have the hardware, so why wouldn't you?

---

### Post by chikara99 on 2011-05-28
11.04 64bit didn't install right keeps restarting. 10.04 64bit seem stable without sound though

---

### Post by linuxinstalledfromhdd on 2011-05-28
[s]The last couple of Ubuntu releases they warned users about installing 64-bit versions due to instability.  At this point I would probably continue with that line of thinking as well..  And I haven't heard them say that it is a completely "stable" yet.[/s]

You can install a PAE kernel after you have installed a 32-bit version if you are worried that you will not be able to use all of your RAM memory sticks that you have installed on your system.   

Also there are closed-source driver packages (for printers, etc) that are only completely functional in a 32-bit OS and only come in 32-bit deb packages.. It would completely depend on the manufacture of your system's components. And you would want to research that on their driver download pages to see what exists for Linux. 

hope that helps:)

---

### Post by chikara99 on 2011-05-28
would i get full use of my quad core on a 32bit os.

---

### Post by linuxinstalledfromhdd on 2011-05-28
[s]do you want an unstable system? or you do want something that runs correctly?[/s]

---

### Post by tgm4883 on 2011-05-28
> **linuxinstalledfromhdd said:**
> do you want an unstable system? or you do want something that runs correctly?

> **linuxinstalledfromhdd said:**
> The last couple of Ubuntu releases they warned users about installing 64-bit versions due to instability.  At this point I would probably continue with that line of thinking as well..  And I haven't heard them say that it is a completely "stable" yet. 

You can install a PAE kernel after you have installed a 32-bit version if you are worried that you will not be able to use all of your RAM memory sticks that you have installed on your system.   

Also there are closed-source driver packages (for printers, etc) that are only completely functional in a 32-bit OS and only come in 32-bit deb packages.. It would completely depend on the manufacture of your system's components. And you would want to research that on their driver download pages to see what exists for Linux. 

hope that helps:)

Please stop spreading FUD. Show me where they have warned users away from running a 64-bit OS. I run 64-bit OS's on all my PC's that support it just fine.

---

### Post by linuxinstalledfromhdd on 2011-05-28
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

What does that dropdown say?

That's right...

"32-bit Recommended".  

Now try selecting the 64-bit version. 

The 64-bit doesn't say recommended. 

How much more do you need than that?

My suggestion would be asking the administrator for that page or the Ubuntu developer who made that "recommendation". :)

---

### Post by 3rdalbum on 2011-05-28
> **linuxinstalledfromhdd said:**
> [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

What does that dropdown say?

That's right...

"32-bit Recommended".  

Now try selecting the 64-bit version. 

The 64-bit doesn't say recommended. 

How much more do you need than that?

My suggestion would be asking the administrator for that page or the Ubuntu developer who made that "recommendation". :)

It's "recommended" only because some people don't know what the difference is between 32-bit and 64-bit, and there are still computers being sold that only have 32-bit CPUs. 32-bit operating systems work on 64-bit CPUs but not vice-versa.

64-bit Ubuntu is fully supported and there is no "stability" difference - the only difference in the binaries is the length of numbers used internally, and there's no difference in the source code. There are pretty much no bugs in the 64-bit edition that are not also present in the 32-bit edition.

---

### Post by tgm4883 on 2011-05-28
> **linuxinstalledfromhdd said:**
> [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

What does that dropdown say?

That's right...

"32-bit Recommended".  

Now try selecting the 64-bit version. 

The 64-bit doesn't say recommended. 

How much more do you need than that?

My suggestion would be asking the administrator for that page or the Ubuntu developer who made that "recommendation". :)

Hmm, it does say recommended. Let me stick that into Python.

```
#!/usr/bin/env python

if "Recommended" == "Warning":
  print "True"
else:
  print "False"
```


Odd, that printed false. That must mean that Recommended and Warning do **_not_** mean the same thing. Perhaps Canonical is recommending people to use the 32-bit version not because the 64-bit version is unstable (seems quite stable to me \\:D/ ) but instead because some people don't know what processor they have and the 32-bit version should run on either type. :-k

---

### Post by wolfen69 on 2011-05-29
It's bad enough people argue over desktop environments, is this really necessary?

For the record, I've been using 64bit OS's for 2 years without a single hitch.

---

### Post by tgm4883 on 2011-05-29
> **wolfen69 said:**
> It's bad enough people argue over desktop environments, is this really necessary?

For the record, I've been using 64bit OS's for 2 years without a single hitch.

Theres a difference between arguing about the desktop environment (which tends to be a subjective argument) and arguing about the technical merits of an architecture and pre-conceived notions of it's failings.

---

### Post by oldos2er on 2011-05-29
> **linuxinstalledfromhdd said:**
> [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

What does that dropdown say?

That's right...

"32-bit Recommended".  

Now try selecting the 64-bit version. 

The 64-bit doesn't say recommended. 

How much more do you need than that?

My suggestion would be asking the administrator for that page or the Ubuntu developer who made that "recommendation". :)

It's been done: [https://bugs.launchpad.net/ubuntu-website-content/+bug/585940](https://bugs.launchpad.net/ubuntu-website-content/+bug/585940)

It was the "website team" who decided this, not developers.

---

### Post by oldfred on 2011-05-29
Back in 2009 the benchmarks showed 64bit better and newer benchmarks confirm it.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
Advantages and Disadvantages of 64bit. (Plus install Guides) from 2008
[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)
Benchmarks Performance on 9.04
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by chikara99 on 2011-05-31
If you read some of the projectsite their packages for 64bit (10.04 and 11.04)say they are not stable. the other reason i switch back to 32bit because there is a better pool of support than there is for 64bit systems. I'm still having problems with my audio that i can't fix even following some of the tutorials that ppl posted.

---

### Post by lister king of smeg on 2011-05-31
i have used 64bit Ubuntu for my main computer since switching from windows and have never had a problem that is not also present in the 32 bit version. also if you want to take advantage of all you memory you will want 64 bit, and as for applications you could always compile the source code.

---

### Post by PhillyPhil on 2011-05-31
> **chikara99 said:**
> would i get full use of my quad core on a 32bit os.

No. Your CPU is 64 bit.  If you use a 32 bit OS you are reducing it's maximum possible performance.

I don't quite understand what happened in this thread re. linuxinstalledfromhdd's posts, but please don't believe him if he is saying 64 bit is less stable, or that that was why the website recommended 32 bit.

If you're using 64 bit, make sure you use 64 bit flash.

---

### Post by FlameReaper on 2011-05-31
> **chikara99 said:**
> I have many thought about using 64bit ubuntu but don't know if there is any difference to the packages that can be installed, is it worth under powering my system capabilities, and even what kinds of problems do 64bit users face over 32bit. 

I have a Alienware m11x R2 with an i7, 8GB of Ram and want to install ubuntu, what would be the best version to install.

You're far more than just able to run a 64-bit OS. Actually, you'll want it instead seeing the amount of RAM you have installed.

I'm running Natty Narwhal 64-bit, and in a laptop with i7, 4GB of RAM, and have 1GB of VRAM on Mobility Radeon HD5470.

Just go ahead and do it.

[This]("http://www.phoronix.com/vr.php?view=8325") might help you get at least a rough idea on the difference.

---

### Post by chikara99 on 2011-06-09
once i figure out what the problem is i'll try 64bit again. though my system hangs on 11.04 64bit (regular and alternative isntall) and then restarts. i'll just stick with 10.04 since its on LTS and it actually loads.

---

### Post by BicyclerBoy on 2011-06-09
You biggest problem is that your h/w is using optimus graphics not 32bit or 64bit. (but go 64bit)

Check out bumblebee and/or vgaswitcharoo projects..

[http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html](http://linux-hybrid-graphics.blogspot.com/2010/10/howto-allienware-m11x-r2-nvidia-optimus.html)

This link is a bit out of date so check out
[https://github.com/z0rc/debumblebee](https://github.com/z0rc/debumblebee)

---

### Post by weasel fierce on 2011-06-10
Ive been running 64 bit for 3 years or so, and its working great.

---

