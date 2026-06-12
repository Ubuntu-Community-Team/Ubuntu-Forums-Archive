---
title: "What language/GUI type for Multiplatform App?"
date: 2007-05-03
forum: Programming Talk
---

### Post by Kimm on 2007-05-03
I'm starting on a project for biologist that wish to track/record wildlife and I want it to be multiplatform.

At the moment, Python is my main choise in language (althought I dont know it, I am willing to learn, but I am drifting between wxWidgets and pyGTK/Glade.
pyGTK and Glade would be great, since it would accelerate the work, but I'm not sure if Glade can run on Windows?

Suggestions would be appretiated! :)

---

### Post by scottious on 2007-05-03
Java.  I've always had an easy development time with Java and it's very cross platform.  Python is good too although I'm not too familiar with it's cross platform capabilities.

---

### Post by msumurph on 2007-05-03
I prefer wxPython for cross-platform GUI programming, mainly for lazy reasons: listboxes, printing, and spreadsheet-grids are easy to code.  For WYSIWYG design, check out [wxGlade]("http://wxglade.sourceforge.net").  wxPython also provides mostly native widgets so apps look native on all platforms.

As for pyGTK, Glade does run on windows ([http://gladewin32.sourceforge.net)](http://gladewin32.sourceforge.net)).  It is also packaged with the Win installer of Mono, for those programming on .Net.

---

