---
title: "First attempt at programming"
date: 2008-07-02
forum: Programming Talk
---

### Post by blazercist on 2008-07-02
Ok heres what I want to do:

I want to create a simple GUI program that appears in the notification area.  

The application will only have three options:

option 1 will run a bash script that I've created.
option 2 will run another bash script that I've created.
option 3 will exit the program.

The only other thing of interest is that the bash scripts require sudo permissions so it would be nice if the program prompted the user for a password after selecting one of the first two options.

The last time I programmed something was, well, never.  I have created GUI's in VB on windows but that was about 10 years ago when I was 13.  So I would appreciate if someone could tell me which tool is best to use and I would appreciate even more if someone could help me out and be specific and give examples of how to do this.  Thanks.

---

### Post by milosz.galazka on 2008-07-02
You could use *gksudo* command in your bash script...
How to create gui see [http://www.tkdocs.com/tutorial/index.html](http://www.tkdocs.com/tutorial/index.html)

If you want to create gui which looks the same as other applications on dektop then use python, ruby, ... so you could use GTK, QT...

---

### Post by blazercist on 2008-07-02
> **milosz.galazka said:**
> You could use *gksudo* command in bash your script...
How to create gui see [http://www.tcl.tk/man/tcl8.5/tutorial/tcltutorial.html](http://www.tcl.tk/man/tcl8.5/tutorial/tcltutorial.html)

If you want to create gui which looks the same as other applications on dektop then use python, ruby, ... so you could use GTK, QT...

thanks! but i dont see anything about making the program run in the notification area?

---

### Post by milosz.galazka on 2008-07-02
> **blazercist said:**
> thanks! but i dont see anything about making the program run in the notification area?

for example [http://ubuntuforums.org/showthread.php?t=821429](http://ubuntuforums.org/showthread.php?t=821429) :)
or [http://marcin.af.gliwice.pl/if-then-else-20070121143245](http://marcin.af.gliwice.pl/if-then-else-20070121143245)

---

### Post by blazercist on 2008-07-02
Ok so I lazily used glade to create GUI with two buttons, but they do nothing, how do I get them to run the bash script when pressed?

---

### Post by Can+~ on 2008-07-02
Since you're using bash scripts, you could do something easier with zenity:

[PHP]zenity --list --radiolist --text="What do you want to run?" --column="Sel" --column="Application Name" TRUE "Application 1" FALSE "Application 2"[/PHP]

I would suggest staying away from GUI-related applications for a while; your learning apps won't need a fancy gui on top to run.

---

### Post by milosz.galazka on 2008-07-03
If you used python then
[http://www.velocityreviews.com/forums/t359776-execute-a-shell-script-from-a-python-script.html](http://www.velocityreviews.com/forums/t359776-execute-a-shell-script-from-a-python-script.html)
and 
[http://forums.fedoraforum.org/showthread.php?t=89216](http://forums.fedoraforum.org/showthread.php?t=89216)

---

