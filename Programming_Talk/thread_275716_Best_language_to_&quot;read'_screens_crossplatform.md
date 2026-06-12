---
title: "Best language to &quot;read' screens crossplatform?"
date: 2006-10-11
forum: Programming Talk
---

### Post by balloons on 2006-10-11
I've done simple ocr solutions for different projects, but I'm attempting to write a small ocr app with cross platform support. The ultimate end would be to do some simple OCR from a single codebase, running on mulitple platforms. Does anyone know the best language to do this in? I'm looking for something quick, so a high-level language would be nicer for proof of concept. I've considered C/C++, python, perl.. Also, all of those with wxWidgets. Anyone have any experience? I need to read a pixel color on X11 screen or in Windows, as well as possibly generating a checksum of a pixelarea, etc. a gui could be foregone, at first, but eventually a SIMPLE gui with some labels, and buttons would be required. Thanks!

---

### Post by slavik on 2006-10-11
have you looked into Java or .NET/Mono?

---

### Post by DavidBell on 2006-10-12
You need a function that gets the memory address of the entire picture area you want in one hit. For eg in windows you can use GetDIBits or others and it's fairly quick, but if you get each pixel individually using GetPixel it's extremely slow.

My guess both GTK & wxWidgets would have some object that wraps images and has equivalents of these functions.

If I was feeling brave enough to attempt OCR I would be using C/C++ for speed, and would use in-memory bitmaps with no reference to the screen at all.

DB

---

### Post by balloons on 2006-10-12
well sounds like i stick to my tried and true C. I know about Blit on windows, but I hadn't thought of Mono. I'll check that out, as well as reading x11 screens from memory. something new for me. Love linux, forced to program in windows. why? sigh

---

