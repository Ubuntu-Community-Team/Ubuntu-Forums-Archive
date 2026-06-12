---
title: "[GLT] &quot;Configure compile options ...&quot; ?"
date: 2013-02-12
forum: Programming Talk
---

### Post by giuscri on 2013-02-12
Hi everyone,

I need to develop an application using the [GLT library]("http://www.nigels.com/glt/"), but I'm finding troubles while installing it on my computer. For the records: I'm using Ubuntu 12.10 right now.

Here ([http://www.nigels.com/glt/download.html](http://www.nigels.com/glt/download.html)) one should be able to download the source, run the makefile, and then just use the library, but I fail.

The installation steps, as the link says, are the following:

[LIST=1]
[*]*Extract core sources, along with extras*
[*]*Configure compile options in **glt/src/glt/config.h***
[*]*Configure compile options in **glt/src/glutm/config.h***
[*]*Configure compile options in **glt/src/misc/config.h***
[*]*Run **make** from the base glt directory.*
[/LIST]
But I have no idea of how configuring compile options in the *config.h-*files:  running the makefile generates an infinitely long output of errors, indeed.

How could I solve that?

Thank you in advance,
Giuseppe

---

### Post by giuscri on 2013-02-22
Hello! I've solved this problem and I write something that might be helpful for everyone else that find troubles with that. You can find that here: [http://giuso-blog.blogspot.it/2013/02/how-to-install-glt-opengl-c-toolkit-on.html]("http://giuso-blog.blogspot.it/2013/02/how-to-install-glt-opengl-c-toolkit-on.html")

---

