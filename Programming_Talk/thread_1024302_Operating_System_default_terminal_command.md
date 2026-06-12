---
title: "Operating System default terminal command"
date: 2008-12-28
forum: Programming Talk
---

### Post by christoforever on 2008-12-28
So I'm writing a small IDE for my senior project(written in java) and after giving up hope of running an external program and giving it input through java's processbuilder and bufferedreader class's I decided to simply run the program through a terminal. I use ubuntu which comes with gnome so my terminal command is gnome-terminal and im sure kde has its own and xfce has their own... I'm wondering if there is a command that will work on any linux os that will launch the deafult terminal for that given os... and I do not want to use xterm.

Thanks in advance,

Christopher Dancy

p.s.

If anyone has ever tried using processbuilder and got it to run a program and give it input and have it produce output and then give it more input I would love to hear how you did it.

---

### Post by stroyan on 2008-12-28
Debian derivative distributions (and Fedora) have an /etc/alternatives directory
that contains generic versions of many commands.
You could start /etc/alternatives/x-terminal-emulator to get a terminal.
But the options to such commands are not standardized.
And not all linux distributions will have that feature.
See "man update-alternatives" for more details.

---

### Post by jamesstansell on 2008-12-28
> **christoforever said:**
> So I'm writing a small IDE for my senior project(written in java) and after giving up hope of running an external program and giving it input through java's processbuilder and bufferedreader class's I decided to simply run the program through a terminal. I use ubuntu which comes with gnome so my terminal command is gnome-terminal and im sure kde has its own and xfce has their own... I'm wondering if there is a command that will work on any linux os that will launch the deafult terminal for that given os... and I do not want to use xterm.

Thanks in advance,

Christopher Dancy

p.s.

If anyone has ever tried using processbuilder and got it to run a program and give it input and have it produce output and then give it more input I would love to hear how you did it.

For your processbuilder question, keep looking.  Java 6 made some improvements, but also there should be a number of sites with helpful information, and probably a project or two of interest at java.net.

It's curious that you don't want to use xterm, which is the one graphical terminal most likely to be found on any unix system.  You might check into the xdg-* family of commands.  But I'm not aware of one yet that opens a terminal.  xdg-open "opens a file or URL in the user’s preferred application" but that's not really what you want.

---

### Post by christoforever on 2008-12-28
I've searched the internet on topics for processbuilder and they all say/do the same thing. The problem comes when an external process wants input. The only way to do this that i've found is to know ahead of time how many arguments it wants then write those arguments to the process inputstream then watch the output spill out. There does not seem to be a clear way on how to read a line from the program and tell if the program wants input and they supply that input at runtime. I've searched and found nothing anywhere.

---

### Post by christoforever on 2008-12-29
It seems very funny to me.... I just opened up jedit and downloaded the console plugin to see the src and possibly understand how they do it. However upon running the console in jedit it does the exact same thing my program does!!! So I suspect that eclipse(which is what im trying to mimic) is using the jni libs to get the input and ouput correct for their console.

---

