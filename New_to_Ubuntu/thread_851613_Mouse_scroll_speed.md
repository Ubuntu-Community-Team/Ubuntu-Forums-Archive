---
title: "Mouse scroll speed"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by DeadEagle on 2008-07-06
I'm just curious as to if there is a way to make my scroll speed faster, I don't see the option under preferences > mouse.

:confused:

---

### Post by happymellon on 2008-07-06
> **DeadEagle said:**
> I'm just curious as to if there is a way to make my scroll speed faster, I don't see the option under preferences > mouse.

:confused:

Unfortunately you can't. But....

Some people have edited their xorg.conf file to add a new line specifying the scroll speed, which seems to have had mixed results. They added:

Option "VertScrollDelta" "6"

to the mouse part, though I have not attempted that before. Let me know if you want to attempt that and I can give you better instructions.

If you are mostly having the issue in Firefox, you can speed that up from following these instuctions - [http://osnovice.blogspot.com/2007/04/test.html](http://osnovice.blogspot.com/2007/04/test.html)

Just to let you know this is something that these is a fix request open for. Though it was only open in March.

[http://brainstorm.ubuntu.com/idea/3214/](http://brainstorm.ubuntu.com/idea/3214/)

---

