---
title: "can i use other apps in my apps"
date: 2008-10-09
forum: Programming Talk
---

### Post by luckydeveloper on 2008-10-09
hi,

i have an app. in that, i want to provider a terminal inside its interface. i mean ..my app must contain a terminal/bash shell inside. can i do that.. is it possible?how do i do that...

---

### Post by dwhitney67 on 2008-10-09
You will need to elaborate more as to what you need.  Start by listing the language you will be using.

Here's a simple bash-script (an application!), that prints "Hello World".  Before printing, it also launches a gnome-terminal.  So does this meet your criteria for an app within an app?

```
#/bin/bash

gnome-terminal &
echo Hello World
exit 0
```

---

### Post by kknd on 2008-10-09
You can use vte (virtual terminal emulator) to embed an terminal into a GTK aplication. Geany does that!

---

### Post by EnGorDiaz on 2008-10-09
> **luckydeveloper said:**
> hi,

i have an app. in that, i want to provider a terminal inside its interface. i mean ..my app must contain a terminal/bash shell inside. can i do that.. is it possible?how do i do that...

i really dont get you question but there are a lot of ways to do this you have to be more specific

---

### Post by snova on 2008-10-09
It's possible. It really depends on *how* you want to go about doing it, and exactly what you want to do.

If you want to use a terminal as another widget in your GUI, it varies with the widget toolkit. KDE applications have the Konsole KPart available to them, and Gnome has something else, for example.

If you want to open a terminal and run a command in it automatically, simply run the terminal program with the proper command line arguments to run the specified program. Konsole can do it like this:

```
konsole -e <command>
```

---

