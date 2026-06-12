---
title: "creating keyboard shortcut"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-12
how can i create a keyboard shortcut like ctrl+alt+del for the "system monitor" application?

---

### Post by Zalbor on 2008-08-12
Are you using compiz (the desktop effects) or not? It's different depending on if you are...

If you are using compiz, install the package called compizconfig-settings-manager (using synaptic for example), and the manager has options to execute commands with key combinations in the "General" options.

If you're not using compiz, you need to use the configuration editor. The easiest way to find it is to open a terminal or press alt+F2 and type "gconf-editor". Then go to apps>metacity>keybindings_commands, enter the command you want in a box there (gnome-system-monitor for example), and then go to global_keybindings and enter the key combination in the run_command box with the same number. Like <Ctrl><Alt>Delete.

---

