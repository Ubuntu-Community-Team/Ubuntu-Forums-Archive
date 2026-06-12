---
title: "Open many console windows"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by doomstone on 2008-07-12
Hello i'm trying to create a way that i by running a simpel script can open 25 new console windows with a spicified command.

That i need to run is a chatbot for the game age of conan.
much like an irc bot.

My bots are coded in C# and loads a files named config.xml by refering to the name "config.xml".
I have tyed to add is as a seasson, but den i get the message "Could not find file "/home/doomstone/Config.xml"."
it should be looking in /home/doomstone/Bots/Helpbot/Config.xml,
and it dose that if i run it from "/home/doomstone/Bots/Helpbot/"
with "mono Doombot.exe".

Are there any way i can create a script that can help me do this?
The reason that i don't want the windows hiden, that i sometimes want to look in the console window se see what happens :D

---

### Post by Bodsda on 2008-07-12
A C# programmer should really know how to use a for loop

i like python so here goes

```
python
>>>import os
>>>for i in range(25):
...    os.system('gnome-terminal')
...

```

Thats using the interactive python prompt (note the >>> and ... are put there by the interpreter)

if you wanted a script

```

#! /bin/bash/env python

import os

for i in range(25):
    os.system('gnome-terminal')

```

Hope this was what you wanted

Bodsda

P.S
Remember linux is case sensitive

"config.xml"

is not the same as

"Config.xml"

---

### Post by gate on 2008-07-12
Open a terminal
```


echo '#!/bin/bash' >> open_many.bash
echo 'COUNT=25' >> open_many.bash
echo '# bash while loop' >> open_many.bash
echo 'while [ $COUNT -gt 0 ]; do' >> open_many.bash
echo '     gnome-terminal &' >> open_many.bash
echo '    let COUNT=COUNT-1' >> open_many.bash
echo 'done' >> open_many.bash

chmod +x open_many.bash

```

to run:
```

./open_many.bash

```

---

### Post by Bodsda on 2008-07-12
wow, see the difference, simplicity vs bash

---

### Post by doomstone on 2008-07-12
Hmm there are 2 things there are forgotten in both your scripts :( maby i diden't dicribet it clear enoth.

Each program must run with "/home/doomstone/Bots/" as the "run from dir"
And they each have a diffrent argument. such as.
mono Doombot.exe Ymir
mono Doombot.exe Dagon

---

### Post by ibuclaw on 2008-07-12
> **gate said:**
> Open a terminal
```


echo '#!/bin/bash' >> open_many.bash
echo 'COUNT=25' >> open_many.bash
echo '# bash while loop' >> open_many.bash
echo 'while [ $COUNT -gt 0 ]; do' >> open_many.bash
echo '     gnome-terminal &' >> open_many.bash
echo '    let COUNT=COUNT-1' >> open_many.bash
echo 'done' >> open_many.bash

chmod +x open_many.bash

```

to run:
```

./open_many.bash

```

??

You are kidding me, right?
```
i=0 && while [ $i -lt 25 ]; do gnome-terminal & let "i++"; done
```

:lolflag:

---

### Post by Bodsda on 2008-07-12
Your not making much sense, you asked how to open 25 terminals, you want each terminal to run a certain program?

---

### Post by doomstone on 2008-07-12
> **Bodsda said:**
> Your not making much sense, you asked how to open 25 terminals, you want each terminal to run a certain program?

Yes, or they all run the same program just with diffrent argument.

---

### Post by Bodsda on 2008-07-12
just add it in

```

#! /bin/bash/env python

import os

for i in range(25):
    os.system('gnome-terminal && <Command>')

```

---

### Post by doomstone on 2008-07-12
> **Bodsda said:**
> just add it in

```

#! /bin/bash/env python

import os

for i in range(25):
    os.system('gnome-terminal && <Command>')

```

os.system('gnome-terminal && mono Doombot.exe Ymir')
This will open a new gnome terminal, but run "mono Doombot.exe Ymir" in the same terminal that the python script was executed

---

### Post by doomstone on 2008-07-12
Found a way 
os.system('gnome-terminal --execute mono Doombot.exe Ymir')

thanks for your help guys

---

