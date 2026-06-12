---
title: "[SOLVED] main menu launcher icon change how to?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by golgo13 on 2008-05-23
I want to change my main menu launcher icon from the ubuntu one to the gnome foot which I downloaded into the shared folder into an icons folder I created
When I searched the forum there were some suggestions none of which worked
What is the easiest way of doing this?

---

### Post by sayakb on 2008-05-23
Change the icons at /usr/share/icons/themename/24x24/places/start_here.png
Do change the icons of other sizes also..

---

### Post by Bodsda on 2008-05-23
WOOT!! one more thanks to add to your book LinuxIsInnovation -- ive looked at loads of threads on here to no avail!! cheers m8

---

### Post by sayakb on 2008-05-23
No problemmo :)

---

### Post by golgo13 on 2008-05-23
this /usr/share/icons thing is really confusing me as originally when I went to the share folder it was empty?!

---

### Post by golgo13 on 2008-05-23
:redface:
sorry was looking in the wrong place...

---

### Post by golgo13 on 2008-05-23
ok so I followed the instructions and changed the start-here.png and nothing happened.....!?

---

### Post by Tuxoid on 2008-05-23
> **golgo13 said:**
> ok so I followed the instructions and changed the start-here.png and nothing happened.....!?

Go to System>Preferences>Appearance and click 'customize' and click the icons tab. If you are unsure about the name of the icon theme that is applied, this will tell you. To change the icons, you will need to run the file browser with administrative privileges. Right now the easiest way to do so is to, create a Lancher (right click your background, Create Launcher), and under the 'Command', type 'gksudo nautilus', and name it whatever you want.

double-click the launcher, enter your password, and go to the folder the currently applied theme is in (a folder somewhere in '/usr/share/icons')

---

