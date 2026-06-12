---
title: "IDLE file save"
date: 2009-09-20
forum: Programming Talk
---

### Post by sbooder on 2009-09-20
Hi All,
        just starting out in python, and I have no programming experience at all.

I am trying to follow the tutorial A Byte of Python by Swaroop CH and am stuck at the very first turn.

I have entered the commands below into IDLE, but where do I save the file to; so it will run in the terminal?

>>> #!/usr/bin/python
>>> # Filename : helloworld.py
>>> print "Hello World"

I realise I am being a bit thick here but I can not get it to work.  I always feel with tutorials that they suddenly assume that you have gained special insight. I need not explain some of the steps.

---

### Post by januzi on 2009-09-20
So, You have got file "name.py" (You can save it into Your home dir). Go to the console and make sure You are inside the dir with name.py. Use command: chmod +x name.py. When You run "ls -l" (lowercase L) then You`ll see that this file is green (or there are x in rights column). It means that You can execute it.
> 
./name.py
You could also try to run it with
> 
python name.py
 (maybe this will work too)

---

### Post by elbarto_87 on 2009-09-20
File > New Window

And past your code there. 

Save the file and follow januzi's instructions if you want to run the file from the terminal.

Regards Elbarto

---

### Post by sbooder on 2009-09-22
Thank you both.  It turns out that there is one important step missing from the tutorial, and that is telling the complete novice like me that once IDLE is open, before you type the code you have to open a new window.  So I was typing directly into the interpreter.

Anyway, I have sorted it now.

Simon.

---

