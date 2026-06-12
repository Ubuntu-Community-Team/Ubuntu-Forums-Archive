---
title: "php ajax and images"
date: 2010-01-03
forum: Programming Talk
---

### Post by korvirlol on 2010-01-03
Hi there,

Im not even sure if this is possible, but here is my scenario:

Im using some graphing software to visually represent different things for a web app im working on. There are many different types of graphs, but this isnt the problem - the graphs are working well.

What i trying to do is make each graph accessbile with ajax, so the user can view all the different types of graphs with different data without reloading the page, and this is where the problem is.

Its calling the graphs properly, and it is parsing the graphs properly, but returning the graph to the page isnt working. The graphing software im using uses the php GD library to draw the graph, so essentially, the ajax request is trying to return an image.

I didnt expect this to work initially, and i dont even know if its possible. The ajax request the image in its binary form (which i expected) and the page cannot interpret it. Things ive tried:

Updating the src of an <img /> element
Updating the innerhtml of a div with the raw image code

... and i dont know what else to try.

Any ideas?

---

### Post by Hellkeepa on 2010-01-03
HELLo!

You don't need to use AJAX in this sitaution, just use a JS to change the src attribute of the image tag you use to show the graph with.
KISS, in other words. ;-)

Quick, and dirty, example:
[html]<a href="graph.php?id=2" onclick="document.getElementById ('graph').src = this.href; return false;">Show graph 2</a>
<img src="graph.php?id=1" id="graph" />[/html]

Happy codin'!

---

### Post by korvirlol on 2010-01-03
oh, i posted before your edit... let me look at that

---

### Post by korvirlol on 2010-01-03
yep, thats what i needed.

Thanks very much for the advice.

KISS are words to live by

---

### Post by Hellkeepa on 2010-01-03
HELLo!

Hehe, indeed they are. :-)
You're welcome, and good luck on your project.

Happy codin'!

---

