---
title: "C++ running exe"
date: 2008-06-19
forum: Packaging and Compiling Programs
---

### Post by Rhaddad on 2008-06-19
Hello, i made a C++ program and i want to run it however i'm not sure how.

The program compiled succssfully and it made a file with extension .0

sorry i am new to ubuntu development

---

### Post by Hubi17 on 2008-06-19
what compiler did you use?

using g++ ( from gcc ) normally like so:

```
g++ sourcefile.cpp
```

creates a file called a.out
this can be run by typing:

```
./a.out
```

hope this helps.

---

### Post by Fertech on 2008-06-21
i'm using g++ and in some code i get an error. here is the result of what i get when i type the code;

[http://www.cprogramming.com/cgi-bin/source/source.cgi?action=Category&CID=2]("http://www.cprogramming.com/cgi-bin/source/source.cgi?action=Category&CID=2")


fertech@fertech-desktop:~$ g++ Battle_ship.cpp
Battle_ship.cpp:5:19: error: conio.h: No such file or directory
Battle_ship.cpp: In function &#8216;void targeting()&#8217;:
Battle_ship.cpp:101: error: &#8216;getche&#8217; was not declared in this scope
Battle_ship.cpp: In function &#8216;void quitGame()&#8217;:
Battle_ship.cpp:18828: error: &#8216;getche&#8217; was not declared in this scope
Battle_ship.cpp: In function &#8216;void checkShips()&#8217;:
Battle_ship.cpp:23539: error: &#8216;getche&#8217; was not declared in this scope
fertech@fertech-desktop:~$

---

### Post by Hubi17 on 2008-06-22
I believe the problem is with *conio.h*

afaik that is a MS-DOS only header file, so its functions, like *getche* dont work under *nix

*Edit:*
Yep that was the problem.
I just changed every occurrence of *getche()* with *getchar()* and it compiles and seems to run. However I did not test it, so dont know if it works as intended.

---

### Post by Fertech on 2008-06-22
ok i fix most of the errors,but what do i do with this error:

fertech@fertech-desktop:~$ g++ ship.cpp
ship.cpp:5:19: error: conio.h: No such file or directory
fertech@fertech-desktop:~$
 do i take it out or do i need to replace it with something else
i remove it and this the results i get::

fertech@fertech-desktop:~$ ./a.out
Battle Ship
By Michael Marques
These are the posible positions:
11 ,12 ,13 ,14 ,15 ,16 ,17 ,18
21 ,22 ,23 ,24 ,25 ,26 ,27 ,28
31 ,32 ,33 ,34 ,35 ,36 ,37 ,38
41 ,42 ,43 ,44 ,45 ,46 ,47 ,48
51 ,52 ,53 ,54 ,55 ,56 ,57 ,58
61 ,62 ,63 ,64 ,65 ,66 ,67 ,68
71 ,72 ,73 ,74 ,75 ,76 ,77 ,78
81 ,82 ,83 ,84 ,85 ,86 ,87 ,88
(3 spaces)Player 1 enter your Battle ship's poition:
position1:

so where is the graph

---

### Post by Hubi17 on 2008-06-22
Yes delete the *conio.h* header from the .cpp file, or just comment it out.

Graph? I dont think there is supposed to be a graph. The earlier link says its Battle Ship without a graphical interface. So I guess it shows the positions of each ship only with the coordinates that you posted.

---

### Post by Fertech on 2008-06-22
so how do i make a software. a regular program. im trying to make a scanner of my own that will scan for virus. i know c/c++,perl and java. just in java im using windows xp,but im having a hard time setting the path. for that i will just look into windows forums. also where can i find open source code, so i can play with the code.

---

### Post by Hubi17 on 2008-06-23
Im not entirely sure what you mean. Theoretically the *a.out* file is the program executable. About the paths, could it be that windows paths are c:\...
and linux paths are /home/...
For source code for a virus scanner, why dont you check out clamav.
[http://www.clamav.org/download/](http://www.clamav.org/download/)
you can download the source code and mess with it, or adapt it to your own program.

---

