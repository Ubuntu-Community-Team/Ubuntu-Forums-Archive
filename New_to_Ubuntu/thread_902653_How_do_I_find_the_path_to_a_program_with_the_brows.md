---
title: "How do I find the path to a program with the browser?"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2008-08-27
My ftp client program, fireFTP, has an option in which I can "open with..." by right clicking on an html file I'd like to work on. I use gvim to work on these files. And yet I can't find it on my File Browser. I know I have it, all i have to do is type "gvim" into the terminal and it pops up. But I can't find it... where would such programs be,? i don't see it in my home folder, where other files exist. It won't show up in a search of the file browser...

---

### Post by Vivaldi Gloria on 2008-08-27
In a terminal give one of the commands:

```
which gvim
whereis gvim
```

---

### Post by t0p on 2008-08-27
I'm a bit confused as to why you'd expect to find gvim in your home folder.  Gvim is a program, which is in /usr/bin, as most apps are.

If you want it to appear in your Applications menu, you can add it under Accessories.  It's got a lovely icon, a grey letter V over a green... something.  A cross?

---

### Post by Scunge on 2008-08-27
> **t0p said:**
> I'm a bit confused as to why you'd expect to find gvim in your home folder.  Gvim is a program, which is in /usr/bin, as most apps are.Indeed, most, but not all. If you install an application but not as root, e.g. something you download outside of the repositories, it will be installed in /home/xxx/.local/bin.

Not saying it would have happened in this case, just that it's possible.
[img]http://i268.photobucket.com/albums/jj22/Rob_0edab8/Spacer.gif[/img]

---

### Post by arnicainthemembrane on 2008-08-27
which gvim... very simple... is there a good guide to all this? there are simple answers to so many of these questions but is there a definitive guide?

---

### Post by t0p on 2008-08-27
> **arnicainthemembrane said:**
> which gvim... very simple... is there a good guide to all this? there are simple answers to so many of these questions but is there a definitive guide?

There's a link in my sig to an absolutely wonderful guide.  :)

---

