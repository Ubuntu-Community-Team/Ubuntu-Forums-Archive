---
title: "GIMP 2.7.5 Compiling GTK+ Error"
date: 2012-03-17
forum: Packaging and Compiling Programs
---

### Post by JustinR on 2012-03-17
Hey everybody,

I've been in the process of compiling GIMP 2.7.5 on Ubuntu Precise 12.04 (Beta 1).

So far I've only gotten to compiling most of the dependencies:
babl-0.1.6
gegl-0.1.8
cairo-1.6.0
GTK+-2.24.7

During the 'make'ing process of GTK+ I get this error:
> 
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libpangocairo-1.0.so: undefined reference to 'cairo_show_text_glyphs'
/usr/lib/gcc/i686-linux-gnu/4.6/../../../i386-linux-gnu/libpangocairo-1.0.so: undefined reference to 'cairo_surface_has_show_text_glyphs'
collect2: ld returned 1 exit status


I've researched this for a while, and only found 1 thread that didn't offer a solution but apparently solved it. It seems to be a problem with the version of either Pango (v. 1.29.5) or Cairo(1.6.0)

Can someone point me in the right direction as to what I should do? Thanks.

---

### Post by gordintoronto on 2012-03-17
> **JustinR said:**
> Hey everybody,

I've been in the process of compiling GIMP 2.7.5 on Ubuntu Precise 12.04 (Beta 1)....

Why?

---

### Post by JustinR on 2012-03-17
> **gordintoronto said:**
> Why?

School project files were created in this version of GIMP that I need to edit.

---

### Post by SevenMachines on 2012-03-17
To be honest, I'd be having a word with whoever created those school project files that demand a version of gimp that hasnt even reached debian unstable yet and ask them to be a bit more pragmatic but as far as your linking errors go...

precise already has a higher version of cairo than 1.6, the error cairo_show_text_glyphs seems to reflect a change that occurred in 1.8 or so, precise uses 1.10. Use the system libraries for those parts, hopefully you've been using a local build chain against them and not overwritten the system libraries? (this is *always* a bad idea!) the gtk version you mention is also superceded in precise

---

### Post by JustinR on 2012-03-17
> **SevenMachines said:**
> To be honest, I'd be having a word with whoever created those school project files that demand a version of gimp that hasnt even reached debian unstable yet and ask them to be a bit more pragmatic but as far as your linking errors go...

precise already has a higher version of cairo than 1.6, the error cairo_show_text_glyphs seems to reflect a change that occurred in 1.8 or so, precise uses 1.10. Use the system libraries for those parts, hopefully you've been using a local build chain against them and not overwritten the system libraries? (this is *always* a bad idea!) the gtk version you mention is also superceded in precise

Okay, thanks for the information on that. I didn't use a local build but this is all being done in a virtual machine so I'll rollback all of these changes and try with the updated precise packages. I'll post back later today if I need more help.

---

### Post by JustinR on 2012-03-18
Thanks for all your guys' help.

I finished compiling it with precises GTK+/Pango/Cairo and only built babl/gegl from source.

---

