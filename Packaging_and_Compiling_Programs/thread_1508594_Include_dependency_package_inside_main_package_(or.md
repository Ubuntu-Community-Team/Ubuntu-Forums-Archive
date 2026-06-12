---
title: "Include dependency package inside main package? (or other solution?)"
date: 2010-06-13
forum: Packaging and Compiling Programs
---

### Post by Master_T on 2010-06-13
Hi guys!

I'm faced with the following scenario: I have a software I want to distribute which consists of two packages: the main program and a shared library it depends on. Now, my problem is as follows: I need to somehow distribute this as a single package (due to reasons out of my control) and I don't know how to do it! If I use "depends" I will need to make the users add a repository manually where the lib is located, which I'd prefer to avoid. Isn't there a way I can somehow include the library package and the program package in a single .deb? Are there any other solutions that would allow me to distribute two packages as one?

Thanks in advance
Master_T

---

### Post by Umang on 2010-06-17
You can make two binary packages (.deb files) from one source package. That way, whichever repository you are distributing the package in (PPA, archieve, etc), will have both binary packages and you can have one depend on the other.

However, if you simply cannot do that (e.g. you need to send a .deb file manually to someone) then you're left with no option but to package such that you install the library with the main package. You will have to be very carefull that you are not packaging an existing lib as a particular user may already have that lib install and you will be overwriting it - BAD.

---

