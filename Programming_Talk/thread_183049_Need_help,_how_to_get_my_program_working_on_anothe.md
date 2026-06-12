---
title: "Need help, how to get my program working on another computer?"
date: 2006-05-27
forum: Programming Talk
---

### Post by Freddd on 2006-05-27
Hi everyone :)

I got glade working in Ubuntu on my laptop and I played around and programmed a very simple application. Everything worked brilliant and then I got the question: what do I need to do to get this simple application to work on another computer? I tried to copy my executable to my desktop computer which also has Ubuntu installed. The program failed to run on this computer, instead the terminal was shown.

My question is, what do I have to do to be able to run my simple application on other computers?

Thanks in advance :???:

---

### Post by viciouslime on 2006-05-27
I can't even get that far. I get:
```
**Error**: You must have `glib' installed.

```
When i try to run autogen.sh. I have searched but can't find a package containing "glib" anywhere. :-k

---

### Post by viciouslime on 2006-05-27
AHA! Just found it!

I had previously found libglib1.2-dev but i've just realised there is a libglib2.0-dev, it seems to be working now. As for running on other people's computers however... pass

EDIT: Also need libgtk2.0-dev. Why aren't these two packages dependencies of glade?

---

### Post by Freddd on 2006-05-27
Search for it in Synaptics, I think it's named: "libglib2.0-dev"

I'm a novice in this subject and I got it up and working after about 30 minutes or so. The only problem was to find the necessary packages. Don't hesitate to put your questions here. I will try to help you out.

**My problem in this thread is already solved. I got it to work by changing the permissions on my executable** :)

---

### Post by Freddd on 2006-05-27
[QUOTE=viciouslime]AHA! Just found it!

I had previously found libglib1.2-dev but i've just realised there is a libglib2.0-dev, it seems to be working now. As for running on other people's computers however... pass

EDIT: Also need libgtk2.0-dev. Why aren't these two packages dependencies of glade?[/QUOTE]Yeah, the instructions could be better. I just installed a package and attempted to run autogen.sh until I finally got it to work.

Another package that I think you will need is: "libgnome2-dev"

---

### Post by viciouslime on 2006-05-27
I don't appear to, unless I already have it installed...
No, I don't (just checked). maybe it depends exactly which features/functions of glade you use in your app...

---

### Post by Freddd on 2006-05-27
Do you know what the difference is between these two project types: gtk+ or gnome? :confused:

---

