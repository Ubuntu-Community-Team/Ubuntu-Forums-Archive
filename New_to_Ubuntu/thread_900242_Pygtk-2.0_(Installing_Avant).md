---
title: "Pygtk-2.0??? (Installing Avant)"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by sdim on 2008-08-25
Hi,everyone.
I've been trying to install Avant through Synaptic,but there seems to be an error somewhere,so I downloaded the file and I am trying to compile it.
Nevertheless,I get this message :

> checking for PYGTK... configure: error: Package requirements (gtk+-2.0 pygtk-2.0 >= 2.10.0) were not met:

No package 'pygtk-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PYGTK_CFLAGS
and PYGTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I've tried through Synaptic to find this "pygtk-2.0",but each time I install sth and run ./configure again,I get the same message.
Any help would be appreciated.
Thank you.

---

### Post by unutbu on 2008-08-25
Did you install python-gtk2-dev?

---

### Post by Nepherte on 2008-08-25
You always need to get the -dev packages when you are compiling something. So when it says the requirement pygtk-2.0 is not met, you should for a package like pygtk-2.0-dev or python-gtk-dev or something alike.

---

### Post by sdim on 2008-08-25
Where is that?
Is it in Synaptic?
I can't remember seeing it there.

---

### Post by Nepherte on 2008-08-25
python-gtk2-dev should be in the repositories (hardy)

---

### Post by unutbu on 2008-08-25
[http://packages.ubuntu.com/hardy/python-gtk2-dev](http://packages.ubuntu.com/hardy/python-gtk2-dev)

---

### Post by sdim on 2008-08-25
Many thanks.

---

