---
title: "[SOLVED] How to change the Eclipse used console"
date: 2008-04-02
forum: Programming Talk
---

### Post by schmendrick on 2008-04-02
Hi,


is there a possibility to change the console that is used by eclipse? When i start my (console) program from within eclipse, the output will be sent to the window/tab named "console". 

do i have the option to channel that somehow to a normal gnome-terminal like you can to in KDEVELOP with konsole? 

i tried a lucky shot opened the Run Dialog, going to common and there under "Standard Input and Output" checking "File" and defined "gnome-terminal" there and started, but this did not do the trick.

i am using eclipse europa with the lastest CDT (=C++)

code on!

---

### Post by schmendrick on 2008-04-03
*bump*

no eclipse users here :confused:

is nobody else disliking the output of eclipse on this eclipse-console-window?

---

### Post by nick_h on 2008-04-03
I use Eclipse but I just use the console supplied.  You can detach it and have it in a separate window if you want.

---

### Post by schmendrick on 2008-04-04
thanks nick_h, but sorry i dont get it:

what do you mean by detaching the console? meaning having it in a seperate window, and not inside the eclipse - window context? that would be exactly what i want but i do not find a HowTo how to do that.


my main problem is that the console output gets overwritten with debugging info when i am debugging as soon as i start hovering with the mouse over a variable. 
i want to have that debugging info and the console seperate.

i want to have the console "floating" as a seperate window and not attached somewhere in one (or more) of the perspectives.

---

### Post by jespdj on 2008-04-04
Right-click on the tab "Console".
You'll see a popup-menu, one of the options is "Detach".
Click that option.

---

### Post by schmendrick on 2008-04-07
whoops.... yes that works, thx, all too simple   ](*,)  :-\"

i also figured out how to put the output to an "external" console window.

for other people trying the same, here's how:

open up your console, check which file it is with "who" on the commandline, and then under "Run" > "Open Debug Dialog" > "Common" > "Check 'File'", put the file for the newly opened console there (example: /dev/pts/0) and start debugging. 
all your output will also be written to that console now.

---

