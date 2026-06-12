---
title: "How to checkout a latest release of lirc with cvs"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by dacium on 2008-06-02
I used:

cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login

then:

cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc


However make fails because there are compile errors, it looks like some clown was adding new version to the CSV but stopped halfway through so now its all broekn. How do I check out the latest stable release so I can make lirc?

---

### Post by rraj.be on 2008-06-02
You can use the synaptic package manager to check the installed version and your lattest version and you can update your packages too with the same

---

### Post by dacium on 2008-06-02
ah i worked it out:
checkout -r lirc-0_8_3 lirc

i needed source because i had to add a custom patch

---

