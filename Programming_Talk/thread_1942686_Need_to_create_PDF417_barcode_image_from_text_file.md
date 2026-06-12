---
title: "Need to create PDF417 barcode image from text file using Python"
date: 2012-03-18
forum: Programming Talk
---

### Post by OrangeVixen on 2012-03-18
Is there a PDF-417 Barcode generating program or library I can use with Python?

I have a program in which I need to generate a text file (using Python) and then I need another program or library to create/encode the PDF-417 Barcode image from it.

Also, is there any PDF-417 libs for Python?

---

### Post by Zugzwang on 2012-03-18
There appears to be an implementation at sourceforge that you can use: [http://sourceforge.net/projects/pdf417encode/](http://sourceforge.net/projects/pdf417encode/) - It isn't in Python, but that doesn't matter. It comes with a stand-along executable that you can simply call from Python using the subprocess module.

---

### Post by OrangeVixen on 2012-03-18
Thanks, yes I have come across that one but only the source. I could not find an executable or packages for that.

It seems very useable but I need to be able to have a portable method and without packages or a static executable it's not useable.

Do you have a link to the static executable?

---

### Post by Zugzwang on 2012-03-18
> **OrangeVixen said:**
> Do you have a link to the static executable?

No, you will need to build it yourself. Make sure you have the package "build-essential" installed, and the development packages for libgif and libX11. 

Then, modify the file "Makefile" of the library. Use an editor that keeps tabs as they are - they have a special semantics! 

In the line "LFLAGS += -lgif -L/usr/X11R6/lib -lX11", add "-static" as first parameter after the "+=".

The Makefile has a small problem that you will also need to fix. The Line "$(LINK) $(LFLAGS) -o $@ $(OBJS)" must be changed to "$(LINK) -o $@ $(OBJS) $(LFLAGS)", so the "$(LFLAGS)" are last - keep the TAB in front of the line.

Afterwards, you can run "make clean" and "make" in the directory. The executable "pdf417_enc" should be statically linked now. Verify this by running "ldd pdf417_enc".

You should build pdf417_enc on a machine running a 32-bit version of Ubuntu, as otherwise you'll obtain a 64-bit executable. Building a 32-bit version on a 64-bit computer is a bit tricky, but doable.

---

### Post by OrangeVixen on 2012-03-19
Okay, thanks I know how to compile stuff... but I just need the python code to be portable to most platforms that have that program instead of asking every user to compile something. :/

PS that program really needs to be updated, it doesn't really use X, just libgif.

---

