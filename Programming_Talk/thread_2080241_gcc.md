---
title: "gcc"
date: 2012-11-03
forum: Programming Talk
---

### Post by thedardanius on 2012-11-03
hey,
 
Lately Im using BASS sound API for linux programming. BUt I get undefined reference errors during compiling, meaning that my linking has failed. How doI link with gcc?? And preferably without command line if possible. Also, what are makefiles and how do you combine them in your project???

---

### Post by slavik on 2012-11-03
install the right -dev packages needed, then add -l for the proper libraries.

---

### Post by thedardanius on 2012-11-03
what do you mean with -I

---

### Post by thedardanius on 2012-11-04
People please,
Im using code::blocks and g++/gcc. How do I link .so libraries to my project? Im totally new to gcc, I just figured out how to compile. But linking... and preferable withing the IDE, not command line linkning/ compiling.

---

### Post by MG&amp;TL on 2012-11-04
IDEs differ. Sorry, you're going to have to look that up, unless there's a Code::Blocks user around here.

From gcc, you'll need to add appropriate flags. For instance:

```
gcc <insert filenames here> -lBASS
```

---

