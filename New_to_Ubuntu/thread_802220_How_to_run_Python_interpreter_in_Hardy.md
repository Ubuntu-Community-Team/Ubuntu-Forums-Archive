---
title: "How to run Python interpreter in Hardy?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by QuizasQuizas on 2008-05-21
Hello!
I'm new to Ubuntu and having recently installed the 8.04 release, I am trying to find the executable file for Python. I have a book in front of me that says it should be somewhere in /usr/local/bin and that the libraries should be in usr/local/lib/python2.x, but I'm not seeing it (the command line recognizes Python as being installed, however).

Thank you for your time, and any input is much appreciated (in the meantime, I'm going to continue the hunt for an executable..)

---

### Post by neurostu on 2008-05-21
do you have the python script that you are trying to run?
If you do try:
```

python nameOfScript.py

```

or you can add ```
#!/usr/bin/python
``` as the first line of the file 
then make the script executable with:
```

chmod +x nameofScript.py

```
then to run it:
```

./nameOfScript.py

```

---

### Post by OffAxis on 2008-05-21
you can use the **find **command to find all instances of the word python.
```

cd /
sudo find -name python
```

here's mine (in xubuntu)

```
./etc/python
./etc/apparmor.d/abstractions/python
./usr/bin/python
./usr/share/python
./usr/share/doc/python
./usr/lib/xulrunner-1.9b5/python

```

---

### Post by Cypher on 2008-05-21
"which <executable>" will tell you where in your path an executable is. So Python is sitting in /usr/bin.

All of it's libraries are located in /usr/lib/python<ver> where <ver> is 2.3, 2.4, or 2.5

---

### Post by gug@fnal.gov on 2008-05-21
Hi,
   I put the following line first in all my python scripts:

#!/usr/bin/env python

Thus as long as python is in my PATH (i.e. typing "python" brings up the interpreter) my code is setup to work on the system. So if python is in /usr/bin or /usr/local/bin, or any other place in my default PATH, I do not have to change the code to get it to work. As another poster said, you need to "chmod u+x" to be allowed to execute the script directly.

---

### Post by QuizasQuizas on 2008-05-21
Thank you!

---

### Post by NetSkay on 2008-08-25
hey guys... i have the interpreter installed and PyDev along with eclipse but when i go to add the interpreter in pydev/eclipse 
i click new folder on System: PYTHONPATH and nothing happenes, the menu isnt coming up
so i tried where it says python interpreters (eg. python.exe) i click new and i navigate to /usr/lib/gimp/2.0/interpreters/pygimp.interp
and i get an error access denied

so what should i do, any manual way of adding.doing this thing

thank you

---

### Post by neurostu on 2008-08-26
> **NetSkay said:**
> hey guys... i have the interpreter installed and PyDev along with eclipse but when i go to add the interpreter in pydev/eclipse 
i click new folder on System: PYTHONPATH and nothing happenes, the menu isnt coming up
so i tried where it says python interpreters (eg. python.exe) i click new and i navigate to /usr/lib/gimp/2.0/interpreters/pygimp.interp
and i get an error access denied

so what should i do, any manual way of adding.doing this thing

thank you

You should start your own thread...

Seriously you will get better visibility (and more answers) if you create a thread that has a good descriptive title rather then tagging your question onto the end of and old thread.

Plus its generally considered bad form to resurrect a dead thread with a new question... (Just in case you didn't know)

---

