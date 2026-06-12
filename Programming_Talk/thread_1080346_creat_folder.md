---
title: "creat folder?"
date: 2009-02-25
forum: Programming Talk
---

### Post by bamdad on 2009-02-25
hi guys,

i was wondering, how can i create folders using my c++ code? i currently use the fstream class to create the text files in general but i have to create folders manually so i'd be happy if someone helped me out.

P.S im am by no means an expert in c++ programming :">

---

### Post by yannos on 2009-02-25
Never tried it, but I've found this:
[http://www.brainbell.com/tutorials/C++/Creating_A_Directory.htm](http://www.brainbell.com/tutorials/C++/Creating_A_Directory.htm)

---

### Post by bamdad on 2009-02-25
thanks for the helpful link. but since i do not care about portability, i was wondering if linux(like windows) has any headers or modules for this purpose

---

### Post by Zugzwang on 2009-02-25
> **bamdad said:**
> thanks for the helpful link. but since i do not care about portability, i was wondering if linux(like windows) has any headers or modules for this purpose

That can also be found on the page linked to by yannos. So read it!

---

### Post by dwhitney67 on 2009-02-25
> **bamdad said:**
> thanks for the helpful link. but since i do not care about portability, i was wondering if linux(like windows) has any headers or modules for this purpose

The way to do it in Linux is to use mkdir(); this is what is described in the link provided by yannos.

Here's a list of some other library functions that can be used to deal with directories and files:
[LIST]
[*]rmdir()
[*]unlink()
[*]stat()
[/LIST]

View the man-pages when you need to learn about a particular library function's API.

---

### Post by geirha on 2009-02-25
The man-pages for the standard c library isn't installed by default, so if you haven't already, install [manpages-dev](apt:manpages-dev) and read mkdir's man-page with ```
man 2 mkdir
``` or search for the manpage on [http://manpages.ubuntu.com](http://manpages.ubuntu.com)

---

### Post by bamdad on 2009-02-26
thanks for all the replies, i did read yannos' page. guess i didnt pay enough attention i thought its just for portable programs :lolflag:

---

