---
title: "Packaging Notalon as a DEB file?"
date: 2009-08-06
forum: Packaging and Compiling Programs
---

### Post by catechu on 2009-08-06
Hi all,

I've developed Notalon, a free and open-source note-taking application ([http://notalon.org](http://notalon.org)). I've been using it on Ubuntu.

I came across the "[Debian New Maintainers' Guide]("http://www.debian.org/doc/maint-guide/ch-start.en.html")," but I wasn't able to figure out how to properly make a DEB file from those instructions. Searching around hasn't yielded anything much clearer to me either.

So I have two questions:

[LIST=1]
[*]Is there a minimal guide for creating a DEB package? (Also, if someone is willing to help me out with packaging this, that would be great!)
[*]After doing so, how can I submit Notalon to be in a Debian/Ubuntu repository?
[/LIST]
I appreciate all pointers and offers to help. Thanks, everyone!

---

### Post by Leslie Viljoen on 2009-08-06
1.
Basic: [http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

Here's how to modify an existing package - also good for learning:
[http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-6-sect-10.html](http://book.opensourceproject.org.cn/distrib/ubuntu/hacks/opensource/0596527209/i-0596527209-chp-6-sect-10.html)

2.
You need to join the Ubuntu MOTU group and become an apprentice packager, or get a MOTU to adopt your package. See: [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)
Probably the latter.

---

### Post by catechu on 2009-08-06
Thank you for those guides, Leslie!

I am confused because my application has resources (e.g. icons, config file), and it's not clear from these guides how best to include those. How can I do this?

---

### Post by chaosrl on 2009-09-29
Hey, any word on this? I can't seem to get Notalon up and running on Jaunty, something about "No module named agw.flatmenu." I'm really interested in seeing what this is like, thanks!

---

### Post by catechu on 2009-09-29
chaosrl, you need the latest version of wxPython for Ubuntu, then that error will go away.

I'm still figuring out how to develop the DEB file -- if anyone who has experience with this is willing to help me out, I'd be grateful!

---

### Post by dinxter on 2009-09-30
maybe the tutorial specific to python will help
[https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)
I dont have much knowledge in the python area myself, but with a Makefile it should be as simple as running dh_make inside the source dir, removing the unneeded files in debian/ (dh_make creates examples you might not need for a simple package) and edit debian/control to add build/run dependencies, dch -i to update the changelog, and check your debian/copyright. using pbuilder to check that your package dependencies are good on a default system is also a good idea
The rest of the ubuntu packaging guide really is a useful read too, not just for python apps :)

---

