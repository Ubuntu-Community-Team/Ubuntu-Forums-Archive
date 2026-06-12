---
title: "embedded glade file"
date: 2010-12-20
forum: Programming Talk
---

### Post by worksofcraft on 2010-12-20
if you are using gtk and glade you can embed the XML glade file directly as a binary object in your executable using the ld command.

This is cool because you don't have to ship and install glade files with your app, but I discovered that even quite a simple one is adding like 17k to my executable memory footprint.

I wonder if anyone has an opinion what is better, embedding your gui definition in the executable, installing it as a separate file somewhere, or coding the widgets explicitly and not using glade at all... or something completely different?

---

