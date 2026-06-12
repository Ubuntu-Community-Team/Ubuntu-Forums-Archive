---
title: "Combine several pictures in certain order"
date: 2010-05-06
forum: Programming Talk
---

### Post by xtjacob on 2010-05-06
Hello, I need a script that will atomatically download and combine several pictures into a certain order. What is the best way of doing this (bash, python, etc.), and are there any tips that would help? I currently only know some perl, but any other scripting language would is fine.

---

### Post by MadCow108 on 2010-05-06
wget for downloading
montage from imagemagick for combining
[http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php) (also packaged)

---

### Post by xtjacob on 2010-05-06
I've looked into imagemagick before, but it didn't seem to let you put them in a certain order (when I mean order I mean layer-wise).

---

### Post by MadCow108 on 2010-05-06
what do you mean by order?
as far as I remember in montage they are added in the order of how they are given in the command line.
maybe you also should look at composite

and you can of course chain all the imagemagick tools together so you can do almost everything, you just need to look at enough docs :)

---

### Post by xtjacob on 2010-05-06
What I need to do is stack them on top of each other like you would with layers in Gimp or Photoshop. Some of the pictures are transparent, and some are not so I need them in a certain order.

---

### Post by MadCow108 on 2010-05-06
imagemagick can do that
your request its even as an example on the composite page...

here is a more detailed page:
[http://www.imagemagick.org/Usage/layers/](http://www.imagemagick.org/Usage/layers/)

if you do not want to use commandline tools there are bindings for a lot of languages including perl.

if you have a good reason not to use it please tell me so I can shut up ;)

---

### Post by xtjacob on 2010-05-06
Cool, that works! :guitar: Now I have another question. How can I have options like they choose a city and it downloads the pictures that are assigned to it?

---

