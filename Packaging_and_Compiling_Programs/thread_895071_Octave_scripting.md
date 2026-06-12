---
title: "Octave scripting"
date: 2008-08-19
forum: Packaging and Compiling Programs
---

### Post by 7raTEYdCql on 2008-08-19
Can i type a Octave script in a editor and then execute it in the octave terminal. How do you do it, what is the extension?

---

### Post by cszikszoy on 2008-08-20
I'm not sure exactly what you mean, but if you add this line to the top of your octave script:

```
#! /bin/octave -qf
```

you can execute the script without invoking octave.  It basically just becomes the same thing as a python or shell program.

You can also access command line arguments from your script using the variable argv().

That should give you a good start to do some more research.

---

