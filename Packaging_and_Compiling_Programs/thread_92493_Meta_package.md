---
title: "Meta package"
date: 2005-11-19
forum: Packaging and Compiling Programs
---

### Post by christooss on 2005-11-19
Does any one know how to make a meta package such as ubuntu-desktop

This meta package contains some files. Is it enough to edit control file in there? Or is there an aplication to make meta package?

---

### Post by az on 2005-11-19
[QUOTE=christooss] Is it enough to edit control file in there? [/QUOTE]

Yes.  You can add your custom docs to your debian tree.  Bump the changelog if you are keeping the same package name.

That's about all I know about the process...

---

### Post by Roptaty on 2005-11-21
You may take a look at: [http://www.us.debian.org/doc/manuals/apt-howto/ch-helpers.en.html#s-equivs](http://www.us.debian.org/doc/manuals/apt-howto/ch-helpers.en.html#s-equivs)

The equivs package can be used to create virtual packages.

---

