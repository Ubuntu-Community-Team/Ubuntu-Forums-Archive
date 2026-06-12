---
title: "[SOLVED] Under 8.10 how to make windows open in last position?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by gregphil on 2008-11-30
All my 'new' windows seem to open positioned in the upper left, no matter where or how they were last closed.  Under Kubuntu new windows open where I last closed them (windows remember their last position)

How can I get this behavior in Ubuntu 8.10 ?

Thank You.

---

### Post by Victormd on 2008-12-01
Do you have compiz installed? If so, you can use the "Place windows" plug-in under window Management.
I have 8.10 installed and my windows always open in the same place (and size) at which they were closed and this is all I did. There might be (and I'm sure there is) another way to do this if you don't have compiz. You might want to look in the configuration editor. From the terminal type:
```
gconf-editor
```
and see if you find anything.

---

### Post by gregphil on 2008-12-01
That fixed it, it was set (defaulted to) 'smart' placement which was anything but.  I changed it to centered and all is well again.

Thank You.

---

### Post by puner on 2009-03-05
> **gregphil said:**
> That fixed it, it was set (defaulted to) 'smart' placement which was anything but.  I changed it to centered and all is well again.

Thank You.

Thanks for that post, really helped me out.

For me it was set to "smart" as well, so I just did what you did and set it to "Centered" now everything is great.

But I wonder if there is a setting to open windows where you **last** closed them.

---

### Post by CerialPhreak on 2009-04-09
I wouldnt call this solved. If you enable that option in compiz, all it does is force the windows to open in the same place every time, such as in the middle of the screen (centered). Im trying to get the window (specifically pidgin) to open in the same place it was when i closed it.

---

### Post by jshzigler on 2011-06-23
This problem is happening to me in 11.04.

---

