---
title: "odd form submissions (html, php)"
date: 2007-04-15
forum: Programming Talk
---

### Post by tocleora on 2007-04-15
On one of my web sites I've recently started getting a bunch of form submissions where every field on it is something like this:

8490d624-b4dd-49df-a3d4-2719384b47ca

sometimes it also includes "<script id=" sometimes it also includes "@@version".  There's usually about 100 of them and they happen within a 5 minute period.  Is this something I should be concerned about?

---

### Post by finer recliner on 2007-04-15
bots trying to run scripts on your website (?)

---

### Post by Frosty Cold Drink on 2007-04-15
It looks like a worm or bot trying to fire up an ActiveX control via its GUID.

---

### Post by tocleora on 2007-04-15
So that would be microsoft related and since I run a linux server, nothing to worry about?

---

### Post by Frosty Cold Drink on 2007-04-15
> **tocleora said:**
> So that would be microsoft related and since I run a linux server, nothing to worry about?

Pretty much, yeah.

---

