---
title: "compiling Mappy map editor"
date: 2011-02-02
forum: Packaging and Compiling Programs
---

### Post by pieman711 on 2011-02-02
A long time ago I wrote a few programs, mainly computer games in Blitz Basic (a BASIC compiler) that came bundled with a map editor called mappy.
 
I've decided to learn a real language and settled on C++ following the learn C++ in 21 days tutorial ([http://newdata.box.sk/bx/c/](http://newdata.box.sk/bx/c/)) with the aim of eventually translating my old games in to C++ and hopefully getting them to run on Ubuntu. 
 
I was hoping to use mappy again and notice it has been compiled and run in linux before [http://membres.multimania.fr/edorul/SDLMappye.htm](http://membres.multimania.fr/edorul/SDLMappye.htm), however I'm having some trouble. 
 
This is what I've done so far...
-installed allegro from source and downloaded the source for mappy.c
-installed code::blocks as an IDE
-opened mappy.c in code::blocks and changed the compiler settings to include the `allegro-config --libs` in the linker settings
-compiled, this gave a lot of warnings about lines being 'deprecated' but no errors
-ran from code::blocks, this gives a allegro #11 error, segfault and closes automatically.
 
I'm still quite new to all of this and have already learnd a lot in the last few days however this has got me stumped. To make things worse I dont have the internet on my computer at the moment so can only check up what to next occasionally. I'll copy the compling log onto a usb and put it up here next time I'm near the net. Any suggestions in the meantime?
 
EDIT->> here is the link to the original Mappy page.... [http://tilemap.co.uk/mappy.php](http://tilemap.co.uk/mappy.php)

---

### Post by pieman711 on 2011-02-03
[FONT=Times New Roman][SIZE=3][FONT=Calibri]Here is the error when compling in COde::blocks:[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][FONT=Calibri][SIZE=3][/SIZE][/FONT][/FONT] 
[FONT=Times New Roman][/FONT] 
[FONT=Times New Roman][SIZE=3][FONT=Calibri]Compiling: /home/pieman/Downloads/cpp/Mappy/mappy.c[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]/home/pieman/Downloads/cpp/Mappy/mappy.c: In function ‘GetScreen’:[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]/home/pieman/Downloads/cpp/Mappy/mappy.c:497: warning: ‘text_mode’ is deprecated (declared at /usr/local/include/allegro/alcompat.h:155)[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]/home/pieman/Downloads/cpp/Mappy/mappy.c: In function ‘NewProject’:[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]/home/pieman/Downloads/cpp/Mappy/mappy.c:1023: warning: ‘file_select’ is deprecated (declared at /usr/local/include/allegro/alcompat.h:141)[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]/home/pieman/Downloads/cpp/Mappy/mappy.c: In function ‘ShowHelp1’:[/FONT][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][FONT=Calibri]/home/pieman/Downloads/cpp/Mappy/mappy.c:1143: warning: ‘text_mode’ is deprecated (declared at /usr/local/include/allegro/alcompat.h:155)[/FONT][/SIZE][/FONT]
[FONT=Calibri]/home/pieman/Downloads/cpp/Mappy/mappy.c:1144: warning: ‘textout’ is deprecated (declared at /usr/local/include/allegro/alcompat.h:157)[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri]...[/FONT]
[FONT=Calibri]The lots more of very similar stuff...[/FONT]
[FONT=Calibri]and finally[/FONT]
[FONT=Calibri]...[/FONT]
[FONT=Calibri][/FONT] 
[FONT=Calibri][/FONT] 
[FONT=Calibri][FONT=Times New Roman]/home/pieman/Downloads/cpp/Mappy/mappy.c:6324: warning: ‘text_mode’ is deprecated (declared at /usr/local/include/allegro/alcompat.h:155)[/FONT]
[FONT=Times New Roman]Linking console executable: /home/pieman/Downloads/cpp/Mappy/mappy[/FONT]
[FONT=Times New Roman]Process terminated with status 0 (0 minutes, 2 seconds)[/FONT]
[FONT=Times New Roman]0 errors, 323 warnings[/FONT]
[FONT=Times New Roman] [/FONT]
[FONT=Times New Roman]Checking for existence: /home/pieman/Downloads/cpp/Mappy/mappy[/FONT][FONT=Times New Roman][/FONT]
[FONT=Times New Roman]Executing: xterm -T '/home/pieman/Downloads/cpp/Mappy/mappy' -e /usr/bin/cb_console_runner "/home/pieman/Downloads/cpp/Mappy/mappy" (in /home/pieman/Downloads/cpp/Mappy)[/FONT]
[FONT=Times New Roman]Process terminated with status 0 (0 minutes, 4 seconds)[/FONT]
[/FONT]

---

### Post by SevenMachines on 2011-02-03
Deprecated is a warning, 
"Your code is old, the libraries you are using have changed and you need to update how you use them, you have some time before the functions you're using are dropped"

They arent in themselves a problem for compiling/running

Sadly, i can't crash the program myself.

With mappy version 101s on i386 (ubuntu natty)
```
$ gcc -o mappy mappy.c -lalleg -lX11  -lm -lXxf86vm -lXcursor -lXpm -lXext -lX11 -lpthread -ldl
$ ./mappy
```runs fine.

You would need to generate a backtrace to understand exactly whats going wrong
```
$ gdb ./mappy
(gdb) run
...
Segmentation fault
(gdb) backtrace full
```(The debugger is your only friend in a crisis :))
Your ide should use gdb in a more friendly way i imagine

---

### Post by pieman711 on 2011-02-06
I've no idea what I did differently but when I re complied it again (not sure how many times I've tried it now) all of a sudden it worked. it still crashes occasionally with a seg fault but mostly runs fine. I've gone to using the windows version in WINE as its a bit more stable and has a nicer GUI anyway. 
Thanks for the help anyway, I may play around with the older version when I'm a bit more competent with C.

---

