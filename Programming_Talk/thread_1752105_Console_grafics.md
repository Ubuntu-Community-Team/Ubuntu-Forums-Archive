---
title: "Console grafics"
date: 2011-05-07
forum: Programming Talk
---

### Post by johnny3k on 2011-05-07
Hi all!
I try find Hello world (messageboxa example) for console. 
I mean graphics dialogs for console example. 

I want try code graphics for console.

---

### Post by hakermania on 2011-05-07
Hello!
Run this in order to show what you want in GUI using zenity:
```
zenity --info --text "Hello World"
```

---

### Post by johnny3k on 2011-05-07
cool and nice! ;) but is not what  i need.
i found example on ruby with rubycurses
[http://totalrecall.wordpress.com/2008/11/25/rubycurses-some-code-samples/](http://totalrecall.wordpress.com/2008/11/25/rubycurses-some-code-samples/)
like that
[http://totalrecall.files.wordpress.com/2008/11/nc_messagebox_input.png](http://totalrecall.files.wordpress.com/2008/11/nc_messagebox_input.png)

but i don't know ruby i try learn c++
oh..

---

### Post by Tony Flury on 2011-05-07
so use ncurses for C/C++

---

### Post by MAFoElffen on 2011-05-07
> **johnny3k said:**
> cool and nice! ;) but is not what  i need.
i found example on ruby with rubycurses
[http://totalrecall.wordpress.com/2008/11/25/rubycurses-some-code-samples/](http://totalrecall.wordpress.com/2008/11/25/rubycurses-some-code-samples/)
like that
[http://totalrecall.files.wordpress.com/2008/11/nc_messagebox_input.png](http://totalrecall.files.wordpress.com/2008/11/nc_messagebox_input.png)

but i don't know ruby i try learn c++
oh..
You said "consiole graphics," so are you looking at something more along the lines of this that the server team came up with?
[http://ubuntuforums.org/showthread.php?t=1709253&highlight=server+ab+screen](http://ubuntuforums.org/showthread.php?t=1709253&highlight=server+ab+screen)
Look at the first post and you can figure out what he's using from it... He describes.

---

### Post by johnny3k on 2011-05-08
i found answer!:popcorn:
[http://www.linuxdoc.org/HOWTO/NCURSES-Programming-HOWTO/helloworld.html](http://www.linuxdoc.org/HOWTO/NCURSES-Programming-HOWTO/helloworld.html)

---

