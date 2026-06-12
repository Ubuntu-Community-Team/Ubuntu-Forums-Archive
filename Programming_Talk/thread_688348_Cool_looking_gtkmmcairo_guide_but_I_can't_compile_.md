---
title: "Cool looking gtkmm/cairo guide but I can't compile examples"
date: 2008-02-05
forum: Programming Talk
---

### Post by BuffaloX on 2008-02-05
I found this guide,

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)

first example compiled fine,
Already 2nd example I can't compile, 3rd example uses automake but I cant make that work either.

Anyone had better luck, the guide looks very cool otherwise.
But kind of futile to use it, if I the examples doesn't work.

---

### Post by xlinuks on 2008-02-05
> **BuffaloX said:**
> I found this guide,

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html)

first example compiled fine,
Already 2nd example I can't compile, 3rd example uses automake but I cant make that work either.

Anyone had better luck, the guide looks very cool otherwise.
But kind of futile to use it, if I the examples doesn't work.

I'm having exactly that same problem and using same tutorial, its pretty cumbersome that they just told "go there and study that book on automake, auto-something", they _should_ at least provide basic explanation how to compile their simple examples.
As such I'm compiling so far by hand their examples, for instance the second example would compile with the following line:
```

g++ main.cc helloworld.cc -o app `pkg-config gtkmm-2.4 --cflags --libs`

```
Hope they will add a chapter or something to cover this weak spot.

---

### Post by BuffaloX on 2008-02-05
Thanx for the feedback
The fact that you can compile, made me try once more.

I also tried manually, but got some weird HelloWorld not defined error.
This apparently was caused by unmet dependency on libglade, which is not mentioned in the dependency overview, and I only found out, because I tried to run the precompiled executable.

So at least I can compile manually too now. :)

---

### Post by DugDra on 2008-02-07
```

g++ main.cc helloworld.cc -o app `pkg-config gtkmm-2.4 --cflags --libs`

```

Thanks all. This is just what I needed. What is the name of this piece of code that is used to compile a program in g++?

Doug Drader

---

### Post by BuffaloX on 2008-02-07
It works for the examples linked to in my original post.
The particular line is for second example in this very intresting guide.
For other examples replace helloworld.cc with what is needed.

---

### Post by xlinuks on 2008-02-09
> **BuffaloX said:**
> It works for the examples linked to in my original post.
The particular line is for second example in this very intresting guide.
For other examples replace helloworld.cc with what is needed.

IMO I found an even easier way:
I downloaded NetBeans - the version bundled with C/C++, configured it to search the /usr/include/gtkm-2.4 directory, and that's it.
Now I only press the green "run" button to compile and run a/any gtkmm project.
Here's the (preconfigured) NetBeans project for the 3rd example from the tutorial (CheckButton):
[http://xlinuks.googlepages.com/CheckButton.zip](http://xlinuks.googlepages.com/CheckButton.zip)

You can set those settings to be the default ones, so you don't have to specify them each time you create a new gtkmm project.

---

### Post by BuffaloX on 2008-02-09
Cool feedback thanks.

Have you tried Code::Blocks
I've used it for some other projects, and it's very powerful, and very nice to work in.
The guide made me realize I need to brush up my C++, But I'll be back on that in a couple of days I hope.
Its not in repos, but they have Ubuntu packages for nightly builds.
It can be added to your repo, so it can auto update too.

---

### Post by jdehaan@ on 2010-09-27
A bit late, but maybe someone else benefits from this:

[http://library.gnome.org/devel/gtk/unstable/gtk-compiling.html](http://library.gnome.org/devel/gtk/unstable/gtk-compiling.html)

pkg-config --cflags --libs gtk+-3.0

gives the compiler flags

Sincerely,

Jan.

---

