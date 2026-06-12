---
title: "beginner scripting do scripts"
date: 2012-01-11
forum: Programming Talk
---

### Post by pigmentty on 2012-01-11
Ok, so when i used windows i liked incredibly much autohotkey [www.autohotkey.com](www.autohotkey.com)
The coding was incredibly simple and powerful, i had a script in my startup that went something like this

1 read settings.txt and store in variable %state%
2 if %state% = 1 
2.1 msgbox timeout=10s "ABORTING /n run=cancel" 
2.2 if buttonpress=ok or buttonpress=timeout 
2.2.1 exitapp
3 else
3.1 msgbox timeout=10s "RUNNING /n run=wait,ok"
3.2 if buttonpress=cancel
3.2.1 exitapp
4 loop all files in folder of script
4.1 if filename<>scriptname and filename<>settings.txt
4.1.1 run file
5 exitapp
(note code in ahk is not like the above, i just made something that is easy to understand by coders)

if i have a project to make, i put all my shortcuts in the script folder, like notes, the app i use(or the project and when it runs it uses that app), editor for the project and stuff like that

soo here are my worries, how do i create a script in ubuntu? i tried to make files that run in terminal or ask to be run in terminal and no matter what extension i gave them they just sit there and wait to be edited by the txt editor... i found in some of the ubuntu folders a file that asked to be run, basically when i want to create a script i just copy that file, delete everything inside it and copy in it what i want it to run (also change the name of the script)
q1 how do i create a script that asks to be run in terminal?
q2 can i create something like the above? with message boxes and other 
variables?

---

### Post by pigmentty on 2012-01-11
ohh yeah, i forgot in the script i also save the new state in the settings.txt XD 
soo if last time i started my computer i worked, now the script will start my working apps, and if last time i started my computer i did not work now it will not start my apps

---

### Post by mörgæs on 2012-01-11
Moved to Programming Talk.

---

### Post by ofnuts on 2012-01-11
> **pigmentty said:**
> Ok, so when i used windows i liked incredibly much autohotkey [www.autohotkey.com]("http://www.autohotkey.com")
The coding was incredibly simple and powerful, i had a script in my startup that went something like this

1 read settings.txt and store in variable %state%
2 if %state% = 1 
2.1 msgbox timeout=10s "ABORTING /n run=cancel" 
2.2 if buttonpress=ok or buttonpress=timeout 
2.2.1 exitapp
3 else
3.1 msgbox timeout=10s "RUNNING /n run=wait,ok"
3.2 if buttonpress=cancel
3.2.1 exitapp
4 loop all files in folder of script
4.1 if filename<>scriptname and filename<>settings.txt
4.1.1 run file
5 exitapp
(note code in ahk is not like the above, i just made something that is easy to understand by coders)

if i have a project to make, i put all my shortcuts in the script folder, like notes, the app i use(or the project and when it runs it uses that app), editor for the project and stuff like that

soo here are my worries, how do i create a script in ubuntu? i tried to make files that run in terminal or ask to be run in terminal and no matter what extension i gave them they just sit there and wait to be edited by the txt editor... i found in some of the ubuntu folders a file that asked to be run, basically when i want to create a script i just copy that file, delete everything inside it and copy in it what i want it to run (also change the name of the script)
q1 how do i create a script that asks to be run in terminal?
q2 can i create something like the above? with message boxes and other 
variables?
To run a script file in a terminal(or elsewhere) without explicitly specifying which interpreter to use to run it, you need to:

[LIST=1]
[*] Make the first line of the file contain: "#! /path/to/interpreter" (usually "[FONT=Courier New]#! /bin/sh[/FONT]", "[FONT=Courier New]#! /usr/bin/python[/FONT]" or "[FONT=Courier New]#! /bin/bash[/FONT]"  and
[*]make the file executable by setting its "executable" flag: "chmod +x *the_script_file*"
[/LIST]
The rest of the instructions will now depend on the interpreter/language you choose.

---

