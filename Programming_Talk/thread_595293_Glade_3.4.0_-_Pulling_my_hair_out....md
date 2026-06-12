---
title: "Glade 3.4.0 - Pulling my hair out..."
date: 2007-10-28
forum: Programming Talk
---

### Post by chris.zeman on 2007-10-28
...and I don't have that much to begin with!!! :lolflag:

I installed Anjuta 2.2.0 and Glade 3.4.0 using Synaptic. I created a simple interface in Glade, but can't figure out how to build the source code for the interface. I keep reading online that you're supposed to click "Build Source", but I can't find it anywhere. :confused: On top of that, Anuta doesn't seem to have Glade integrated as I've seen online. How do I set that up?

Once I am able to pass this hurdle, how do I go about including the interface in my program? There is a line in main.c that defines the glade file, but then there is code that generates a window. Do I need that code?

Thank you,
Chris

---

### Post by tageiru on 2007-10-28
You shouldn't build the source code for the interface. It is easier (and much more dynamic) to use libglade and let it generate the user interface at runtime from the XML file.

[http://www.jamesh.id.au/software/libglade/](http://www.jamesh.id.au/software/libglade/)

Read the second paragraph carefully, or you will end up pulling even more hair out when the UI callbacks doesn't work.

---

### Post by chris.zeman on 2007-10-28
Thank you very much!!! That is exactly what I needed! I'll start gluing my hair back on now. :)

Thank you!!!!
Chris

---

### Post by kh_naba on 2007-10-29
> On top of that, Anuta doesn't seem to have Glade integrated as I've seen online. 
> How do I set that up?
> 
Get anjuta 2.2.2 from [http://anjuta.org/downloads](http://anjuta.org/downloads) repository. You will get the integration.

---

