---
title: "Proper package description"
date: 2007-11-16
forum: Packaging and Compiling Programs
---

### Post by viraptor on 2007-11-16
Hey
I'd like to ask about description in debian/control.
Let's say I want to open a repo where package XYZ-1.5 is available. There's XYZ-1.1 already available in ubuntu and debian/{control,rules,*} files are usable for the new version.

I'm putting myself in changelog, but should I also change the "Maintainer: Abc D." field?
I'm planning to package future versions in that repo, but would like to use original Ubuntu build scripts as long as possible. I feel it makes sense to change Maintainer, so that guy won't be bothered about my mistakes. On the other hand it's like changing copyrights line (though his credits are still in debian/copyright...).

Ideas? Opinions?
TIA

---

### Post by geraldm on 2007-11-18
Perhaps I am reading into your post what you did not intend...

When you update a package, submit the changes to the package 
maintainer.  This field should not change for any update.  When
a package is forked, as is permissable, then there should be a
maintainer for each branch.  You could include, with the patch,
an offer to maintain, or co-maintain, as you wish.  I think the 
community values having a maintainer, and changing the field 
without the consent and approval of the current maintainer is 
a possible start of a flame war or slight of the maintainer.
The community also places value on cooperation, and finding different
versions of a similar package is frowned upon.  Try to do the best
course, which is to cooperate in development of a unified package,
as long as it can be done.  

Gerald

---

### Post by viraptor on 2007-11-18
What I really intend to do, is give to original maintainer all credit (s)he deserves, but also prevent them for getting reports about my bugs in packaging.
I don't really want to mail every developer, What I intend to open is repository with development / unstable packages - something mostly for developers / someone trying to test new soft. Currently ubuntu is just not very good for developing stuff that will depend on libs available in next release - unless you compile all dependencies yourself. In that case I expect many people bitching about my packages quality :)
So I need to basically fork packaging as new version of soft won't show up in ubuntu for a couple months.
I really wanted to find a way to both give proper credit and prevent people for getting blamed....

---

### Post by dholbach on 2007-11-19
Change the maintainer field, only if you really want to take over maintenance yourself.

On a related note: [https://wiki.ubuntu.com/DebianMaintainerField](https://wiki.ubuntu.com/DebianMaintainerField)

---

