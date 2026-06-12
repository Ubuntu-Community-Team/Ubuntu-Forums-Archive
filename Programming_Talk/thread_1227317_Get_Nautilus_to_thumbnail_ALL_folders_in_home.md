---
title: "Get Nautilus to thumbnail ALL folders in /home"
date: 2009-07-30
forum: Programming Talk
---

### Post by altonbr on 2009-07-30
Nautilus seems to thumbnail folders only when I enter the folder and sometimes that can look quite messy when there are hundreds of pictures.

Is there a bash or python script that can recursively thumbnail all my files in /home?

I don't care that it'd take a couple hours or take a couple gigs worth of space, I just want it done.

---

### Post by benj1 on 2009-07-30
i dont think i understand what you mean ???

---

### Post by ibuclaw on 2009-07-30
I don't have the time to write something at the moment.

But looking at the nautilus source, you can write a quick C program for this.
The function that you want is:
```
nautilus_file_get_icon(NautilusFile *file, int size, NautilusFileIconFlags flags);
```
That looks like it creates the thumbnail if it doesn't exist.

Regards
Iain

---

### Post by altonbr on 2009-07-30
> **tinivole said:**
> I don't have the time to write something at the moment.

But looking at the nautilus source, you can write a quick C program for this.
The function that you want is:
```
nautilus_file_get_icon(NautilusFile *file, int size, NautilusFileIconFlags flags);
```
That looks like it creates the thumbnail if it doesn't exist.

Regards
Iain

Thanks for your help, but I'm not that familiar with C.

Is there a program that can be ran from the command-line, e.g. in a BASH script?

---

### Post by altonbr on 2009-07-30
> **benj1 said:**
> i dont think i understand what you mean ???

I want to thumbnail every single photo and document on my /home partition instead of doing it manually by entering ever single directory I have.

e.g.
```
$ gnome-thumnbailer /home
```

---

