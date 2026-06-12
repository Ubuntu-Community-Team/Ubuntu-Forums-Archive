---
title: "Problems installing GTK+-3.0"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by mark allyn on 2012-09-23
Hello everyone,
 
I'm making rather a mess of installing GTK+ because of a dependency between GNU's gettext library and glib-2.32.4.  In the make step for glib, make can't find libgettextsrc-0.18.1.so.  In fact, that library is installed in /usr/local/lib.  What I need to know is how to tell the make step for glib-2.32.4 that it should look in /usr/local/lib instead of wherever it is looking now.
 
I guess this is a pretty generic problem, but I am green at this stuff and would appreciate some coaching.  I will no doubt run into this hurdle again in the future.
 
Thank you,
Mark Allyn

---

### Post by steeldriver on 2012-09-23
not a real expert here but you could try passing it via the LDFLAGS macro on the make command line

```
make "LDFLAGS=-L/usr/local/lib"
```

---

### Post by mark allyn on 2012-09-23
Hi again Steeldriver,
 
Yes, that might work.  At this moment I'm trying a variation on your approach.  In about 15 minutes I'll be able to report back results.  
 
Regards,
Mark Allyn
 
PS.  Wow, GTK building is a nightmare.....

---

### Post by mark allyn on 2012-09-23
Hi again, steeldriver,
 
Well, my method (which was to set the library path varialbe in ./configure) did not work.  I gave yours a shot and it didn't work either. On refelection, it seemed to me that LDFLAGS was never going to set a search path unless there was some way of using the Wl,--"set shared library searh path=///", which, as far as I know, does not  exist.
 
I have resorted to setting LD_LIBRARY_PATH=/usr/local/lib, but this too seems ineffective.
 
Any further thoughts?
 
Regards,
Mark

---

### Post by mark allyn on 2012-09-23
Hi yet again, steeldriver.
 
Actually, LD_LIBRARY_PATH did work.  I still think as you do that there must be a way to set the search path in the make step.  Just don't know what it is.  I'd prefer that solution if it were available.
 
Regards,
Mark

---

### Post by steeldriver on 2012-09-23
I don't know Mark - my understanding is that LD_LIBRARY_PATH is used by ld (in addition to the paths defined by ldconfig, as we discussed in a different thread) at runtime - perhaps it is used at build time as well, and LDFLAGS only works for static (.a) libraries?

---

### Post by mark allyn on 2012-09-23
Hi steeldriver,
 
I don't know enough to be surprised about anthing that happens with linux/ubuntu!  We'll put the matter to the acid test tomorrow morning when I try to install Cairo-1.12.2.  If it balks over glib-2.32.4 then I'm back to square one.
 
Will let you know.
 
Regards,
Mark

---

### Post by mark allyn on 2012-09-24
Hi steeldriver,
 
Well, I was able to install cairo-1.12.2, so it appears as if setting the LD_LIBRARY_PATH was successful in getting glib2 installed.  Feeling rather triumphant (as a rank amateur) I then proceeded to try to install Pango-1.30.1.  
 
In the configure step for Pango I got the following message:
 
  "Could not enable any of Freetype, X11, Cairo, or Win32 backends."
  Must have at least one backend to build Pango.
 
As it happens, Feetye, X11, and Cairo libraries are all installed in /usr/lib.  So, something needs to be set in the configure command.  Don't know what, but looking around on the internet it appears that PKG_CONFIG_PATH may be involved.
 
Regards,
Mark

---

