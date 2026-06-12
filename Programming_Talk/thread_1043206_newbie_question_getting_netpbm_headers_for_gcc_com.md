---
title: "newbie question: getting netpbm headers for gcc compilation?"
date: 2009-01-18
forum: Programming Talk
---

### Post by pk1 on 2009-01-18
I am using 2.6.27.9 and I am unable to find the headers of the netpbm library (specifically [FONT="Courier New"]pam.h[/FONT])

The command: [FONT="Courier New"]
   sudo apt-get install net[/FONT]pbm

results in:
[FONT="Courier New"]   0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]

I can find [FONT="Courier New"]libnetpbm.so.10.0[/FONT] in[FONT="Courier New"] usr/lib[/FONT] but[FONT="Courier New"] pam.h[/FONT] is not found when I do a search of the entire computer. I have downloaded a tarball of the netpbm source (that includes [FONT="Courier New"]pam.h[/FONT]) but I'm sure there must be a better way of installing a software sdk.

Is there an easy way to set up the gcc programming environment to use netpbm?

---

### Post by eye208 on 2009-01-18
Headers are always in separate *-dev packages. In your case it is either libnetpbm10-dev or libnetpbm9-dev, depending on the library version you want to use.

---

### Post by pk1 on 2009-01-18
Many thanks! I appreciate the help.

---

