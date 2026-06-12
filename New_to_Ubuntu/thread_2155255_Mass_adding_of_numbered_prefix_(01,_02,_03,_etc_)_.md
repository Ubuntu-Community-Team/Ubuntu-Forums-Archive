---
title: "Mass adding of numbered prefix (01, 02, 03, etc ) to files in a folder"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by neuroimage on 2013-06-17
Hello Linux Experts,

I would like to add a numbered prefixes to all my folders in a folder.

For example, I have the following
Picture_a.jpg
Picture_b.jpg
Picture_c.jpg
Picture_d.jpg
Picture_e.jpg

I want to have 

01_Picture_a.jpg
02_Picture_b.jpg
03_Picture_c.jpg
04_Picture_d.jpg
05_Picture_e.jpg

I have 91 photos that I want to rename in this fashion. Thanks!

---

### Post by Cheesemill on 2013-06-17
You could use [PyRenamer]("apt://pyrenamer").

---

### Post by steeldriver on 2013-06-17
or if you like shell scripting, maybe a loop like this (the 'echo' in it stops it from actually doing the renames - kind of like a dry run)

```

i=0; for pic in *.jpg; do printf -v prfx '%02d' ${i}; echo mv "${pic}" "${prfx}_${pic}"; ((++i)); done
mv Picture_a.jpg 00_Picture_a.jpg
mv Picture_b.jpg 01_Picture_b.jpg
mv Picture_c.jpg 02_Picture_c.jpg
mv Picture_d.jpg 03_Picture_d.jpg
mv Picture_e.jpg 04_Picture_e.jpg
mv Picture_f.jpg 05_Picture_f.jpg

```

---

