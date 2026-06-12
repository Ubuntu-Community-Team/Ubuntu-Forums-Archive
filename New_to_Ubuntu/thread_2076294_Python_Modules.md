---
title: "Python Modules"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by peterfarrell66 on 2012-10-25
Hello to the Community!

I'm new to Ubuntu, and fairly new to Python as well. My Home folder shows I've dowloaded scipy, matplotlib and pylab (or they're on here somewhere) but when I try to import them in Python it gives me an error. "No module named ___" I don't know if this is a really easy issue, but I think it's just a matter of somebody showing me where these modules are and how to access them.

Any Python users know how to solve this newbie question?

Thanks in advance!

Peter Farrell

---

### Post by drmrgd on 2012-10-25
It's been a little while since I've worked with Python.  If I recall correctly, though, modules need to be either in your working directory (i.e. where you're launching your scripts from), or in your pythonpath environmental variable path.  I think you find this by looking at sys.path:

```
import sys
print sys.path
```

Just had a quick look and found this, which might help:

[http://docs.python.org/tutorial/modules.html](http://docs.python.org/tutorial/modules.html)

---

### Post by peterfarrell66 on 2012-10-26
Thank you very much for the information!

Peter

---

### Post by getThem_robots on 2012-10-26
As a followup, note that you could do the following:

```

import sys
sys.path.append("RELATIVE_OR_ABS_PATH_TO_MODULE")

```Or, if you want a more general solution, add the path to PYTHONPATH in your bashrc.

Open bashrc to edit:
```

vim ~/.bashrc

```Add the following to the end of bashrc:
```

export PYTHONPATH=$PYTHONPATH:PATH_TO_MODULE

```Where PATH_TO_MODULE is the absolute path to the module.
[Edit: or the path to the directory containing the module]

Setting the PYTHONPATH is especially useful if you have a bunch of modules sitting in a directory and you want Python to recognize them. 

Hope that helps.
-
Mahdi

---

### Post by peterfarrell66 on 2012-10-27
Thank you, Get Them Robots.

I'm such a coding newbie that I can't figure out the "path to module." I've been trying to copy the modules' folders into the correct directory but it says it's been denied. When trying to extract numpy into Python 3.2 folder I'm told I don't have permission. I'm the administrator! In name only? 

Once all my modules are in place (as they are in my windows setup), I can do a lot of wonderful mathematical things with Python, but getting my ducks in a row in Ubuntu has proven a challenge. Maybe I need to be told exactly what to type in (by a user saying "Type dir something something and post what it tells you" and "type cd something" and so on.

I'm willing to try a little hand-holding. 

Thanks for the help so far!

Peter Farrell

---

### Post by drmrgd on 2012-10-27
The path to module could be anything you desire.  If you want to put them into one of the Python directories, by default they only have write access by root.  So, even though you're the administrator, you'd need to issue 'sudo' in front of the copy command, which gives you root level permissions to do the task.  Being an administrator only means that you'll be able to issue sudo as opposed to regular users who can not.  

I would agree that making a local repository of those extra modules might be nice.  In that case, follow the advice about adding the line to your ~/.bashrc file, and point it to some directory where you'll keep all those extra modules.  For example (assuming you have a directory in $HOME that's called myPythonModules) add the line:

```
export PYTHONPATH=$PYTHONPATH:/home/<username>/myPythonModules/ #substitute '<username>' with your username
```

Then don't forget to reload your shell by either logging out and back in, or just issuing:

```
source ~/.bashrc
```

---

### Post by peterfarrell66 on 2012-10-28
Thank you for the great suggestions. 

I created a directory in Home called "My Python Modules" and the first line didn't get me any error messages.

The sys.path.append line worked with no error messages. 

It didn't like the PYTHONPATH line, though. "Invalid syntax" 

I downloaded numpy again and I'm trying to extract it to the Python 3.2 folder and it says I don't have permission to extract to that archive and apparently I don't have permission to create a directory, either.

I'm the administrator on the Windows side of the machine. Did I not get administrator status on the Ubuntu side?

Thank you in advance!

Peter

---

### Post by drmrgd on 2012-10-28
> **peterfarrell66 said:**
> Thank you for the great suggestions. 

I created a directory in Home called "My Python Modules" and the first line didn't get me any error messages.

The sys.path.append line worked with no error messages. 

It didn't like the PYTHONPATH line, though. "Invalid syntax" 

I downloaded numpy again and I'm trying to extract it to the Python 3.2 folder and it says I don't have permission to extract to that archive and apparently I don't have permission to create a directory, either.

I'm the administrator on the Windows side of the machine. Did I not get administrator status on the Ubuntu side?

Thank you in advance!

Peter

You have to be careful with spaces in filenames and directories in Linux.  If you call the directory 'My Python Modules', the spaces in the directory names could cause problems if you've not either quoted the name:

```
export PYTHONPATH=$PYTHONPATH:/home/<username>/"My Python Modules"/
```

or escaped them:

```
export PYTHONPATH=$PYTHONPATH:/home/<username>/My\ Python\ Modules/
```

Please paste the actual call that you entered into your .bashrc (or where ever you put it so that we can make sure you typed it) correctly.

With regard to permissions, as I said, the Python directories are owned by root.  So, although you're Administrator in the system, you still need elevated privileges (root level) to do these kinds of tasks.  Being an admin only means that you're able to issue 'sudo' in front of a command, which grants root level access for that command only.  Perhaps this Community documentation will help explain root and sudo:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by peterfarrell66 on 2012-10-28
Thanks!

The python error was pointing to the PYTHONPATH, not the directory name. I don't know if it's because I haven't declared a "PYTHONPATH" before or what.

I'll definitely check out the link to the RootSudo issue.

Peter

---

### Post by peterfarrell66 on 2012-10-29
Hello, again,

I finally got numpy copied to the Python3.2 directory. Come to find I was working in the terminal in Python, and once I exited the commands worked. I used 'sudo mkdir' and so on.

But now Python still won't import the numpy module, even though it imports other modules in the same directory. I guess this is a Python issue now so I thank everybody in the Ubuntu forum for their patience with my newbie issue! 

I'm sure I'll be back.

Peter Farrell

---

### Post by drmrgd on 2012-10-29
If you open Python3.2 and run the following, what is the output:

```
import sys
print sys.path
```

In that, you should see the new modules directories that you've created.

---

### Post by drmrgd on 2012-10-29
As an update to the above, I noticed that the syntax has changed in Python3.2 (haven't used it yet, but just installed to check it out).  So, the command should be:

```
import sys
print(sys.path)
```

Also, see this for more info on Python3.2 and installing numpy:

[http://ubuntuforums.org/showthread.php?t=1818188](http://ubuntuforums.org/showthread.php?t=1818188)

and this for more info about python modules:

[http://ubuntuforums.org/showthread.php?t=963837](http://ubuntuforums.org/showthread.php?t=963837)

---

