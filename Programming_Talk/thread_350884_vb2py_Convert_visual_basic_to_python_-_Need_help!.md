---
title: "vb2py Convert visual basic to python - Need help!"
date: 2007-02-01
forum: Programming Talk
---

### Post by Garyu on 2007-02-01
I found a neat application... I think...
[http://vb2py.sourceforge.net/documentation.htm](http://vb2py.sourceforge.net/documentation.htm)
The object of this project is to make an application that converts visual basic code to python. Seems like a great idea. But... I can't install it... There is a demo available online, but it has some limitations to it, so I would really like to install the whole thing.

First of all there are some dependencies that need to be solved. Easy enough since they are in the repositories (universe):
```
sudo apt-get install python-simpleparse pythoncard
```

Then you download the sourcecode from the above link. The documentation says that it is sufficient to run
```
./setup.py install
```
But when I run this I get only errors...

First I get three lines of "Command not found". Then "WIN_DEFAULT_COMMAND - command not found" (which should really just be the "install" option, not a command). Then "APPLICATION_NAME - command not found". After these errors the cursor will change and nothing happens unless I click somewhere, the cursor changes again and I have to click somewhere, then a third time after which I have to wait a few seconds and the following errors appear:
```
from: can't read /var/mail/distutils.core
from: can't read /var/mail/distutils.command.install_data
./setup.py: line 20: if len(sys.argv) == 1 and sys.platform.startswith(win):
: kommando hittades inteDEFAULT_COMMAND)
: kommando hittades inte
./setup.py: line 25: 
This script is setup.py of the vb2py package.
: kommando hittades inte
: kommando hittades inte
./setup.py: line 27: syntax error near unexpected token `('
'/setup.py: line 27: `class smart_install_data(install_data):
```
I'm in swedish so "kommando hittades inte" = "command not found"...

Can someone please help to get this thing working? Anyone with python expertise?

---

### Post by DaveArb on 2007-02-01
> The documentation says that it is sufficient to run
Code:

./setup.py install



At [http://vb2py.sourceforge.net/docs/installation.html](http://vb2py.sourceforge.net/docs/installation.html) , the command given is:

```
> python setup.py install
```

I don't know anything about that program, but the errors you're getting seem pretty compatible with trying to get the shell to run Python code.

---

### Post by Garyu on 2007-02-01
> **DaveArb said:**
> I don't know anything about that program, but the errors you're getting seem pretty compatible with trying to get the shell to run Python code.

Duuh... wow, sometimes I really do deserve a "RTFM"... Thanks for that very informative response though. Now everything works fine. I never went into that line of thought since the script begins with "#!/usr/bin/python" and that seemed correct so I really thought I was getting the errors from the python interpreter. And also, since things were really happening... Guess I need a smarter computer who understands my lines of thought. :P

Or... Maybe I just need to learn some python. But I will learn python, so I shall try to refrain from really stupid questions in this area in the future. :D

---

### Post by DaveArb on 2007-02-01
> **Garyu said:**
> Guess I need a smarter computer who understands my lines of thought. :P

Don't we all! :D Glad it helped.

---

### Post by Garyu on 2007-02-01
*sigh*
OK, I spoke too soon... again...

```
dan-erik@BlueZen:/usr/lib/python2.4/site-packages/vb2pygui$ python ./vb2pyGUI.pyw
Traceback (most recent call last):
  File "./vb2pyGUI.pyw", line 6, in ?
    from PythonCardPrototype import model, dialog
ImportError: No module named PythonCardPrototype
```

Pythoncard is installed from repository. So there really should be no issues here... But still I can't run this application. ](*,) 

There are three python dirs in /usr/lib: python2.3 which is basically empty, python2.4 in which there is a lot of stuff among others the site-packages/vb2pygui directory. But there is also python2.5 directory. So I tried to copy the installation to the 2.5 directory but I got the same error there. However, the pythoncard is installed in /usr/share/pythoncard so a totally different directory. Still that shouldn't matter should it?

---

### Post by Garyu on 2007-02-03
I contacted the developer (Paul Paterson) and he said the errors are because of changes in newer versions of pythoncard. He is working on a fix though, so soon it might be functional. :)


EDIT:

Got my reply, a new version is out... and it works! :D
I'm writing a howto on how to install it. Otherwise, just check out the project homepage
[http://vb2py.sourceforge.net/](http://vb2py.sourceforge.net/)

---

