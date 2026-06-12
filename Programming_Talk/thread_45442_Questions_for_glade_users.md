---
title: "Questions for glade users ?"
date: 2005-06-30
forum: Programming Talk
---

### Post by frodon on 2005-06-30
Hi

I want to develop a software with graphical interface and i want this software to be compatible with windows and linux. My software will only use serial port of the computer.
My first target is window (first need) so I would like to develop using C++ and glade on linux and compile C code with windows.
Is it possible to do it like that ?
If not is it possible using linux to compile my C code with windows as target and package a .exe for windows and how ?
Does gtk contains macros to drive serial port ?

thanks for any kind of answer.

---

### Post by superhac007 on 2005-07-01
For cross platform development look at the Mono Project.

[http://www.mono-project.com](http://www.mono-project.com)

---

### Post by m87 on 2005-07-04
[QUOTE=frodon]Hi

I want to develop a software with graphical interface and i want this software to be compatible with windows and linux. My software will only use serial port of the computer.
[/QUOTE]

if you really want it to be cross platform you should totally dive into gtk/glib and FORGET any function that's not standard library, and sometimes even the std lib functions are replaced by something else (e.g. glib has even functions like g_strstr() or g_strlen() which are the exact clones of the strstr() and strlen() funcs).

[QUOTE=frodon]My first target is window (first need) so I would like to develop using C++ and glade on linux and compile C code with windows.
Is it possible to do it like that ?[/QUOTE]

i can't see any point in using two different languages if you want that program really to be cross-platform, but 

[QUOTE=superhac007]For cross platform development look at the Mono Project.[/QUOTE]

you should check it out, but you'll have to learn a new language (C# is fine nowadays with the MONO framework), and of course you need the .NET framework installed on the windows machines.

[QUOTE=frodon]If not is it possible using linux to compile my C code with windows as target and package a .exe for windows and how ?[/QUOTE]

nope, there are no ways to compile into the win32 .exe format, you should use cygwin from a windows box, providing that you designed the software from a linux box.

[QUOTE=frodon]Does gtk contains macros to drive serial port ?[/QUOTE]

gtk is just the FRONT END, glib is the lowlevel library which is COMPULSORY for portability, but, no, none of the libs allow such thing.
AFAIK, there are no abstractions for doing such a lowlevel job, therefore it's kernel-specific, therefore you should write TWO backends, but it's not easy to learn so many libraries in a short time... gtk itself is a bit tricky when you begin

**EDIT: **Mono 1.2 will support Microsoft Whidbey, which itself supports serial port handling... another good reason to use Mono (i personally love it). The 1.2 is planned for releasing Q3/05... check this out [http://www.mono-project.com/Mono_Project_Roadmap#Mono_1.2](http://www.mono-project.com/Mono_Project_Roadmap#Mono_1.2) 

omfg, pardon me :( that was reeeally long! i hope you found that useful!

marco

---

### Post by frodon on 2005-07-20
thanks marco.

The big problem in my application, and for me it's why my software can't be compatible, is that the way to handle serial port is really different between linux and windows and I think I will spend less time to build 1 interface for each OS. 

Thanks for the really interesting informations that you gave me.

---

### Post by m87 on 2005-07-20
[QUOTE=frodon]thanks marco.

The big problem in my application, and for me it's why my software can't be compatible, is that the way to handle serial port is really different between linux and windows and I think I will spend less time to build 1 interface for each OS. 

Thanks for the really interesting informations that you gave me.[/QUOTE]

nope. the interface CAN BE portable. what's impossible to port is the backend, the real program, the thing that handles serial ports. and you could solve with A LOT of #ifdef's , or two separate programs... you can use the same UI.

that's why i suggested you mono. if you have patience you can wait for 1.2 release.

marco

---

### Post by frodon on 2005-07-20
[QUOTE=m87]the interface CAN BE portable[/QUOTE]Yes, sorry if I didn't explain well. Mono seems to be the best solution for my need, but indeed i have to look forward the 1.2 release, also i see there is a VB.net compiler embedded in mono ... it's interesting.
thanks for your time marco  :)

---

