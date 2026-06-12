---
title: "Software Center says &quot;Dependency not satisfiable: libconfig++8&quot;"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by abattleofone on 2012-11-21
I just installed Ubuntu, and I'm quite enjoying it. However, I want to install this .deb file, but whenever I double click it (or try to install it using the terminal, I get a similar response), I get the error from the Software Center saying "Dependency not satisfiable: libconfig++8". As far as I can tell, I do in fact have a libconfig++8 on here. Like I said, I'm very new to this operating system, so I'm most likely overlooking something really simple and making myself look like a fool.

---

### Post by lykwydchykyn on 2012-11-21
Chances are your deb file is not compiled for this version of Ubuntu, or something other than Ubuntu.  Does the error indicate a particular version of libconfig++8?

---

### Post by abattleofone on 2012-11-21
> **lykwydchykyn said:**
> Chances are your deb file is not compiled for this version of Ubuntu, or something other than Ubuntu.  Does the error indicate a particular version of libconfig++8?

No, that is all that the software center says. When I try installing it through terminal, it says "Package libconfig++8 is not installed."

---

### Post by lykwydchykyn on 2012-11-21
I don't think there's a package called libconfig++8 in the repositories.  What is this deb and does it indicate that it's for the version of ubuntu you're currently running?

---

### Post by windscape on 2012-11-21
libconfig++8 was in Ubuntu 12.04, in 12.10 it is now libconfig++9. As indicated in the post above, it sounds like your package was written for Ubuntu 12.04 and you're running Ubuntu 12.10.

---

### Post by squakie on 2012-11-21
I would think you could set a link between the 8 version name and the actual 9 version lib installed, or you could check to see if there is some form of back ports available that would have that version in it.

---

