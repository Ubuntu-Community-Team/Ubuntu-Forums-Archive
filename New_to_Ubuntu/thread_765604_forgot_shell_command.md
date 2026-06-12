---
title: "forgot shell command"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Troca on 2008-04-24
I googeld earlyer today and found a gr8 command you could do in the shell that would give you a cross when executed, then you could click any app with that cross and it would give you the shell command to start that app. anyone know the command for this ?

---

### Post by Vadi on 2008-04-24
Try typing "history" in the terminal, see if you find it there.

---

### Post by Troca on 2008-04-24
Thank you !!! i found it ;)

it is  

xprop | grep WM_CLASS

---

### Post by ardchoille42 on 2008-04-24
> **Troca said:**
> Thank you !!! i found it ;)

it is  

xprop | grep WM_CLASS

How about: ```
xprop | grep WM_COMMAND
```

You can also make some bash scripts, make a menu entry for them, and then execute them from the menu entry.

appclass.sh:
```

#!/bin/bash
myclass=`xprop | grep WM_CLASS`
zenity --info --title="App Class Information" --text="$myclass"

```


appcommand.sh:
```

#!/bin/bash
mycommand=`xprop | grep WM_COMMAND`
zenity --info --title="App Command Information" --text="$mycommand"

```


apppid.sh:
```

#!/bin/bash
mypid=`xprop | grep _NET_WM_PID`
zenity --info --title="App PID Information" --text="$mypid"

```

---

### Post by Vadi on 2008-04-24
> **Troca said:**
> Thank you !!! i found it ;)

it is  

xprop | grep WM_CLASS

Thank you too! I guess this'll come in handy someday. Copied over to my tomboy note of useful commands :)

---

