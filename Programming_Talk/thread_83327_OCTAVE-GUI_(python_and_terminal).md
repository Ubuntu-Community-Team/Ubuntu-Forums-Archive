---
title: "OCTAVE-GUI (python and terminal)"
date: 2005-10-28
forum: Programming Talk
---

### Post by gheorghe_pop on 2005-10-28
Hello.
I want to build a gui-frontend for octave. I have a design for the interface (for now in my mind only). It's made with glade and to programm the application I will use python.
 The first probblem that i encounter is the following:
How can I build a small console in my application using python and glade? 
In the console octave will start by default. And when the user run's a octave program evry line from the program will be passed to the console and executed.

Documentation,examples all is wellcome.

10x

---

### Post by WarGoX on 2007-11-30
Mira para embeber una consola dentro de una aplicación utilizando GTK debes utilizar la librería libvte (Virtual Terminal Emulator) esta librería está escrita en C y tiene por supuesto ports para Python y Perl que yo conozca quizás para otros lenguajes, pero al menos para estos dos los he probado, Te dejo adjunto un ejemplo bien sencillo que lo que hace es crear una ventana con GTK y embeber dentro de ella una consola, espero que te sirva.

Cualquier duda puedes escribirme a [email]betancourt.jorge@gmail.com[/email]

slds

---

