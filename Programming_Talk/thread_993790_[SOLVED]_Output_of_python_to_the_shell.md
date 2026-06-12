---
title: "[SOLVED] Output of python to the shell"
date: 2008-11-26
forum: Programming Talk
---

### Post by talsemgeest on 2008-11-26
I am completely new to programming and have chosen python as my first language of choice. I have done a few tutorials and have a reasonable grip on the language (for a complete noob) and feel I am ready to write my first real program.

Just a quick question though, obvious and stupid: how to I get my python program to run commands? I'm hoping that from the input given, my program will generate a command and then run it as though I had typed it into the bash terminal.

So, hopefully this will be an easy question with a quick answer, thank you in advance for all help.

---

### Post by Tony Flury on 2008-11-26
Look at the **os.system** builtin function - that will spawn a new shell and execute a command.

Note that this is a new shell - you will have to think about things like environment variables etc, and also any commands you execute wont appear in command history etc.

---

### Post by Greyed on 2008-11-26
os.system() is the most simplistic way to do it but not the best.

Popen and its objects are more complex and the generally accepted manner to do it.

---

### Post by talsemgeest on 2008-11-26
OK, can you give me some example code for the os.system() function? I tend to learn better that way.

Thanks!

---

### Post by Greyed on 2008-11-26
[php]
import os
print("---------- os.listdir()")
for file in os.listdir('.'):
    print file
print("---------- os.system('ls -1')")
os.system('ls -1')
[/php]

---

### Post by talsemgeest on 2008-11-26
Thank you both for your help, it is greatly appreciated. I think that should be all I need.

---

