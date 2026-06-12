---
title: "quick qosmic question"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by fontenot_1031 on 2008-05-23
Quick question I built the program qosmic from source with no errors :) but I am not for sure how to make it executable in any directory in the command line.  I've installed the base in /usr/local/share/qosmic/ where the executables are and I have a link of the qosmic executable in that local/share/qosmic directory linked to /usr/local/bin so I can execute it anywhere.  The only problem is since just the one executable is the program looks for the flam3 palettes in ./flam3/flam3-palettes.xml.  Even if I linked that (besides cluttering up /usr/local/bin) I would have to link all of the other executables to it and so on.
Is there a quick (and tidy) workaround for this type of problem?

THIS THREAD IS AN ALLITERATION AWESOME!

---

### Post by perillux on 2008-05-23
not 100% sure, but you could try this:
instead of having the program look for **./flam3/flam3-palettes.xml**
type the entire path, so if the folder flam3 was in your home folder it would be something like **~/flam3/flam3-palettes.xml**
*in case you didn't know, using '~' at the front of path, points to your home directory.*

I'm thinking your problem is because when you run it in a different directory, your current path is different from the actual programs, and the program is using a relative path.  So using an absolute path should fix it.

---

### Post by fontenot_1031 on 2008-05-28
> **perillux said:**
> not 100% sure, but you could try this:
instead of having the program look for **./flam3/flam3-palettes.xml**
type the entire path, so if the folder flam3 was in your home folder it would be something like **~/flam3/flam3-palettes.xml**
*in case you didn't know, using '~' at the front of path, points to your home directory.*

I'm thinking your problem is because when you run it in a different directory, your current path is different from the actual programs, and the program is using a relative path.  So using an absolute path should fix it.

Alright though it looks like I'll have to recompile the program and type in the correct path myself.  I wish Ubuntu had a package for this program.

---

