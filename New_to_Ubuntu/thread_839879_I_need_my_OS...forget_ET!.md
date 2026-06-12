---
title: "I need my OS...forget ET!"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by rlntel on 2008-06-24
Ok...here's what happened...

1) I got bored and wanted to try to Enemy Territory for Linux release, which I had not tried on Hardy. I did the sudo apt-get to download et; then ran it according to the instructions;

2) ET ran but without sound. So, I researched the troubleshooting tips for getting sound running and it never got there.

3) I rebooted and the Ubuntu bar moved from the left almost to the right during the bootdown and then hung. In desperation, I finally did a 'hard' reset shutting down the power.

4) Ubuntu restarted, this time, however, the panels appeared, but no icons on the desktop. I restarted again. This time, the desktop icons appeared, but the panels did not: no menus, no shortcuts, no status icons, nothing...

5) I dropped to terminal via Ctrl-Alt-F1 and tried all the gnome-panel/gnome-terminal suggestions in the Forums, but nothing seems to help.

Let me know what info you need.

Thanks in advance.

Rob

---

### Post by iaculallad on 2008-06-24
If you could drop in your terminal (Or if you can't, press Alt+F2 and input "gnome-terminal" (w/o quote)) try doing this:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

---

### Post by rlntel on 2008-06-24
Well...I did as you suggested and the panel bar (on which the menu items and shortcuts normally exist) on both the top and bottom are now gone.

We're getting somewhere...what next?

By the way, Alt-F2 doesn't do anything for me. I'm having to resort to Ctrl-Alt-F1 to get to terminal and then Ctrl-Alt-F7 to get back out.

Eagerly awaiting your reply.

Rob

---

### Post by Yuki_Nagato on 2008-06-24
I imagine we are going to reinstall the gnome-panel packages through Synaptics next?

---

### Post by iaculallad on 2008-06-24
Both top and bottom panel are now gone :confused: Do your Ctrl+Alt+F1 again and issue the commands below to unset your panels.

```
gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &
```

Do the Ctrl+Alt+F7, logout then log back in.

---

### Post by rlntel on 2008-06-24
right off the bat, I got 'cannot open display: Run 'gnome-session-remove --help' to see a full list of...,' you know the rest.

---

### Post by rlntel on 2008-06-24
how do i run synaptic from the command line?

---

### Post by omi291 on 2008-06-24
> **letterrep.com said:**
> how do i run synaptic from the command line?

```
sudo synaptic
```

---

### Post by rlntel on 2008-06-24
Running 'sudo synaptic' rendered: Gtk-WARNING **: cannot open display:'

---

### Post by DGortze380 on 2008-06-24
if all else fails -

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

---

### Post by iaculallad on 2008-06-24
> **letterrep.com said:**
> Running 'sudo synaptic' rendered: Gtk-WARNING **: cannot open display:'

You cannot run gnome-session applications without the X Windows running. In your Ctrl+Alt+F1 terminal, try typing **init 5** and see what it displays.

---

### Post by rlntel on 2008-06-24
SOLVED

You're a genius!

Thanks

---

### Post by nowshining on 2008-06-25
while ur there - i suggest of having shut down the power without the reg. shutdown seq.

in terminal

cd /

sudo /bin/bash

touch /forcefsck

reboot.

---

