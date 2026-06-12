---
title: "Where is the GUI-toolkit for Moblin 2 desktop?"
date: 2009-06-04
forum: Programming Talk
---

### Post by moma on 2009-06-04
Hello,

I've seen the [Moblin based user interface...]("http://moblin.org") that evidently uses the [Clutter-library...]("http://clutter-project.org/") to animate the GUI elements.  

Moblin clutter [demo 1...]("http://www.youtube.com/watch?v=AYGp6iBmCyM")
Moblin clutter [demo 2...]("http://moblin.org/documentation/moblin-netbook-intro")

But what GUI-toolkit it (the Moblin) uses? 
Does Clutter have its own GUI-toolkit (for buttons, scrollbars, edit fields, etc) or should we developers just sew GTK2 and Clutter together best we can? 

I think Moblin still needs the Xorg/XCB stack.

---

### Post by unknownPoster on 2009-06-04
It's just QT/GTK

Sometimes you need to dig a little to get your information...

[http://moblin.org/documentation/moblin-overview/moblin-core](http://moblin.org/documentation/moblin-overview/moblin-core)

Attached is a "screenshot" of the moblin-core

---

### Post by moma on 2009-06-06
Hello,

It's a pity that there is no common UI toolkit that integrates user interface components (like in GTK2) and Clutter together. All that seamlessly.

Anyway, I already compiled and ran [this example application...]("http://moblin.org/documentation/moblin-sdk/create-new-application") on an ordinary Ubuntu 9.04, so at least the start was easy. They even provide a small [project generator app]("http://moblin.org/projects/linux-project-generator"). To avoid errors, run "sudo ldconfig" before using it. It generated a project but compilation failed either because it didn't include libraries or it relied on a wrong lib version (libclutter-0.8 vs. libclutter-0.9).  

Her is a list of all important [docs...]("http://lwn.net/Articles/336455/")

Thanks.

EDIT: Well, [Tidy... ]("http://www.clutter-project.org/blog/?p=41")seems to be an experimental toolkit based on Clutter. Simple [demo1...]("http://folks.o-hand.com/ebassi/tidy-viewport.ogg"), [demo2...]("http://folks.o-hand.com/ebassi/tidy-list-view.ogg")

---

