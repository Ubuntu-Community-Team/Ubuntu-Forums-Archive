---
title: "How to Compile and Run my c and C++ applications ?"
date: 2006-04-03
forum: Programming Talk
---

### Post by kolichina_s_s on 2006-04-03
Hi,

I finally got ubuntu and also add the gcc,g++ packages successfully. I made a simple Helloworld.c program. 

How should i compile and Run it.

Please tell me i am new to linux...:confused:

KSS

---

### Post by rmjokers on 2006-04-03
You could try:

make helloworld

or

gcc -o helloworld helloworld.c

and then run it by typing:

./helloworld

---

### Post by kolichina_s_s on 2006-04-03
[QUOTE=rmjokers]You could try:

make helloworld

or

gcc -o helloworld helloworld.c

and then run it by typing:

./helloworld[/QUOTE]

Thank q This worked , at last after 4 years of my work on windows](*,)  i have run my first application on *nux :D .

Thanks a lot

---

### Post by hod139 on 2006-04-03
Make sure you install the build-essential package, not just gcc, g++.  You will most likely run into problems later if you don't.

---

