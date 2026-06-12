---
title: "How to give &quot;Wire&quot; permission to access the webcam?"
date: 2018-12-28
forum: New to Ubuntu
---

### Post by evilevilhamster on 2018-12-28
Hi all, I just installed Ubuntu LTS 18.04 on a Laptop. I installed wire with the inbuilt installer. But, when trying to make a video call, it says that it does not have permission to access the webcam etc. and gives a link for support. The support page only describes what to do in Windows and on browsers... not on Linux.

When making an audio call, it works fine. Also, when using the inbuilt webcam app, it gives me video, so I assume that the drives are automatically installed from Ubuntu. Anyway, if anyone has any tips, I would appreciate it (also, please do talk slowly, as I am very much a noob :))

Best

---

### Post by Holger_Gehrke on 2018-12-28
"wire" is a snap-package. snaps are constrained using appamor profiles so they are less likely to do bad stuff on your machine (note the 'less likely'; it's not like they can't do bad things, it's just a little bit harder ...). One of the things a snap can't do without explicit permission is access the camera. To give this permission, open a terminal and enter ```
snap connect wire:camera core:camera
```Note: I haven't tested this. I just looked in "Software", found it was a snap, called "snap info wire" in a terminal which gave me the address for the [snapcrafters github page for wire]("https://github.com/snapcrafters/wire"), and read the instructions there. 
Also: this thing is a node.js / electron application, so it's basically a local copy of the web-app + a javascript engine + an almost complete browser; that explains why it's 126 MB just for a chat app ...

Holger

---

### Post by evilevilhamster on 2018-12-28
briliant. Works like a charm :).

I did not quite understand the second part of the post, but at some point I probably will :).

Thanks a bunch.
Best regards.

---

