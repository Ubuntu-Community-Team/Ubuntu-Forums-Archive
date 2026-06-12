---
title: "script help"
date: 2020-11-22
forum: New to Ubuntu
---

### Post by rburkartjo on 2020-11-22
running 20.04
i have this script to output local weather
#!/bin/bash
curl [http://wttr.in](http://wttr.in)

however when i run i want to have terminal on maximum size
how do i do note terminal is normally set to open at smaller size and want to keep it that way only need change when run this script/tks

---

### Post by Holger_Gehrke on 2020-11-22
wmctrl might be what you want. 
```

wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz

```
used in a script will toggle the currently active window - that should be the terminal in which the shell that executes the script is running - to horizontally and vertically maximized and back.

Holger

---

### Post by rburkartjo on 2020-11-22
tks hol but didnt work

---

### Post by rburkartjo on 2020-11-22
okay i can get this script to work
gnome-terminal --window --maximize 
however when try to tie to the weather script the terminal opens maxed but cant get the weather script to run in it

---

### Post by &amp;KyT$0P# on 2020-11-23
Specify your script on command line of gnome-terminal -
```
gnome-terminal --window --maximize -- '[COLOR="#FF0000"]/full/path/to/your/script[/COLOR]'
```
replacing [FONT=Courier New][COLOR="#FF0000"]/full/path/to/your/script[/COLOR][/FONT] with that actual path (keep the quotes as shown in the code box).

With this method, the terminal might automatically close when the script is completed.  If you want to get the chance to review the output, you could add the line
```
read
```
at the end of your script to require pressing Enter to complete the script and thus close the terminal.

---

### Post by ActionParsnip on 2020-11-23
Make sure you mark your script as executable with:
```

chmod +x /full/path/to/your/script

```

---

### Post by TheFu on 2020-11-23
> **Holger_Gehrke said:**
> wmctrl might be what you want. 
```

wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz

```
used in a script will toggle the currently active window - that should be the terminal in which the shell that executes the script is running - to horizontally and vertically maximized and back.

Holger

Worked for me.  I use xterms.  
But I really need to set the font to a smaller size for that output to fit on one screen without wrapping.

---

### Post by rburkartjo on 2020-11-23
tks everyone for your input
here is the script that finally worked
#!/bin/bash
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
#!/bin/bash
'/home/ray/weather'

---

### Post by TheFu on 2020-11-23
> **rburkartjo said:**
> tks everyone for your input
here is the script that finally worked
```
#!/bin/bash
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
/home/ray/weather
```

is probably what you want and if you use curl to hit **/usr/bin/curl   [https://wttr.in/](https://wttr.in/)**
then just use,

```
#!/bin/bash
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
/usr/bin/curl   https://wttr.in/
 
``` to save a few extra processes from starting.

---

### Post by rburkartjo on 2020-11-24
tks fu

---

