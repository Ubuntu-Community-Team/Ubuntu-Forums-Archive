---
title: "[SOLVED] Mathematica help window; search bar and buttons frozen"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by camac014 on 2008-10-22
Hello, I'm running Mathematica 6.0.0 for students on Hardy and I sometimes come across random bugs that sometimes occur when using the program.

I've not been able to use the documentation center very much because the search bar is frozen: see image

[IMG]http://programplace.googlepages.com/screenshot12.png[/IMG]

I've tried 

```
mathematica -defaultvideo
```

and the workaround with the notebook window settings. These fixed the extra windows problem, but I'm still having trouble with the search bar being frozen.

Any help is appreciated. Thank you.

EDIT: Also, I'm not sure if this is the correct forum to post this in. If it's not, will someone please move it?

---

### Post by 4KvRMU7Nnv on 2008-10-24
as spectacular as it may sound, the frozen searchbar is caused by numlock.  Disable it to be able to type. :)  

I am very annoyed with the linux implementation of Mathematica because it doesn't seem to take full or perhaps ANY advantage of the OpenGL rendering for 3D graphics in real time when, on the same computer, it renders quickly and 3D images can be dragged and rotated easilly.  I dont know how to fix that part...

---

### Post by camac014 on 2008-10-24
Aha! That's why it worked spontaneously! Thanks.

---

