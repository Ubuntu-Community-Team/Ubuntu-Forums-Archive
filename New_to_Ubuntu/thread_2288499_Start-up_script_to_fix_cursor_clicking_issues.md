---
title: "Start-up script to fix cursor clicking issues"
date: 2015-07-27
forum: New to Ubuntu
---

### Post by Deja_Wh0 on 2015-07-27
Currently when I boot up Ubuntu my cursor will click on the side bar but is unresponsive within applications.
I found the solution however I would like the command to run on start-up so I don't have to fix the bug each time I reboot.
How do I turn this into a start-up script?
```
#!/bin/bash
compiz --replace &
unity --reset
```
I don't have root access to create files within the /etc/init.d folder as several other post instruct you to place your script.
Any and all help will be much appreciated.

---

### Post by veddox on 2015-07-28
Save your code in a shell script (e.g. at $HOME/.cursorfix.sh). Set the permissions to disallow write, but allow read and execute (for security):
```
chmod 555 $HOME/.cursorfix.sh
```
Open your dash and search for "startup applications". Start the first application that appears. Click "Add". Enter a name ("Fix cursor bug" or some such) and the following command:
```
bash $HOME/.cursorfix.sh
```
Click "Add" and close the application. Next time you log in, your script should run automatically.

---

