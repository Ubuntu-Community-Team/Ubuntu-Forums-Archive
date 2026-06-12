---
title: "What library or tool to use for printing?"
date: 2008-03-11
forum: Programming Talk
---

### Post by cronholio on 2008-03-11
I am currently developing a wxWidgets app that needs some very basic printing function (should print only a few lines of text). The wxWidgets printing system is giving me a hard time and I figure I don't really have to use it, so what library or external tool could I use to just print a simple text?

---

### Post by rbprogrammer on 2008-03-11
try googling something like:
[INDENT]
c++ printing
linux print command
[/INDENT]
etc, etc....

when i did it i found this:
[INDENT][http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=ot8&q=linux+command+to+print&btnG=Search](http://www.google.com/search?hl=en&safe=off&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=ot8&q=linux+command+to+print&btnG=Search)[/INDENT]
but more importantly:
[INDENT][http://tldp.org/HOWTO/Printing-Usage-HOWTO-2.html](http://tldp.org/HOWTO/Printing-Usage-HOWTO-2.html)[/INDENT]

the later might help you with printing, probably if you used the system() function with it.

hope that helps, i dont have too much expertise with printers since i can never get mine to work under ubuntu.

---

### Post by geraldm on 2008-03-11
I can print a basic page from ghostscript, version 8.60
Useage: gslp0 filename
The printer is a winprinter.

The command script:
#!/bin/bash
#gslp0 - send a page in raster format to the printer
gs -sOutputFile=/dev/lp0 -sDEVICE=gdi $1 &

Gerald

---

### Post by dwblas on 2008-03-11
You can also send text directly to the print spooler.  Most languages have a method to open and write to lpr.  Alternatively you can write to a file, close the file and use a system call "lpr file_to_print".  You can also use /dev/lp0 but the print spooler won't screw up enough to cause a reboot to get the printer to work again.

---

### Post by slavik on 2008-03-11
> **dwblas said:**
> You can also send text directly to the print spooler.  Most languages have a method to open and write to lpr.  Alternatively you can write to a file, close the file and use a system call "lpr file_to_print".  You can also use /dev/lp0 but the print spooler won't screw up enough to cause a reboot to get the printer to work again.
```
echo "some text" | lpr
```

---

### Post by cronholio on 2008-03-12
Thanks for all your help. I will try now which of these things work for me.

---

