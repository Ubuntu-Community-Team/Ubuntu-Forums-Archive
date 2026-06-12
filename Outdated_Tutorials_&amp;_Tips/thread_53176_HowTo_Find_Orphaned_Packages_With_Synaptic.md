---
title: "HowTo: Find Orphaned Packages With Synaptic"
date: 2005-07-30
forum: Outdated Tutorials &amp; Tips
---

### Post by Xian on 2005-07-30
Your Ubuntu installation will accumulate packages over time that are no longer required. Usually this occurs because they have been pulled into the system so as to satisfy the dependency requirements of other software that has since been removed. When using Apt and/or Synaptic (the default Ubuntu package manager), these dependent packages don't get uninstalled during the normal process of removing the parent package.

This is one method in which to find and remove orphaned packages from your system. It is notably easy since you will be using the Synaptic package manager, which is a tool that most people are already familiar with and use regularly. 

Please note that orphaned packages cause no harm and can be left installed with no ill effects. The primary reason to remove them is just to make your system leaner, and for anyone that simply doesn't want installed packages which may no longer serve any purpose.

It is important _not_ to remove any orphaned packages that you might feel to be erroneously reported. The process and results are relatively safe, but obviously the results can not be taken for granted and should always be viewed with some level of scrutiny.

1. Enable the [Extra Repos](http://ubuntuguide.org/#extrarepositories)

2. Install deborphan
```
 $ sudo apt-get install deborphan
```
3. Open Synaptic and click the 'Custom' button in the lower-left corner.
You should already see sections such as 'Broken' and 'Marked Changes'.

4. From Synaptic's main menu choose Settings > Filters
It should look similar to this:


[img]http://img.photobucket.com/albums/v469/camplear/forums/synaptic70b.png[/img]


5. Click on the 'New' button. 
In the Dialogue box type in 'Orphaned' in place of 'New Filter 1'
This will name the filter (choose any name you prefer).

6. Click the 'Deselect All' box then tick the 'Orphaned' box.
It should look similar to this:


[img]http://img.photobucket.com/albums/v469/camplear/forums/synaptic71b.png[/img]


7. Click 'Okay'

8. Highlight the 'Orphaned' option and view the selected packages.
Choose any/all of them and 'Mark For Removal' with right-click.


It should look similar to this:


[img]http://img.photobucket.com/albums/v469/camplear/forums/synaptic72b.png[/img]

---

### Post by autocrosser on 2005-07-30
I think I've got it set up right, but no pictures are coming thru--could you edit or repost them?

---

### Post by Xian on 2005-07-30
They are .png files and I can see them fine in Opera and Firefox.

If you are having difficulty just download these links to your desktop.
Then open them in an image viewer like Gimp.

[Image 1](http://img.photobucket.com/albums/v469/camplear/forums/synaptic70b.png)
[Image 2](http://img.photobucket.com/albums/v469/camplear/forums/synaptic71b.png)
[Image 3](http://img.photobucket.com/albums/v469/camplear/forums/synaptic72b.png)

---

### Post by autocrosser on 2005-07-31
THANK YOU--I'd done it correctly, but it is nice to see it--Funny-I've got the current version of Firefox & could not see the images---

---

### Post by bored2k on 2005-07-31
Very nice tricks. Eases deborphan by a _bunch_ . Cheers.

---

### Post by Spudgun on 2005-07-31
Great HowTo, maked Deborphan nice and easy to use. :D

---

### Post by ubuntp on 2005-07-31
You may also want to check for orphaned packages a few times in a row, because sometimes removing orphaned packages will cause other packages to become orphaned. It once took deborphan 4 runs until all orphaned packages were resolved.

---

### Post by lol on 2005-07-31
[QUOTE=][/QUOTE]
 For those who are not using synaptic (or who cannot), don't forget "orphaner". It's a small but handy console front end to deborphan (installed with deborphan, so you probably have it)...

---

### Post by dolphinsonar on 2007-03-14
This seems like a really core function for an operating system, are there any movements to get it integrated into synaptic?

This post was 2005, maybe it already happened?  At any rate, nice work on cutting the system bloat!

---

### Post by Endolith on 2010-07-03
> **dolphinsonar said:**
> This seems like a really core function for an operating system, are there any movements to get it integrated into synaptic?

This post was 2005, maybe it already happened?  At any rate, nice work on cutting the system bloat!
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/17297](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/17297)

---

