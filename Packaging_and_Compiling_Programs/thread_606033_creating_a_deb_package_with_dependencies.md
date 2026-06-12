---
title: "creating a deb package with dependencies"
date: 2007-11-07
forum: Packaging and Compiling Programs
---

### Post by CrZy_T on 2007-11-07
Hi.

I hope I found the correct forum to post this, if not I would be glad if a moderator moved it to the correct one.

I'm trying to create a deb package with dependencies. I think I've gotten it correct. My next question is, is it possible to make the package install these dependencies from apt without having my deb package in a repository?

\\CrZy_T

---

### Post by Jussi Kukkonen on 2007-11-07
That's not up to the package, but the program the user is using. dpkg does not install dependencies (although you can fix that with apt later), but I believe the default graphical install on ubuntu (Gdebi?) does install dependencies if they are available.

---

### Post by CrZy_T on 2007-11-07
I tried Gdebi, it only said "dependencies missing. To fix this, run apt-get install -f" or something. It might be my package having errors, but I though I got it right.

My problem is trying to make it as easy as possible for end users to install the needed software to use an authentication solution. A simple deb-package would make things a lot easier then giving the end user 5-10 bash commands :)

---

### Post by Kow on 2007-11-07
I would say force install your package and then see if aptitude or synaptic will fix dependencies.

---

### Post by LaserJock on 2007-11-07
Perhaps more information would help:

 * what are you using to create the .deb ?
 * what are the dependencies?
 * are all of the dependencies in repos?

-LaserJock

---

