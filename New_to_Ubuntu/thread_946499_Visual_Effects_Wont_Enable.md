---
title: "Visual Effects Wont Enable"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by wnishantha1 on 2008-10-13
I tried to install compiz fusion and it worked. It just wont show up on my desktop because my visual effects (right click on background > desktop background > Visual effects tab > super) this wont work because it said there was some kind of error that had occurred. I think this might be because my graphics card isn't made for stuff like this. What might be the problem?

Thanks for the help (:

---

### Post by SpenceMakesSense on 2008-10-13
make sure your graphics card is installe by going to system-admistration-hardware drivers

---

### Post by wnishantha1 on 2008-10-13
There is just a blank window. it has the task bar and everything but it doesent show any drivers...

---

### Post by wnishantha1 on 2008-10-13
it also says "No proprietary drivers are installed on this system"...?

---

### Post by NewJack on 2008-10-13
First off, what video card are you using?

---

### Post by wnishantha1 on 2008-10-13
I dont know but my computer is a unitron i thin because thats what the sticker says on it. i dont know that its from because i got it from a friend. just assume that he didnt change annything on it ok...

---

### Post by WWSmith36 on 2008-10-13
To find out what video card you are using.  Open a terminal and type

```
lspci | grep -i vga
```

---

### Post by wnishantha1 on 2008-10-13
I got this

nishantha@nishantha-desktop:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: S3 Inc. 86C410 Savage 2000 (rev 02)
nishantha@nishantha-desktop:~$

---

### Post by NewJack on 2008-10-13
Try this post:

[http://ubuntuforums.org/showthread.php?t=681064&highlight=Savage+2000](http://ubuntuforums.org/showthread.php?t=681064&highlight=Savage+2000)


These do not look good though:

[http://ubuntuforums.org/showthread.php?t=864446&highlight=Savage+2000](http://ubuntuforums.org/showthread.php?t=864446&highlight=Savage+2000)

[http://ubuntuforums.org/showthread.php?t=226247](http://ubuntuforums.org/showthread.php?t=226247)

---

