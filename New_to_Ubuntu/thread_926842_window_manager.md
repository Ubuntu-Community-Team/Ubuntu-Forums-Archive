---
title: "window manager"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by vinceRRR1 on 2008-09-22
Hello Forum

i have installed ANTIX linux (new version) on a dual boot laptop
with winXP.

It is all working correctly.

I have installed the AFTERSTEP window manager into ANTIX.

How do i get ANTIX to boot into the Afterstep window manager?

How do i get the menu's in Afterstep to show everything that the ANTIX operating system is offerring....(it is DEBIAN based...ANTIX)?

I know this is not ubuntu but i figured ANTIX is debian based...like ubuntu and maybe somebody can help.

thanks

Vince.

---

### Post by Het Irv on 2008-09-22
In Ubuntu in the bottom right hand corner there is a menu that you can pull up and choose which session you want to start.  That is the closest that I can come to answering your question.  I am kinda a newbie when it comes to Linux, but I know Ubuntu fairly well.

---

### Post by vinceRRR1 on 2008-09-22
Hello

Thanks for replying.

If only it were that simple.

I know that i need to go in and MANUALLY edit some lines in a config file. But i don't know which file and what lines.

I know that ANTIX uses the SLIM login screen. SLIM offers the selection of window managers....but manually selecting different WM's......has no effect...Antix still boots into the same WM each time....

thanks

Vince.

---

### Post by Het Irv on 2008-09-22
When asking around about this I was refered to this site:
[http://www.malfunction.de/afterstep/ashow/overview.html](http://www.malfunction.de/afterstep/ashow/overview.html)

Does this help any?

---

### Post by digitalvectorz on 2008-09-22
try looking at [http://www.malfunction.de/afterstep/ashow/overview.html](http://www.malfunction.de/afterstep/ashow/overview.html).

i'm not quite sure as i've never worked with or even heard of antix/afterstep until this post.

---

### Post by willca on 2008-09-23
/etc/slim.conf

look for sessions and add the new window manager there if not yet in there.

---

