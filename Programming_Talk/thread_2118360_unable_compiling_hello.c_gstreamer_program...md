---
title: "unable compiling hello.c gstreamer program.."
date: 2013-02-21
forum: Programming Talk
---

### Post by sudhakarRedi on 2013-02-21
hi every one...

I have the same problem that unable to include <gst/gst.h> and <glib.h>

can any one help me...

thank you..

---

### Post by codemaniac on 2013-02-21
Hello sudhakarRedi,

Your post is now moved to its own thread. Feel free to use the edit button and include more details if required.

Best Regards,
codemaniac

---

### Post by sudhakarRedi on 2013-02-21
hi...

I run the following commands
gst-inspect 
gst-launch

i got bunch of information indicating that gstreamer lib's are working.., but I am unable to use gst.h in my code. :(

can any one help me..

thank you

---

### Post by Zugzwang on 2013-02-21
It is always helpful to post the *precise* error message, i.e., a copied&pasted one.

So I have to guess what is actually wrong. My main guess is that you did not install the needed development packages. Go to "packages.ubuntu.com", look in which package "gst.h" is located, and then install it.

---

