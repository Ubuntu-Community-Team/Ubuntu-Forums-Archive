---
title: "PDF font problems how can I fix it?"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by jingo811 on 2008-05-20
On Debian a PDF's fonts look a certain way but when you open the same PDF on another distro like Ubuntu then the text compresses itself so noone can read it smoothly.  Well it's not Ubuntu specific the same problem can occur when looking at a working PDF on Ubuntu.  And then trying to look at the same PDF on another distro.
Like this:
**Scalix Installation Guide - Version 11.3** 
[http://www.scalix.com/community/downloads/documentation.php](http://www.scalix.com/community/downloads/documentation.php)
[IMG]http://i30.tinypic.com/1447gwm.png[/IMG]

What's the proper way to fix font problems like this?  How can I know which font is missing?  Is there some Standard-apt-get-Fonts-package out there that can fix this sort of annoying effects easily?

---

### Post by Mark_in_Hollywood on 2008-05-20
Disclaimer: I don't have this problem, but googling for:

adobe reader font fixes

I found:

#1572280 Type 3 fonts with missing operators.

at the Adobe site:

[http://kb.adobe.com/selfservice/viewContent.do?externalId=kb402673](http://kb.adobe.com/selfservice/viewContent.do?externalId=kb402673)

May I suggest that this is more an Adobe problem than an Ubuntu problem. I'm glad to help our community, but I'm really just guessing about your problem.

---

### Post by jingo811 on 2008-05-20
Yeah I asked a similar question initially at a SuSE forum and according to a response I got I'm missing these fonts.  But now I multi-booted into my main OS Ubuntu and I can't seem to find any of those fonts when I do "apt-cache search ***SomeFont".  Since that SuSE guy said he could watch my PDF example with these fonts without problem.  While my SuSE distro couldn't display that PDF correctly.

xorg-x11-fonts
ghostscript-fonts-std
ghostscript-fonts-other
agfa-fonts

Since the SuSE guy told me that this was a common Linux problem no matter which distro you used.  I thought maybe Ubuntu had some Font-fixer-upper-package-for-PDF-problems that you could download via apt-get.
So is there such a package for Ubuntu?

---

### Post by Dougie187 on 2008-05-20
As with the other guy. I really have no idea as to your issue. But you can try doing the package msttcorefonts
I have no idea if that will help, but it might.

---

