---
title: "Autorun python script IN TERMINAL after login?"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by David2249 on 2012-11-29
I created a python script and I've made it executable so I can click on it and it asks. Is there a way to make it default to automatically run after double clicking on it? I've been also trying to make it run after logging in, but the autostart feature doesn't seem work. Do I need to put it in a bash script or something else?

---

### Post by David2249 on 2012-11-29
I think I'm getting there...

I installed this:

sudo apt-get install gnome-panel

Then did this:

gnome-desktop-item-edit ~/Desktop/ --create-new

Now I have a desktop icon that starts it without prompting me to edit. But I tried putting it in the startup applications and it opens in gedit after logging in.

---

### Post by sandyd on 2012-11-29
a)Make sure it has executable permissions
b) Add
```

#!/usr/bin/python
```
to the very top of the script

Then, launch the script using gnome-terminal
```

 gnome-terminal -x /path/to/script

```

---

### Post by David2249 on 2012-11-30
> **sandyd said:**
> a)Make sure it has executable permissions
b) Add
```

#!/usr/bin/python
```
to the very top of the script

Then, launch the script using gnome-terminal
```

 gnome-terminal -x /path/to/script

```

That worked great!

---

