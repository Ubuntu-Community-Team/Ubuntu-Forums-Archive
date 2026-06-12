---
title: "Upgrade to 11.10 from NN leaves me with no windows management !!"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by kalimojo on 2011-10-16
title says it all. allowed the 11.10 upgrade to go ahead and now i cant manage any of my windows - all the windows controls are gone. only alt-tab has allowed me to continue working.

any ideas good folks ?

[http://synthetictelepathy.maxforum.org/](http://synthetictelepathy.maxforum.org/)

---

### Post by searchfgold6789 on 2011-10-16
Are you saying that the title bar of all of your windows is gone?
Try getting to a terminal and typing the below command. If you can't do that, type Alt + F2. Type in:```
metacity --replace
```If it works, you can set it to be run at startup using Startup Applications.

---

### Post by searchfgold6789 on 2011-10-16
EDIT:
My computer crashed and I accidentally posted again. Remove this post please.

---

### Post by bslayers on 2011-10-17
I have a simular problem with my laptop,  nothing but a screen with a header "File Edit Go Bookmark Help"    no borders, no icons.  It did retain my desktop folders and files.  I did ctr+alt F2. The terminal was different from 11.04.  I typed in both sudo metacity and metacity --replace. Both returned "unable to open X display"
Any further ideas would be great.

---

