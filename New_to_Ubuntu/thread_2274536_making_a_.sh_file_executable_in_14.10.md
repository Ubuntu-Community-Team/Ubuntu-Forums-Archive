---
title: "making a .sh file executable in 14.10"
date: 2015-04-20
forum: New to Ubuntu
---

### Post by James_McGarry on 2015-04-20
I am trying to install a game that is an .sh file no matter what I do either in the terminal or by right clicking works please help

---

### Post by deadflowr on 2015-04-20
Post the commands you've tried...

So as to prevent us from posting uselessly.

---

### Post by James_McGarry on 2015-04-20
sorry I have tried chmod +x filename sh tried this a few different ways did not work also tried allowing it permission under properties did not work either

---

### Post by deadflowr on 2015-04-20
Well the file should be executable now.
what does
```
ls -l filename
```
say?
Also,
How are you trying to run it?
Through the terminal, or by double-clicking the file?

---

### Post by brian62 on 2015-04-20
Do sh nameOfFile.sh.

---

### Post by James_McGarry on 2015-04-20
I am trying to run it by double clicking and the terminal double clicking brings me to the editor and the terminal does nothing tried the sh filename.sh and that does not work either

---

### Post by deadflowr on 2015-04-20
Open up Files.
go to the menu, which should be in the top panel of your screen.
(The menus are hidden usually, just mouse over where the name of the program is and the menu should show.)
Now, go to Edit >> Preferences.
Go to the section  Behavior and change the selection for Executable Text Files.
Choose either run or ask.
The default is view, which causes problems.
Then close the window and try to run the file.

---

### Post by James_McGarry on 2015-04-20
thank you very much deadflowr your last tip worked like a charm game is installed and working

---

