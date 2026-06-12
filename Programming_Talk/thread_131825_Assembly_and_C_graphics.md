---
title: "Assembly and C graphics"
date: 2006-02-17
forum: Programming Talk
---

### Post by omerlh on 2006-02-17
Hello!
First, soon we start learn at school Assembly, of course under windows. I have Ubuntu 5.10. Can I program with it in windows Assembly? If not, what else I can do, except dual boot?
Second, I want to learn graphics under linux. There is good manual at the net?
Thanks,
Omer.

---

### Post by Gustav on 2006-02-17
If you mean that you want to program stuff with graphics you should look at SDL ([www.libsdl.org/)](www.libsdl.org/)). It's made for C but it's usable in many different languages.

For programming assembly you could use nasm

---

### Post by omerlh on 2006-02-17
I want to lern program in C with graphics, There is any lib for this?

---

### Post by nagilum on 2006-02-17
Depends on what you mean with graphics. Just creating applications with a GUI? Then you might look at GTK+, wxWidgets or QT. If you want to work with / manipulate 2D graphics (like JPGs, PNGs etc.) there are some libraries like ImageMagick or Imlib2 . And if you talk about 3D graphics there's for example OpenGL and SDL (which can do more than just 3D graphics).

Maybe you should give us a little more information on what you are interested in.

---

### Post by omerlh on 2006-02-19
All I wan't is a bite command line graphics. Using colurs, centering text, font of text, something like this. If you know dos.h and graphic.h in windows, that stuff I want to learn.

---

### Post by nagilum on 2006-02-19
Then ncurses is probably what you want.

---

### Post by ipssshh on 2010-04-01
Hi, Im new in Ubuntu.Can anyone plzz tell me how this following can be written in Ubuntu....

#include<stdio.h>
#include<graphics.h>
#include<abs.h>
void main()
{
 int gdrive=DETECT,gmode;
 initgraph(&gdrive,&gmode,"c:\\tc\\bgi");
.
.
.
.
}


If i write the same what would i put in place of "C:\\tc\\bgi",plzz tell me with some example and proper description if i need to install any softwere...

---

### Post by Zugzwang on 2010-04-01
> **ipssshh said:**
> Hi, Im new in Ubuntu.Can anyone plzz tell me how this following can be written in Ubuntu....


First of all, what you just did is called "thread hijacking" and "thread necromancing". It is common here to start your own thread if you have a question rather that posting to some very old thread.

Now to your question: The code you posted uses some functions that are only available in "Turbo C++", which is rather old. The question you are posting is somewhat recurring. See for example [here]("http://ubuntuforums.org/showthread.php?t=1422279&highlight=graphics.h") for an answer. In a nutshell, you will need to use different libraries and rewrite your program to get in running. Alternatively, you can always run "Turbo C++" in a dosbox if it is likely not to pay off to rewrite your application.

---

