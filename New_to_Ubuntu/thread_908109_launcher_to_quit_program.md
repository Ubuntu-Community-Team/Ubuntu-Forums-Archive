---
title: "launcher to quit program"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by jason6g on 2008-09-02
do not want to force quit, just nicely exit a program such as vlc or firefox

my goal is to bind it to a key shortcut, so that even id it is minimized the program will safely exit

---

### Post by stunningman on 2008-09-02
unlike windows you can force quit program without any problem in ubuntu.

---

### Post by fballem on 2008-09-02
I have had occasion to use Force Quit, and it does not appear to have any ill effects. It works a little like Task Manager in Windows.

If you're running GNOME, then you may want to add Force Quit to either the Top or Bottom Panel. To do this, right-click on one of the panels. this will provide a menu, from which you will select 'Add to Panel'. This will give you a list of Applications. Select Force Quit, then select the Add button. You can then close the list.

Hope this helps,

---

### Post by jemate18 on 2008-09-02
> **jason6g said:**
> do not want to force quit, just nicely exit a program such as vlc or firefox

my goal is to bind it to a key shortcut, so that even id it is minimized the program will safely exit

Force quit is a very good in "killing the application" it doesn't give any "PROBLEM", it also "kills" the application instantly. Unlike the "End Task" in M$ which always gives a problem and sometimes a computer hang....

---

### Post by zerhacke on 2008-09-02
Actually, jemate18, force quit doesn't always kill the program.  Many times it will just kill the gui leaving the program running as an orphan.\

Look to your command line.  ps -A will show all running programs and their PID.  You simply ps -A | grep YOURPROGRAMNAME and then kill - YOURPID.

---

