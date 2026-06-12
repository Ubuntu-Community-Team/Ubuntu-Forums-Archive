---
title: "Vectorizing plug-in for GIMP"
date: 2009-01-23
forum: Programming Talk
---

### Post by Mohamedzv2 on 2009-01-23
Hey, I've been recently getting annoyed at GIMP for it's being mostly pixel editting with no vector support except the format, so I've been thinking about making a vector plug-in myself for it.

However I've run into a bit of a dillema. Should I use C++, which I am currently learning, or learn GIMP's scripting language?

And also, if I should use C++, can you pinpoint me to a link about the method of vectorizing?

---

### Post by bruce89 on 2009-01-24
GIMP doesn't use C++, it uses C.

C would make most sense for this, but GIMP isn't supposed to be a vector program, that's what Inkscape is for.

---

### Post by mssever on 2009-01-24
GIMP is also scriptable in Python and Scheme(I think). However, as bruce89 said, Inkscape is for vector graphics. GIMP isn't. And trying to make it into a vector program would probably be very difficult, and a waste of time.

---

### Post by Kilon on 2009-01-24
> **Mohamedzv2 said:**
> Hey, I've been recently getting annoyed at GIMP for it's being mostly pixel editting with no vector support except the format, so I've been thinking about making a vector plug-in myself for it.

However I've run into a bit of a dillema. Should I use C++, which I am currently learning, or learn GIMP's scripting language?

And also, if I should use C++, can you pinpoint me to a link about the method of vectorizing?


Well I have to disagree with the above posters. The whole purpose of the plugin architecture is to bring unique features. I see no reason why someone should not implement vector capabilities to GIMP. 

Choosing between the script language and C will be matter of speed. C will execute with more speed but the script will take less time to develop. You could combine both , use C where speed is required and script when you want to finish coding as fast as possible.  

It wont be an easy task , but I am sure you will finds loads of tutorials for programming vector graphics. If you manage to complete your task , I am sure many GIMP users will worship you like God. 

PS: 

Make sure none is actually trying this. If there is unite with him and you will see your task becoming alot easier. Actually I am partly interested as well.If you take your task seriously and need some part done in python I am sure I can help. I know C and coded in c/C++ but do not touch it anymore as now I develop in JAVA and python.

---

### Post by Mohamedzv2 on 2009-01-24
Thanks for the replies. Right now, I know that GIMP isn't natively a vector program, however for me, it has many features over inkscape, and the interface it has is much better for me, especially as I am a GFX designer.

Now, I'm not far into learning C++, so I guess I could start learning C instead for the time being. And I'll be sure to contact you, Kilon, if I need a python programmer, I will contact you. Now to go find some tuts about the formula for vectorization

---

### Post by antony_css on 2009-03-01
If you just want to "cartoonize" your photos, I suggest AutoTrace:
[http://autotrace.sourceforge.net/index.html]("http://autotrace.sourceforge.net/index.html")
which also provides Frontline as the frontend.

---

