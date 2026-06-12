---
title: "How to make a sh file to run a jar file?"
date: 2012-08-13
forum: New to Ubuntu
---

### Post by Com_2_Reset on 2012-08-13
Hello all,

I downloaded a RoboMind program. To run the program from command line:


[LIST=1]
[*]I go to Dir "Downloads" using [COLOR=Red]cd Downloads[/COLOR] command.
[*]Then to Dir "RoboMind" using [COLOR=Red]cd RoboMind[/COLOR] Command.
[*]Then Run RoboMind.Jar using [COLOR=Red]java -jar RoboMind.jar[/COLOR]
[/LIST]
It works fine.

My question is How to make a sh file to run the RoboMind.jar file?

---

### Post by ajgreeny on 2012-08-13
```
#!/bin/bash
java -jar /home/*username*/Downloads/RoboMind/RoboMind.jar
```should do it.  Make the shell script executable and then a double click will run it.

If all you want is a launcher you can write a **robomind.desktop** file with contents
```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=java -jar /home/user/Downloads/RoboMind/RoboMind.jar
Comment[en_GB]=Network transfer of files.
Name=RoboMind
Comment=<your comment>
Icon=/path/to/icon/file
``` make it executable again, and and put it in /usr/share/applications.  It should then appear in your menu (or dash, I think).

If you are really still using 10.10 you can right click on the desktop and choose to create a new launcher.  Use the full pathway command ```
java -jar /home/user/Downloads/RoboMind/RoboMind.jar
```and that should also work.

---

