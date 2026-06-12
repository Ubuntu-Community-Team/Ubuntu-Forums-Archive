---
title: "The Difference between .deb and .rpm."
date: 2012-05-26
forum: New to Ubuntu
---

### Post by EpicFlyingCoffee on 2012-05-26
(I Hope this goes here)

So...Technically, there is a division between the Linux Community.  Aren't there two types of executable files?

I would like to know if I got this correct:
.deb =  I know that this relates to something like Debian based OSes
.rpm = I remember this mentioned something about Red Hat or Slackware or whatever.

I'd also like to know the differences between the two, as I'm trying to learn more about Linux in General.

---

### Post by agillator on 2012-05-26
Deb files are installation files for debian based distributions. Rpm files are installation files for Red Hat based distributions. There are other types for other distributions. Each is slightly different from the other. All are designed to make the installation of programs easier on the various distributions. None are executable files. Deb files are used with dpkg, aptitude, apt-get. Rpm files are used with yum.

---

### Post by JKyleOKC on 2012-05-26
Both these groups are "package managers" which greatly simplify the process of installing, updating, otherwise maintaining, and removing software. The "deb" files are for use by the "dpkg" utility that originated with the Debian distro (of which Ubuntu is a variant) and the "rpm" files are for the RedHat Package Manager, a similar but very different utility that originated with the Red Hat distribution.

Before package managers came into use, installing a new piece of software was a complicated process that turned off many non-geeks. You had to locate its source code, then compile and link that source into an executable binary file. The first attempt to do so usually resulted in a long string of error messages about missing library files -- for which you had to search, install, and repeat the process.

The package manager utilities made it possible to list all these "dependencies" within a single file that also included a description, and the ready-to-run binary program file. The package manager takes care of fetching all the needed dependencies, and also handles initial configuration of the new software.

While the two different types of manager do essentially the same job, their files are not directly interchangeable. A utility does exist for converting RPM files into the DEB format, but there's no guarantee that a converted RPM file will automatically configure things properly for the Debian standards of file location (which differ significantly, in some respects, from those of Red Hat and its descendants).

I hope this helps a bit; not all distributions use package managers, so if you want to learn more about the "old ways" you can try things like Slackware or GenToo! That may tell you more than you'll be comfortable learning :lolflag:

---

### Post by mapes12 on 2012-05-26
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by EpicFlyingCoffee on 2012-05-26
Wow, thanks a lot!
I guess I know the difference now!
Thanks.

---

### Post by gamblor01 on 2012-05-26
You're still welcome to build programs from source on Ubuntu (or any other Linux distribution).  However, it is highly recommended to install a binary version (one that was already built) instead.  When installing packages via the package management system, the distribution will not only handle dependencies for you, but it can automatically alert you when there are updates.  If you build from source then you will be stuck with that same version until you manually go out, download the update, and then it again.  Having an old version can mean that you are lacking new features and/or missing updates to plug security vulnerabilities, etc.

There are times were binary packages are not available and you must build from source...or maybe you wish to modify some source code to make it work the way you want.  For this reason, I recommend that you install the "build-essential" package right now (if you have the free hard drive space).  It's probably only going to pull a couple hundred megabytes of stuff but it could prove to be insanely useful in the future.  Just open a terminal and run:

```
sudo apt-get install build-essential
```

---

### Post by andrew.46 on 2012-05-27
> **EpicFlyingCoffee said:**
> .rpm = I remember this mentioned something about Red Hat or Slackware or whatever.

Slackware actually uses tgz files, which are simply gzipped tar archives, that are installed with *installpkg *and removed with *removepkg*.

---

### Post by afz12 on 2012-05-27
Whether my comments are appropriate may be debatable I guess, but I would hope that people distributing Linux software should adopt a simple format - after all not everyone wants to be a Linux geek. I like the concept but in no way do I want to be a Linux guru - I just want tools that do as they pretend to action. The .deb format seems most convenient, .rpm will be a mission and man do I hate .tars. Also, .sh never works - BOINC is an obvious proof of this. I get replies such as "it works fine on my PC" - so what - I don't care, it doesn't work on mine so go away! 

Given that Ubuntu has tried to bridge the gap between "real population" and "software oriented geeks" - not that I dismiss geeks in any way; I admire them - surely we can offload some of this retrograde packaging garbage in favour of transfers that can "just be installed and work"!

Ubuntu is the best candidate in this - Fedora is still ruled by "druids" and I have never gotten any distribution to actually "work" - dissmissable +++. Debian is better, but Ubuntu is better as a candidate OS for the masses (as physiologically we are all pretty much the same). So why cling to druid oriented unfriendly file formats - why not select a convenient version and promote this. Many bolts from the past may be historically interesting but not of immediate applicational advantage. There is nothing wrong with Windows "1 PC in every home ambition" - despite all detractors, Gates was right on with this. Accessibility should always be paramount to any Linux distribution, holy grail druids have no position in our current world and requiring specialist knowledge to use something that is a tool just as a hammer, a screw driver, a hair comb or a toothbrush is a tool, as well as money is just a tool, ant s/w on offer should be usable immediately if it is well designed. For example, we turn water taps "off" to the right as this shuts down the flow. We associate right turns to "action", and we in many cases have commonly expected expectations of what natural responses should mean (red=danger, blood?) so software should be exactly consistent. 

Incompatible software, with our psychology, demands unwanted learning expense, contributes to errors and overall, degrades subjective appreciation. I hope Ubuntu (its proponents do a great job despite very constrained resources) can find ways to incrementally bridge the gap between general public expectations and actual interaction to each O.S. The solution is not to expect the general public to be robotic Linux druid geeks but to invite the general public into greater over-arching issues regarding software freedoms. unconstrained distribution and pro-social initiatives.

---

