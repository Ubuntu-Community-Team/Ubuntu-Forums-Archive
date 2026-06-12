---
title: "Runing a program using g++?"
date: 2007-07-28
forum: Programming Talk
---

### Post by Yes on 2007-07-28
I've successfully compiled a C++ source using g++, but now I need to know how to run it.  Is there an option to run the program after it's been compiled?

Thanks.

---

### Post by Paul820 on 2007-07-28
Yes, to run it you have to go to the terminal, enter the path to your file, and type: ./theNameOfYourFile so if your file is HelloWorld type: ./HelloWorld

---

### Post by Yes on 2007-07-28
Great, thanks! 

Is there any way to make it compile the file, and then run it, all in one command?

---

### Post by slavik on 2007-07-28
g++ -o prog prog.cpp; ./prog

but as a single command, no.

---

### Post by AlexThomson_NZ on 2007-07-28
If you are using a makefile (you should probably look at doing this) you can put ./programe_name after the $(CC) line to start it automatically

---

### Post by Paul820 on 2007-07-28
If you don't want to keep typing the full path to your file, you can get nautilus-open-terminal from synaptic or sudo apt-get nautilus-open-terminal. Wherever you are in a folder etc, if you right click you can select open terminal from that path. I find it invaluable when writing console programs. Just thought it might come in handy for you  :)

---

