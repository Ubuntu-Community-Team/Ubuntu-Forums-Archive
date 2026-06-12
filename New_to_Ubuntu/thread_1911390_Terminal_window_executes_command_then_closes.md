---
title: "Terminal window executes command then closes"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by sgrov on 2012-01-18
I put in a command for gnome-terminal to run upon opening to disable my touchpad on my laptop. I think it was also set to close the terminal after executing my command. When I try to open the terminal, it comes up for a split second, then closes. How can I change it back so I can use the command line? I've tried installing and reinstalling.

---

### Post by sgrov on 2012-01-19
I tried to replace the modified %gconf.xml file with the original config file in the ~/.gconf/apps/gnome-terminal Default folder. Everytime I ran gnome-terminal, the file reverted back to the modified file, and the terminal would pop open and then close. I then found the configuration editor (gconf-editor) and was able to modify the settings of gnome-terminal. It now works fine again. I'm not sure why there is even a setting to close the terminal after a custom command is automatically executed.

---

### Post by mcduck on 2012-01-19
> **sgrov said:**
> I tried to replace the modified %gconf.xml file with the original config file in the ~/.gconf/apps/gnome-terminal Default folder. Everytime I ran gnome-terminal, the file reverted back to the modified file, and the terminal would pop open and then close. I then found the configuration editor (gconf-editor) and was able to modify the settings of gnome-terminal. It now works fine again. I'm not sure why there is even a setting to close the terminal after a custom command is automatically executed.

The setting is there because you can have several different profiles for the terminal, so you can create launchers that run a specific application with a certain profile, and doesn't leave the terminal open when you close that application.

Enabling the option to close the terminal would of course be a bad idea when using your default profile.

---

