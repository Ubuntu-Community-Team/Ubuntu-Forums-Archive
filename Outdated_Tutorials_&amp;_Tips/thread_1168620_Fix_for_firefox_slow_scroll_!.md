---
title: "Fix for firefox slow scroll !"
date: 2009-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by cdahmedeh on 2009-05-24
Hello,

I've noticed, especially with pages that have Flash applets, that scrolling is very slow and sluggish. I have a found a way to fix this. What we're going to do is replace Flash Player 10 with version 9, which seems to run faster and allows much faster scrolling.

1. Open Synaptic Package Manager from System>Administration
2. Mark flashplugin-nonfree and flashplugin-installer for Removal and press Apply
3. Close Synaptic Package Manager.
4. Open up : [http://packages.ubuntu.com/hardy-updates/flashplugin-nonfree]("http://packages.ubuntu.com/hardy-updates/flashplugin-nonfree")
5. Scroll all the way that page and select i386 or AMD64 depending on your architecture.
6. You should be sent to page with different mirrors, chose anyone and it will download the .deb file for installation package.
7. Make sure you have closed Firefox including the download window.
8. Find the .deb file you downloaded and install it. It's very straightforward, just double-click it and press install package. Ignore the warning that says that there are a newer version available in the repositories.
9. In order to prevent Synaptic from updating back to version 10, open up Synaptic package manager again and look for the flashplugin-nonfree package. 
10. Highlight it (click on it once) and in the Package menu in the menu bar, check Lock Version. Now close Synaptic

Feel free to open firefox and go visit some webpages, even the ones without flash will seem to scroll much faster.

Have and enjoy the tip ! Ask any questions in this topic.

---

### Post by lavinog on 2009-05-24
I wouldn't recomend downgrading flash since there are many security vunerabilities in older versions.

The scrolling issue can be due to other issues.
If flash 9 fixes it, then the problem may be due to your video drivers. If I remember correctly 9 doesn't use hw accelleration while 10 does. If that is the case, have you tried turning off hw accelleration in flash?
Also, if you are using 64bit ubuntu, you might get better performance with the 64bit flash instead of the default 32bit wrapper

---

### Post by Wanas on 2009-05-24
Agree with lavinog
because actually I am using flash 9 in opera and flash 10 in firefox and I think the same performance in the different flash versions

---

### Post by Arup on 2009-05-24
Scrolling issue is nothing to do with flash but a video driver issue. FF creates and loads small pixmaps which earlier nvidia drivers had issues. Check your video card and install the latest drivers for it.

---

