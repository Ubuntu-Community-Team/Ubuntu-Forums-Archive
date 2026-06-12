---
title: "Send keys and shell commands from Python?"
date: 2008-03-09
forum: Programming Talk
---

### Post by xelapond on 2008-03-09
Hello again, 

I have been perusing the Library reference and google, and have not found anything useful.

Is there a way to send keys from Python to the OS,  specifically the function keys?  Also, is there a way I can run shell(bash) commands from Python?

Thanks, 

Alex

---

### Post by mssever on 2008-03-09
My Python skills are quite rusty, but I think that you can run shell commands from either the os or sys module--I don't remember which.

Try either os.system or sys.system.

---

### Post by Acglaphotis on 2008-03-09
If you want to run the command it's (import os) os.system. If you want to know the output its os.popen. Hmm... for the function keys try xsend (its an application) and then try to call it from inside the script.

---

### Post by xelapond on 2008-03-09
Thanks, I checked out os.system and that does exactly what I want.  I looked at xsend though, and it appears to be a UNIX mailer or something.  Is there a way I could use echo, or something like that?

---

### Post by pmasiar on 2008-03-09
os.system was easy, anybody can guess that :-)

IMHO Python has solution also to your other problem: [Pexpect](http://www.noah.org/wiki/Pexpect#Description_of_Pexpect)  allows your script to spawn a child application and control it as if a human were typing commands.

Python rulez :-)

---

### Post by xelapond on 2008-03-09
I'm not sure if Pexspect does what I want to either, but that is cool.  Ill keep it in mind for other proejcts.  What I want to do is have python "hit" F11 to open Yakuake, or ALT+TAB to switch apps, among several other things.

---

### Post by Acglaphotis on 2008-03-09
oops... i ment xautomation (sudo aptitude install xautomation) and then to call any key its like:

[php]
xte "key F1"
[/php]

---

### Post by imdano on 2008-03-09
My understanding is there is no built-in way to do this in python, but you can do it by controlling some third-party app that simulates X keystroke-events (like [xmacro](http://xmacro.sourceforge.net/) or xautomation) through python.

---

### Post by pmasiar on 2008-03-09
There is pty: [http://docs.python.org/lib/module-pty.html](http://docs.python.org/lib/module-pty.html) - Linux only.

---

### Post by slavik on 2008-03-09
> **pmasiar said:**
> os.system was easy, anybody can guess that :-)

IMHO Python has solution also to your other problem: [Pexpect](http://www.noah.org/wiki/Pexpect#Description_of_Pexpect)  allows your script to spawn a child application and control it as if a human were typing commands.

Python rulez :-)
Tcl had expect a long time ago. :)

---

### Post by infernosoft on 2010-04-14
So, were you finally able to send keystrokes to other windows via python?

---

