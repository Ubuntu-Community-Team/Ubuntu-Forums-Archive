---
title: "[SOLVED] How to open a file from Terminal?"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by projecthikari on 2008-07-17
Alright, lets say i go into a directory, and I got all my files showing and I want to open a file from the terminal...

Lets say I want to open "Sonicicon.jpg"
How would I go about doing that?

---

### Post by Inxsible on 2008-07-17
> **projecthikari said:**
> Alright, lets say i go into a directory, and I got all my files showing and I want to open a file from the terminal...

Lets say I want to open "Sonicicon.jpg"
How would I go about doing that?you have to choose the appropriate editor for the type of file and use that. So for your example, since its a jpg file, you would have something like ```
mirage Sonicicon.jpg
```where mirage is the image viewer I use. also not that you will have to be in the directory where Sonicicon.jpg lies for the above command to work. If you do not want to cd to that directory, you will have to provide the entire path to the file.

---

### Post by sisco311 on 2008-07-17
```
**gnome-open** Sonicicon.jpg
``` opens the item specified by the url with the preferred 
GNOME app for that file/mime-type.

[http://ubuntu.wordpress.com/2006/12/16/gnome-open-open-anything-from-the-command-line/](http://ubuntu.wordpress.com/2006/12/16/gnome-open-open-anything-from-the-command-line/)

---

### Post by projecthikari on 2008-07-17
*Big hugs for both of you* Thanks!!

I love learning new things. :KS

---

### Post by hyper_ch on 2008-07-17
don't worry, there's still plenty to learn for all of us ;)

---

### Post by JoshuaRL on 2008-07-17
Thank you Sisco311, that even works in XFCE without Gnome.  Cools.

---

### Post by projecthikari on 2008-07-17
> **hyper_ch said:**
> don't worry, there's still plenty to learn for all of us ;)

Oh yes. \\:D/
I like your signature, by the way. It's clever.

---

### Post by hyper_ch on 2008-07-17
btw, use the thread tools to mark this one as solved ;)

---

### Post by projecthikari on 2008-07-17
Just learned THAT too! XD

---

