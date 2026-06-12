---
title: "compile &amp; run openGL: right-click script"
date: 2009-02-23
forum: Packaging and Compiling Programs
---

### Post by Shady3D on 2009-02-23
hi all, i don't know if this is the right thread but i will give it a try.

i want to make a Nautilus script to compile and run cpp open gl program, so i made a bash file in Nautilus script's folder and put 
```

#!/bin/bash
g++ $NAUTILUS_SCRIPT_SELECTED_URIS -lGL -lGLU -lglut -o out;
./out;
rm out

```

so when i try to use this it doesn't work, and i don't have any clues, thx in advance

---

### Post by geirha on 2009-02-26
g++ does not accpet URIs. Try with $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS instead.

---

