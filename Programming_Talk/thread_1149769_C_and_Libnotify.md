---
title: "C and Libnotify"
date: 2009-05-05
forum: Programming Talk
---

### Post by winter_mute on 2009-05-05
I'm trying to add libnotify support to a program, but I keep running into a problem with the compiling step.  The only resource I've found so far is this:

[http://manishtech.wordpress.com/2009/03/29/working-with-libnotify/](http://manishtech.wordpress.com/2009/03/29/working-with-libnotify/)

Are there any better resources with, say, a list of dependencies and what I'd need to call in GCC to get the example code there to compile?  I'd really like to figure this out, but I'm completely lost and without resources.  Right now I'm compiling with:

gcc `pkg-config --cflags --libs gtk+-2.0` temp.c -llibnotify -o notify

But I get a comment that ld can not find libnotify.  Any help would be great.

---

### Post by eye208 on 2009-05-05
> **winter_mute said:**
> But I get a comment that ld can not find libnotify.
Your command line is wrong. It should be -lnotify, not -llibnotify

---

### Post by winter_mute on 2009-05-05
Aha!  Thanks!  I was entirely at a loss.  That fixed it perfectly.

---

### Post by manishtech on 2009-05-16
I am honoured that my blog post was beneficial for the public. I would research more on this library and write more blog posts. Well in the post itself I have written

> $ gcc `pkg-config &#8211;cflags &#8211;libs gtk+-2.0` notify.c -o notify -l notify

Sorry for bumping an old thread.

---

### Post by crdlb on 2009-05-18
That's not really ideal either; just add libnotify to the pkg-config command line so that pkg-config can handle everything for you:

```
gcc `pkg-config --cflags --libs gtk+-2.0 libnotify` notify.c -o notify
```

---

### Post by manishtech on 2009-05-18
Hey[ crdlb]("http://ubuntuforums.org/member.php?u=90928")

Thanks for the info

---

