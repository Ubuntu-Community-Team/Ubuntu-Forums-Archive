---
title: "Getting OpenCV in Eclipse to not have errors. Ubuntu 12.04"
date: 2014-04-09
forum: Packaging and Compiling Programs
---

### Post by epicbattle on 2014-04-09
Pardon, I am new to programming/teaching self.

Getting these errors  "Symbol 'foo' could not be resolved". Where foo is the word underlined in the image. I am just trying to get OpenCV to work in eclipse. I believe I have all the proper libraries. OpenCV2.4.8. and that I set it up properly. If you look at the picture on the left it shows all the .h  and .hpp files that I have added to the project. So I don't know where to go from here. Any idea on what I am missing or what I could have goofed up? 

[ATTACH=CONFIG]251872[/ATTACH]

Thank you.

---

### Post by steeldriver on 2014-04-09
Symbol resolution errors come from the link phase - nothing to do with header files - so do you have all the appropriate **libraries** listed (Project --> Properties --> C/C++ Build --> Settings --> Libraries)? 

You can get a list of all the OpenCV + dependent libraries by running 

```
pkg-config --libs opencv
```

in a terminal. I *think* someone was working on a plugin so allow Eclipse to use the pkg-config system directly - otherwise it's all a bit of a PITA I'm afraid.

---

