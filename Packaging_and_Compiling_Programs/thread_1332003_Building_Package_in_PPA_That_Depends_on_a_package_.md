---
title: "Building Package in PPA That Depends on a package Another PPA"
date: 2009-11-19
forum: Packaging and Compiling Programs
---

### Post by roadkillbunny on 2009-11-19
Hi there,

I am trying to publish a python script that rotates the screen of a tablet based on the orientation of the tablet. To do this, I use xrandr, or to be more specific the python bindings called python-xrandr. But this package is only available inside the [Displayconfig-gtk](https://launchpad.net/~displayconfig-gtk/+archive/ppa) PPA.

After I install python-xandr on my laptop, I can build a deb package successfully. However when I upload the source to the PPA that I want to use to publish this ([ppa:kkrizka/thinkpad-x61t](https://launchpad.net/~kkrizka/+archive/thinkpad-x61t)), and add the Displayconfig-gtk PPA as a dependency.

But the build fails with the following error ([buildlog]("https://launchpad.net/~kkrizka/+archive/thinkpad-x61t/+build/1353660/+files/buildlog_ubuntu-karmic-i386.autorotate_0.3_MANUALDEPWAIT.txt.gz")):
```

Build status
Dependency wait on thallium (virtual) Retry this build

    * Missing build dependencies: python-xrandr 
```

This is my first time trying to distribute a deb using a PPA, so I'm not sure if there is a way to handle such external dependencies.

---

### Post by SevenMachines on 2009-11-20
if you go the page of your ppa theres an 'edit ppa dependencies' entry at the top right where you can choose the ubuntu repositories and add ppa repositories too. i remember having this problem before and not being able to do this so i'm guessing this is relatively new, or i was previously blind to it :)

---

### Post by roadkillbunny on 2009-11-20
> **SevenMachines said:**
> if you go the page of your ppa theres an 'edit ppa dependencies' entry at the top right where you can choose the ubuntu repositories and add ppa repositories too. i remember having this problem before and not being able to do this so i'm guessing this is relatively new, or i was previously blind to it :)

I've added the Displayconfig-gtk PPA before I uploaded my package, so it's either not working or it doesn't do anything other than display a message to others that try to add it to their sources.list.

---

### Post by SevenMachines on 2009-11-20
displayconfig is gutsy whereas your repository is karmic, i imagine thats the problem. you might be better importing displayconfig into your ppa since its quite old

---

### Post by roadkillbunny on 2009-11-21
> **SevenMachines said:**
> displayconfig is gutsy whereas your repository is karmic, i imagine thats the problem. you might be better importing displayconfig into your ppa since its quite old

That does seem to have been the problem. The python-xrander package works perfectly on karmic, even though it was packaged for gutsy. But it seems that the launchpad PPA dependency requires that the release be explicitly for karmic. 

I did a quick test. I've added a random PPA that has a karmic release (banshee-unstable), and tried to rebuild my package. The buildlog shows that it did contact the banshee-unstable's karmic section.

I'll try to contact the maintainer of the python-xrandr package to see if he is planning to update his PPA to karmic. If not, then I'll probably fall back to uploading it myself.

Thank you for your help.

---

