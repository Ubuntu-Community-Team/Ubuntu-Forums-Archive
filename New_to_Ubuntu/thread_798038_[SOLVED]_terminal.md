---
title: "[SOLVED] terminal????"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Tux.Ice on 2008-05-17
ok i need to open terminal and type in raspberry and it runs a script located at ~/.raspberry.sh

how do i do this?

---

### Post by Xerp on 2008-05-17
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by aysiu on 2008-05-17
Open [a terminal](http://www.psychocats.net/ubuntu/terminal) and then paste in these commands: ```
chmod +x .raspberry.sh
./.raspberry.sh
``` If you have any error messages, post them back here.

---

### Post by Tux.Ice on 2008-05-17
yes. but that dosent help if i need to create my own command/program.

isnt there a file i put in some folder like /bin/bash and call the file reaspberry.sh and have the contents of the file say nautilus /home/adam/raspberry.sh? wont that work?

---

### Post by Tux.Ice on 2008-05-17
aysiu

adam@adam-laptop:~$ chmod +x .raspberry.sh
chmod: cannot access `.raspberry.sh': No such file or directory
adam@adam-laptop:~$ chmod +x .raspberry.sh
adam@adam-laptop:~$ ./.raspberry.sh
adam@adam-laptop:~$ raspberry
bash: raspberry: command not found
adam@adam-laptop:~$ 
adam@adam-laptop:~$

---

### Post by aysiu on 2008-05-17
Okay. You said it was located at ~/.raspberry.sh, but it clearly isn't.

~/.raspberry.sh means /home/adam/.raspberry.sh, but the output you posted indicated there's no such file as *.raspberry.sh* in your home directory.

Where is the file?

---

### Post by Tux.Ice on 2008-05-17
you can see that it wasnt @ the first command but it was in the second. problem is last line.:popcorn:

---

### Post by aysiu on 2008-05-17
Why don't we back up a few steps? What exactly are you trying to achieve with this raspberry script? This is a script you created yourself?

Is the real question, "How do I run this script someone else created this one time?" or "If I wanted to create a script, how would I make it run easily?"

---

### Post by Tux.Ice on 2008-05-17
i want to open a terminal type 'raspberry' and have it run the script.

---

### Post by scxtt on 2008-05-17
put this entry in .bashrc

**alias raspberry='~/.raspberry.sh'**

and make sure *#!/bin/bash* is the 1st line of your script.

---

