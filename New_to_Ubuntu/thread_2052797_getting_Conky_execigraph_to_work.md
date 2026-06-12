---
title: "getting Conky execigraph to work"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by facetoe on 2012-09-04
Hello I'm new to Ubuntu and am trying to set up a Conky display on my desktop. I've run into a problem with execigraph though, and I was hoping someone could point me in the right direction. 

I've got a simple script in ruby:

```
print rand(100)
```It works fine for the execgraph: ```
 ${execgraph  ~/myStuff/conky/test.rb}
``` and prints a nice graph. 

When I try and run ```
${execigraph 5  ~/myStuff/conky/test.rb}
``` I don't get anything at all. Any ideas where I'm going wrong?

I'm running Ubuntu 12.04

Any help appreciated!

---

### Post by djyoung4 on 2012-09-04
can you start your conky from a terminal and post what happens in the output.  I'm also reposting your question in the main [conky thread]("http://ubuntuforums.org/showthread.php?p=12216527#post12216527")

---

### Post by facetoe on 2012-09-04
I get this in the terminal:

```
Conky: desktop window (2000095) is subwindow of root window (af)
Conky: window type - normal
Conky: drawing to created window (0x4e00001)
Conky: drawing to double buffer
```

No errors or anything, the graph just doesn't show up.

---

### Post by facetoe on 2012-09-04
Maybe someone could post a working execigraph example and I can try it on my machine.

---

