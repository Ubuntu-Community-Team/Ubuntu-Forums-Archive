---
title: "Capturing a window's size, position and viewport on close"
date: 2008-12-21
forum: Programming Talk
---

### Post by tijuana on 2008-12-21
Hi!

I'm new to linux, but I've been told it's highly customizable; so I'd like to make a script that will assist my apps to remember their last used size and position. Is there a way to retrieve this info when a window is closed, and use it in a bash script?

Thanks!

Regards!

---

### Post by OutOfReach on 2008-12-21
I'm afriad that these kind of things usually have to be built into the program itself. Unless...You can find a way with the window manager to set these properties, or maybe the X server (which will require more than a script).

---

### Post by mssever on 2008-12-22
People often use devilspie for custom window manipulations. I've never used it, so I don't know if it can do what you want. But it's worth a look.

---

### Post by tijuana on 2008-12-22
Thanks!

I'll take a look at that devilspie

Regards!

---

### Post by Cracauer on 2008-12-22
I use this to capture the positions of my xterms, so that I when I restart X11 I'll have xterms in the same position:

```

#! /bin/sh

ids=`xlsclients -l | perl -p -e 's/\n//' | perl -p -e 's/Window /\n/g' \
        | grep xterm | egrep -v 'worlddates|monitoring|ethload' \
        | awk -F: '{print $1}'`

for id in $ids ; do
        echo xterm `xwininfo -id $id | grep geometry` '&'
done

```

The key here is to know your Windowid and then ask the X11 server for the position. Obviously if you are a C program you don't have to go through the command xwininfo, which has very messy output.

---

### Post by tijuana on 2008-12-23
Thanks! it's a bit late now so I can't make heads nor tails from the script xD, but I'll take a look at it tomorrow

Regards!

---

