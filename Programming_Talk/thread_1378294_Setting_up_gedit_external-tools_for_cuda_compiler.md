---
title: "Setting up gedit external-tools for cuda compiler"
date: 2010-01-11
forum: Programming Talk
---

### Post by Aiyen on 2010-01-11
Hello all 
I am trying to use the external-tools plugin of gedit to compile and run programs I write using the CUDA compiler. These are my settings for it. 


```
#!/bin/sh
# [Gedit Tool]
# Name=nvcc compile with g++-4.3
# Shortcut=F5
# Languages=
# Applicability=all
# Output=output-panel
# Input=nothing
# Save-files=nothing

nvcc $GEDIT_CURRENT_DOCUMENT_NAME --compiler-bindir=/home/aiyen/CUDA_Test_Folder/ -o ${GEDIT_CURRENT_DOCUMENT_NAME%.*}
```

But I keep getting this error

```
Running tool: nvcc compile with g++-4.3

/home/aiyen/.gnome2/gedit/tools/shortcut-for-nvcc-under-g++-4.3: 11: nvcc: not found

Exited: 32512
```

When I am trying to call nvcc in a terminal there is no problem so what do I need to change to make it accept nvcc calls in gedit as well? 
Thanks in advance

---

### Post by meborc on 2010-01-14
you might want to refer to nvcc with its full path...

---

### Post by Aiyen on 2010-01-14
Thanks for your reply meborc
I tried to do that, but then it comes with an error saying I don't have root. Since I am not the sharpest linux user ever, I would also not mind an example or link to where it is shown.

---

### Post by meborc on 2010-01-15
> **Aiyen said:**
> Thanks for your reply meborc
I tried to do that, but then it comes with an error saying I don't have root. Since I am not the sharpest linux user ever, I would also not mind an example or link to where it is shown.

i don't know why you would need root, but you can run the command with "sudo" to get root

---

### Post by Aiyen on 2010-01-15
I figured out my mistake, the path was enough to use, but I had typed it in wrong. 
Many thanks for your help!

---

