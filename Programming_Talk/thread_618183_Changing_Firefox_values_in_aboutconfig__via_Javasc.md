---
title: "Changing Firefox values in about:config  via Javascript"
date: 2007-11-20
forum: Programming Talk
---

### Post by DivineOmega on 2007-11-20
Is there any way of changing the values in about:config (specifically print.print_printer) using Javascript, or via any other method when a page loads?

Basically, I need a way of telling Firefox to print a document to specific printer (in this case a label printer). If there is a better way of doing this, I'm open to all suggestions?

Thanks. :)

---

### Post by CptPicard on 2007-11-20
I'm pretty much absolutely certain the answer is "no" as that would be a huge security hole...

---

### Post by DivineOmega on 2007-11-20
> **CptPicard said:**
> I'm pretty much absolutely certain the answer is "no" as that would be a huge security hole...

That's what I expected. Is there any chance this could be done via an Firefox add on/extension?

---

### Post by smartbei on 2007-11-20
You can use a local javascript file which is called, I believe user.js in the profile folder to control firefox for that particular profile. You might be able to use it to print a certain page when it is opened in the browser. Since this file is local and must be installed by the user it is not a security risk :).

---

