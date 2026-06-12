---
title: "How do you run a script when a tarball is extracted?"
date: 2008-06-03
forum: Programming Talk
---

### Post by days_of_ruin on 2008-06-03
I know some documentation tarballs that when you extract them they must
change all the links (I am talking about html here) so that they work
for offline.How do they do it?

---

### Post by nhandler on 2008-06-04
As far as I know, the only way to do this would be if the extraction program had this function. I personally have never heard of it before. Are you sure that the links weren't modified prior to packaging it in a tarball? They could have done this if they used relative links. Relative links would work as long as the directory structure remained the same. Also, if they instructed the user to extract the tarball to a certain directory, they could have used absolute links (although relative links are much more likely).

You could also package a script inside the tarball. Then, the user could just run the sript, and it would take care of adjusting all of the links based on the location of the files.

I personally feel that they most likely created a special version of the documentation that was designed for offline use. This version probably uses relative links so that the actual location of the documentation on the user's computer is irrelevant.

---

### Post by Can+~ on 2008-06-04
What do you mean with "changing the links"?

Html can work inside a folder, if you do <a href="folder/something.html">a link</a> using a relative path.

---

