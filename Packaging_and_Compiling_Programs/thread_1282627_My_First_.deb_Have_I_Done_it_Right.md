---
title: "My First .deb: Have I Done it Right?"
date: 2009-10-04
forum: Packaging and Compiling Programs
---

### Post by Penguin Guy on 2009-10-04
I just turned an icon theme called [Mashup]("http://www.gnome-look.org/content/show.php?content=86452") into a .deb. It installs fine but I just wanted to check that I hadn't done anything stupid that's going to be a pain later. I'd be grateful if somebody could just take a look at it and tell me if it's okay or not: [Mashup-1_1.7.deb]("http://dl.getdropbox.com/u/1217030/mashup-1_1.7.deb"). Also - is it okay to upload this to launchpad even if the upstream developer doesn't use launchpad?

---

### Post by Hreinsi on 2009-10-04
Im using it on karmic looks great think i will keep on using it.Thanks

---

### Post by SuperSonic4 on 2009-10-04
Wouldn't you have to change the name or credit the original copyright holder?

---

### Post by dinxter on 2009-10-05
you should probably post links to the diff.gz, .dsc and orig.tar.gz files, its difficult to look at a package on the basis of a pre-built deb. You can also get a good example of a textbook package by looking at hello (yes, the hello package is there for a reason!) 
$apt-get source hello

One thing though, I would highly recommend never to use your own licence unless you really know what your doing and you have an exceptional reason not to use a well known and approved licence. There is a good overview of licences  at the [Open Source Initiative]("http://www.opensource.org/licenses/category"). in particular you should check to see if one of the licences in the 'popular and widely used' category is suitable. By the sounds of it you may want the Lesser GPL, specifically created for those who find the gpl too restrictive

[EDIT] sorry, no sudo needed to apt-get source so removed it

---

### Post by Penguin Guy on 2009-10-05
> **SuperSonic4 said:**
> Wouldn't you have to change the name or credit the original copyright holder?

I did that in [COLOR="Green"]/usr/share/doc/mashup/COPYING[/COLOR]. Was I supposed to put it somewhere else?

> **dinxter said:**
> you should probably post links to the diff.gz, .dsc and orig.tar.gz files, its difficult to look at a package on the basis of a pre-built deb.
There were none of those files. I just used [COLOR="Green"]dpkg -b mashup-1_1.7 mashup1_1.7.deb[/COLOR], mashup-1_1.7 was a folder containing the files [COLOR="Green"]DEBIAN[/COLOR] and [COLOR="Green"]usr[/COLOR].

> **dinxter said:**
> One thing though, I would highly recommend never to use your own licence unless you really know what your doing and you have an exceptional reason not to use a well known and approved licence. There is a good overview of licences  at the [Open Source Initiative]("http://www.opensource.org/licenses/category"). in particular you should check to see if one of the licences in the 'popular and widely used' category is suitable. By the sounds of it you may want the Lesser GPL, specifically created for those who find the gpl too restrictive
Even the LGPL is too restrictive for me, I am looking for a license that allows people to do anything they want. I looked at the WTFPL, but though it seemed a bit unprofessional, so made my own.

---

