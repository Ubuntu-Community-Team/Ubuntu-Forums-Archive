---
title: "cat ip - strange writing"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-18
yeah so I am looking around and I try to concatenate a file called ip and a lot of strange alien-glyphics came up and now in that terminal I am typing this bizarre font.  What is it and how do I make it normal?

---

### Post by halitech on 2008-09-18
if you close and reopen the terminal does it still happen? if so, can you post a screenshot so we can see what you mean?

---

### Post by ggaaron on 2008-09-18
Yeah, it happens sometimes (cat /dev/urandom for example does it sometimes to me). Only thing that I could have done was restart in case of terminal and reopen in case of X console.

---

### Post by adamogardner on 2008-09-18
> **halitech said:**
> if you close and reopen the terminal does it still happen? if so, can you post a screenshot so we can see what you mean?

I'm guessing that restarting the Gnome-terminal will fix it but I'll wait and use another in the meanwhile  just to see if I can't figure it out.

---

### Post by Titan8990 on 2008-09-18
This is common if the file is not readable by the terminal. For example, if you cat a .png it will screw your terminal until you close and reopen it.

---

### Post by Locutus_of_Borg on 2008-09-18
cat is really only useful on text

---

### Post by nowshining on 2008-09-18
> **ggaaron said:**
> Yeah, it happens sometimes (cat /dev/urandom for example does it sometimes to me). Only thing that I could have done was restart in case of terminal and reopen in case of X console.

i tried that on Kgutsy and i get the first part but hitting ctrl+c to stop it returns everything back to normal..

---

### Post by adamogardner on 2008-09-18
> **Locutus_of_Borg said:**
> cat is really only useful on text

the first half of it is text

---

### Post by ggaaron on 2008-09-18
I've written sometimes it did this for me. Rarely though,

---

### Post by Therion on 2008-09-18
[IMG]http://www.dolcevitapets.com/blog/upload/2007/10/cat-like-typing-detected.gif[/IMG]

---

