---
title: "[SOLVED] Help creating nautilus script"
date: 2008-03-31
forum: Programming Talk
---

### Post by brennydoogles on 2008-03-31
I am trying to write a nautilus script to allow me to right click a java class and test it in terminal. right now I have ```
#!/bin/bash
gnome-terminal --command=java $NAUTILUS_SCRIPT_CURRENT_URI/$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
```
But that doesn't seem to be working. Any ideas?

---

### Post by heikaman on 2008-03-31
try this
```
#!/bin/sh
gnome-terminal --execute java `basename $1 .class`
```

---

### Post by brennydoogles on 2008-03-31
> **heikaman said:**
> try this
```
#!/bin/sh
gnome-terminal --execute java `basename $1 .class`
```

That works!! The only problem is that the terminal immediately  closes after the class is run, which means that you can't always see the last output of the class. Any ideas?

---

### Post by heikaman on 2008-03-31
> **brennydoogles said:**
> That works!! The only problem is that the terminal immediately  closes after the class is run, which means that you can't always see the last output of the class. Any ideas?

yeah a couple of ideas, 
1- you can add a System.in.read() to your class, not really practical.
2- use xterm instead of gnome-terminal try this
```

#!/bin/sh
xterm -hold -e java `basename $1 .class`
```

the -hold option keeps the terminal window around until you close it i couldn't  find something like this for the gnome-terminal.

this should work fine, try it :)

---

### Post by nanotube on 2008-03-31
> **heikaman said:**
> yeah a couple of ideas, 
1- you can add a System.in.read() to your class, not really practical.
2- use xterm instead of gnome-terminal try this
```

#!/bin/sh
xterm -hold -e java `basename $1 .class`
```

the -hold option keeps the terminal window around until you close it i couldn't  find something like this for the gnome-terminal.

this should work fine, try it :)

instead of resorting to xterm, why not add a sleep or a read to the commandline? e.g.:

```
#!/bin/sh
gnome-terminal --execute java `basename $1 .class`; sleep 10
```

or

```
#!/bin/sh
gnome-terminal --execute java `basename $1 .class`; read bla
```

the former will sleep for 10 seconds after the java command finishes, the latter will wait for you to hit the enter key. (it will actually read your input into the $bla variable... but you wouldn't care about that :) ).

---

### Post by heikaman on 2008-04-01
> **nanotube said:**
> instead of resorting to xterm, why not add a sleep or a read to the commandline?
actually i tried something like this and it didn't work, i used cat

```
#!/bin/sh
gnome-terminal --execute java `basename $1 .class`; cat
```

and after reading your post i tried sleep and read but it doesn't work. ](*,)

---

### Post by brennydoogles on 2008-04-03
> **heikaman said:**
> actually i tried something like this and it didn't work, i used cat

```
#!/bin/sh
gnome-terminal --execute java `basename $1 .class`; cat
```

and after reading your post i tried sleep and read but it doesn't work. ](*,)

I will give this a try when I get home, and post back. Thanks for the help all!

---

### Post by nanotube on 2008-04-03
> **heikaman said:**
> actually i tried something like this and it didn't work, i used cat

```
#!/bin/sh
gnome-terminal --execute java `basename $1 .class`; cat
```

and after reading your post i tried sleep and read but it doesn't work. ](*,)

huh... so what does it do? just exits immediately as if that stuff wasn't there? hmm... maybe it needs an escape before the ;? or maybe the whole thing needs to be quoted?

ah yes... i tried it. it seems that anything after ; is interpreted as part of the next command, and doesn't get swallowed into the --execute. quoting it results in an error to... well, xterm it is, then :)

---

### Post by heikaman on 2008-04-03
> **nanotube said:**
> 
ah yes... i tried it. it seems that anything after ; is interpreted as part of the next command, and doesn't get swallowed into the --execute. quoting it results in an error to... well, xterm it is, then :)

told u so...:biggrin:

---

### Post by nanotube on 2008-04-03
> **heikaman said:**
> told u so...:biggrin:

indeed! :lolflag:

---

