---
title: "[SOLVED] An equivalent for windows start up folder"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by Prabakar on 2008-10-11
I want pidgin to start automatically when I login. In windows, I will paste a shortcut in start up folder. how will I do it in ubuntu 8.04? Please help

---

### Post by JasenGroves on 2008-10-11
You need to click System > Sessions and then in the dialog box you need to click "+ ADD" and fill out the information. The command is "pidgin" and the rest you can fill out as you wish

---

### Post by expatCM on 2008-10-11
system / preferences / sessions - startup tab

---

### Post by KOld Iron on 2008-10-11
Two possibilities:

1. Choose "System > Preferences > Session" from the panel menu
2. Choose the "Startup Programs" tab
3. Choose "Add": Name = "Pidgin";  Command = "pidgin"; Comment = optional

or

1. Start pidgin (and every other app that you want to run on startup).
2. Choose "System > Preferences > Session" from the panel menu.
3. Choose the "Session Options" tab
4. Choose "Remember currently running applications"

---

### Post by Prabakar on 2008-10-12
Thanks to all of you. It works like a charm:)

---

