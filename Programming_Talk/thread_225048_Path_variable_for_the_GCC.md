---
title: "Path variable for the GCC?"
date: 2006-07-29
forum: Programming Talk
---

### Post by MrNelson on 2006-07-29
Hiya,

I've been using SuSe until recently (damn Novell buying it and all), and I've been used to typing 
```
gcc -c myFile.c -o myFile
```
but I tried doing this for a java file, and it said "error can't find bash command gcj".

Am I doing this wrong, or am I supposed to configure some environment/path variables for the GCC?

---

### Post by tseliot on 2006-07-29
moved to a more appropriate section

---

### Post by sirclaudio on 2006-07-29
Did you installed the gcj package? build-essential doesn't install this.

---

### Post by GeoMX on 2006-07-29
As sirclaudio pointed out, check whether you have gcj installed:

*$ aptitude show gcj*

Best wishes,
JJ (GeoMX).

---

