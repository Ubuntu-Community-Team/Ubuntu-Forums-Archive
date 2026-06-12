---
title: "geany error:  start-script could not be created"
date: 2008-01-03
forum: Programming Talk
---

### Post by poisonblack on 2008-01-03
Hi all.
I am using Geany for my C++ programs, but each time I try executing a program, it says:

13:20:53: Failed to execute "/media/sda1/Ascii" (start-script could not be created).

The program compiles and builds successfully.But it just doesn't execute.

Any help.??

---

### Post by moma on 2008-01-03
Can you move your project to another location.

Take a copy of your project folder and files to $HOME/tmp/. Start Geany, load the project, build & run. What happens?

See also: [http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418](http://ubuntuforums.org/showthread.php?p=3627418&posted=1#post3627418)

---

### Post by poisonblack on 2008-01-03
Hey, That worked.!!Thanks.:KS :KS
Just moved the file to /home/poisonblack/ directory and it executed perfectly.!
Has it got something to do with NTFS partition.??The initial location of the file was on a windows partition, afterall.[http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

