---
title: "Ctrl + Alt + Supr Ubuntu Version?"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by Gecast on 2011-11-18
Well, I have been using Ubuntu lately and I've tried to learn from it but... there so many information and I don't know where to put my doubts except for this place.

First one. When the computer crashes and get freeze, there exists an option to kill process as happens with Windows?

And the second one, I want to learn more about Linux in all of their versions (personally, I want to take the hard way and I've been doing it since like 1-2 years ago but... where I can enter to learn, provide some help, there are so many things ~

Well, that's all, I'll be waiting.

---

### Post by tartalo on 2011-11-18
You are looking for the "system monitor", it's different in each Desktop Environment, but it's generally an application that shows you the running processes and allows you to kill them.

You can also launch xkill and click on the misbehaving application to kill it.

Another good tool is htop, it works from a command line.

There are plenty of options.

Por cierto, en Ingles te van a  entender mejor si dices ctrl+alt+del ;)

---

### Post by Gecast on 2011-11-18
Jajaja, cierto, gracias que no lo había notado ~ 

Buscaré acerca de esas aplicaciones. Pero por ejemplo ¿esas aplicaciones como las puedo llamar si la computadora se queda congelada? Alt + F2? Esa es la parte que me da duda, porque en ocasiones se me congela la computadora y me queda la duda.

Thanks ~

---

### Post by Jguy on 2011-11-18
Using Alt+F2 Key combination brings up a 'Run Process' window. typing 'xkill' will turn your cursor into an 'X' allowing you to click on the process windows on the GUI to send the KILL command do it, effectively ending it.

---

### Post by tartalo on 2011-11-18
> **Gecast said:**
> ¿esas aplicaciones como las puedo llamar si la computadora se queda congelada?

- Para comprobar si alguna aplicación está consumiendo demasiados recursos htop es excelente, instalalo. Si el entorno grafico no responde pasa a una terminal de texto con ctrl+alt+F1 (hasta F6 son terminales de texto, F7 es el entorno grafico)

- Para comprobar si la memoria está en buen estado, en GRUB (El menu del principio donde te deja elegir Windows y Linux) hay una opción llamada  MemTest.

---

### Post by Cavsfan on 2011-11-18
> **Jguy said:**
> Using Alt+F2 Key combination brings up a 'Run Process' window. typing 'xkill' will turn your cursor into an 'X' allowing you to click on the process windows on the GUI to send the KILL command do it, effectively ending it.

Sweet! Thanks for that info. I am making a note of that. :D
Ubuntu - always something to learn.

---

### Post by Gecast on 2011-11-18
Amé lo de ctrl + alt + F1-6 ~ jajaja, for sure I love it ~

---

### Post by Gecast on 2011-11-18
> **tartalo said:**
> 
- Para comprobar si la memoria está en buen estado, en GRUB (El menu del principio donde te deja elegir Windows y Linux) hay una opción llamada  MemTest.

¿Para qué sirve revisar si la memoria esta en buen estado? Siempre me he quedado con esa duda.

---

### Post by tartalo on 2011-11-18
Si una memoria está en mal estado hará que el ordenador se cuelgue o se congele aleatoriamente y se debe reemplazar.

---

### Post by Pferra on 2011-12-30
Hi there guys. Just in case some of you are wandering around, where can I find other "everyday Linux tricks" like these, for newbies?

You know, there are so many tricks that are obvious for the experienced user that sometimes are not explained or even not documented...

Anyway, this thread was very enlightening.

Regards (and Happy New Year!)

Pablo

---

### Post by Henkdroid on 2011-12-31
If you press (left)Alt + SysRq + K then all your processes will be killed and you will be logged out. This is useful when something goes wrong.

---

