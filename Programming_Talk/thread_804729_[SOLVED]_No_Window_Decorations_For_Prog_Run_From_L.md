---
title: "[SOLVED] No Window Decorations For Prog Run From Login Script"
date: 2008-05-23
forum: Programming Talk
---

### Post by mike_g on 2008-05-23
I added a couple of lines of script that runs a java app on login from: home/username/.profile
It runs the straight away on startup, which is what i want, but the windows in it have no decorations. So, whenever you open one you cant close it, which sux. My main window is set to having no decorations (i dont know if that makes any difference), but none of its child windows should have decorations. Do I somehow have to load the desktop first before starting the prog? Any suggestions on how to fix this would be appreciated. Cheers.

edit: I'm using GNOME for the WM

---

### Post by NormR2 on 2008-05-23
Are you talking about the Title bar?
Is your main GUI class a Frame or a Window?
Windows don't have title bars.

---

### Post by mike_g on 2008-05-23
The windows don't have any decorations at all. They have no titlebar, buttons, or frames and cant be manipulated. However I have started to like this since the WM is not loaded and non-admin users can't exit the prog then they can't do anything outside of the program. The child windows look kind of ugly w/o borders, but I added keybindings to close them now. So yeah, my prblems kind of solved now.

---

### Post by NormR2 on 2008-05-23
Just curious, what java class are you using to display the window?

---

### Post by mike_g on 2008-05-23
Oh, I'm using Swing and all my window classes in the prog extend JFrame if thats what you mean.

---

