---
title: "Troubleshooting links"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by bdemers on 2008-10-18
Geda is a suite of multiple executables.  I would like to launch these from my desktop, rather than from its directory, several layers deep.  I verified that a targetl file will launch from its proper location and then created a link and left the link in the original directory.  I can not launch from the link.  The original suite was installed using sudo, but I then went and chown'd the directory to me.  The link algorithm is working as I created a link for the parent geda directory, moved it to the desktop and was able to drill down until I got to the target file.  No go at that point.  How do I figure this out?

Second question, I installed an application called ngspice and another called xspice.  I am able to run the app, but a search on ngspice (no hiddens)doesn't return a hit. Doesn't with xspice either.  How do I find the executables for these apps?

Thanks

---

### Post by oldos2er on 2008-10-18
To answer your second question, most user installed executables wind up in /usr/bin .

---

