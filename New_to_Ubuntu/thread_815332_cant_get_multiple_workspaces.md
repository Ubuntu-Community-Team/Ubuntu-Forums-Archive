---
title: "cant get multiple workspaces"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ludacrisman7 on 2008-06-01
i have enabled the cube effect, but i can only access two workspaces. i went to the prefreces to get more workspaces, and ive add four but still only lets me go to only two of the workspaces, and not the rest. its in a 2 by 2 setting right now, but i can only use the top two. what can i do?

---

### Post by ibuclaw on 2008-06-01
Press "**Alt+F2**" and type **gconf-editor** into the textbox and run the app.

In the new window, go into "**desktop>gnome>applications>window_manager**" in the registry and set the value of **number_of_workspaces** to **4**.

Changes should be instantaneous,

Regards
Iain

---

### Post by philinux on 2008-06-01
> **ludacrisman7 said:**
> i have enabled the cube effect, but i can only access two workspaces. i went to the prefreces to get more workspaces, and ive add four but still only lets me go to only two of the workspaces, and not the rest. its in a 2 by 2 setting right now, but i can only use the top two. what can i do?

You need columns 4 rows 1.

---

