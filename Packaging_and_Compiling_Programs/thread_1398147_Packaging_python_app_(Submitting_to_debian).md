---
title: "Packaging python app (Submitting to debian?)"
date: 2010-02-04
forum: Packaging and Compiling Programs
---

### Post by J V on 2010-02-04
I have a small python app I would like to package (rpm & deb would be nice)

I also would like to submit to debian (Will automatically trickle to buntu repos)

Problem is, all the guides I can see make things so frikkin hard lol :P

I have a folder with files in it, they go in (I presume) /usr/share/myAppName and then add a menu item.

How hard is that? It would probably be easier to compile a C app to do it for me pfft...

Is there any software that makes packaging easy? Any guides that take out the unpleasantness?

---

### Post by SevenMachines on 2010-02-05
hi there, the best tutorial for python packaging is probably the [ubuntu packaging guide - python.]("https://wiki.ubuntu.com/PackagingGuide/Python")
theres was also a recent [developer week session]("https://wiki.ubuntu.com/MeetingLogs/devweek1001/PyAppsPkgs"), which might be worth a look. once the basic control files and rules files (using cdbs and debhelper) mentioned there are set up it should be fairly straightforward to do what your looking for. good luck!

---

### Post by zubin71 on 2010-04-03
yes, i too recommend checking out distutils. However distutils currently lacks the --uninstall feature; that is being worked on under the namespace "distutils2" which should be out soon.

Until then, use distutils.

---

