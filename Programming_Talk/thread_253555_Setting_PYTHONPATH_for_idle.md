---
title: "Setting PYTHONPATH for idle?"
date: 2006-09-08
forum: Programming Talk
---

### Post by maubp on 2006-09-08
I've got some python modules installed in my home directory, so I added a couple of lines to my .bashrc as follows:

# Tell Python about my locally installed Python Modules:
export PYTHONPATH="/home/maubp/lib/python2.4/site-packages"

This works great when running python from a terminal, the imports work and you can check it with:

>>> import sys
>>> print sys.path

However, it doesn't work if I run IDLE.  Any suggestions?

Do I need to set the PYTHONPATH environment somewhere in gnome (where?), or configure IDLE in some way (how?)

Thanks

---

### Post by toojays on 2006-09-08
I've had a similar problem with Emacs in the past. Try putting a snippet like this in your python code:```
import sys
sys.path.insert(0, '/home/maubp/lib/python2.4/site-packages')
```

---

### Post by dwblas on 2006-09-08
I would put it in ~/.bashrc.  You might have to create that file.  You would add:
> export PYTHONPATH="${PYTHONPATH}:/usr/lib/python/site-python/:/home/site-python/" 
or whatever you want.  This will update it system-wide whenever you log in.  Also, note the quotes.

---

### Post by toojays on 2006-09-08
dwblas, maubp already told us that he does put it in his bashrc!

Some programs, especially IDEs, run their child processes in a restricted or "clean" environment. That's why this doesn't work.

---

### Post by maubp on 2006-09-10
**dwblas** - you need to read things more slowly ;) As **toojays** pointed out, I've already setup my PYTHONPATH in the .bashrc file and it doesn't work for IDLE.

Thanks for the suggestion **toojays**, I think that would work but its a pain to add that work around to each and every scipt I use. ](*,)

---

### Post by maubp on 2006-09-10
Here is my quick hack, which *should* work for all users.

sudo gedit /usr/bin/idle

Then make it look like this, I have used .... to show an indentation (four spaces):

> #! /usr/bin/python2.4

from idlelib.PyShell import main
if __name__ == '__main__':
....import os, pwd
....home_site_packages = os.path.join(pwd.getpwuid(os.getuid()).pw_dir, "lib/python2.4/site-packages")
....if os.path.isdir(home_site_packages) :
........import sys
........sys.path.insert(0, home_site_packages)
....main()

As a side effect, when using IDLE, the three modules sys, os and pwd will have already been imported.

---

### Post by grj23 on 2009-08-17
Does anyone know if this is still necessary for Ubuntu 9.04?  I'm using python 2.5, and have only switched over recently from windows.  Seems strange that PYTHONPATH doesn't apply to Idle?!

---

### Post by maubp on 2009-08-17
> **grj23 said:**
> Does anyone know if this is still necessary for Ubuntu 9.04?  I'm using python 2.5, and have only switched over recently from windows.  Seems strange that PYTHONPATH doesn't apply to Idle?!
I don't know if there is a better way, and use an updated version of my hack for IDLE on my Ubuntu 9.04 "Jaunty" machine.

---

### Post by grj23 on 2009-08-17
Thanks.  I'll give it a go.  Does anyone know what the default value of PYTHONPATH is?  I think I wiped it out when I was fiddling.  But I'm pretty sure it's empty at installation, right?

So to use a self-made module I have to both (1) update PYTHONPATH in case I run it from nautilus or whatever, and (2) do the fiddle maubp suggested in case I run it from IDLE?  

Is that right?

---

### Post by grj23 on 2009-08-17
Hi

So frustrations mount!  

Firstly, I changed my idle start up as suggested (more or less).  Mine is called idle-pthon2.5 in /usr/bin (because I have two versions of python running).  I have a simplified version as follows:
#! /usr/bin/python2.5

from idlelib.PyShell import main
if __name__ == '__main__':
    import os
    myPath="home/grj23/Documents/General/Fun Stuff/Python/MyProgs"
    if os.path.isdir(myPath):
        import sys
        sys.path.insert(0,myPath)
    main()

When I run this, idle starts as normal, but neither os nor sys is imported.  More crucially, the path is not changed.

Here's an example:
>>> sys.path
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    sys.path
NameError: name 'sys' is not defined
>>> import sys
>>> sys.path

I was then having a problem, where I'd type sys.path.insert(, and as I typed "(" a bunch of Tkinter errors would occur.  I did this several times, and so was just writing this and decided to do it again, but of course this time it worked.  So embarrassing.

Anyway, I can't see what I'm doing wrong, but maybe someone else can.  I also saw on another tread that IDLE maybe isn't the best python shell to use.  A shame because I enjoy using it (been mainly doing python in xp), but am open to suggestions.  What do people use?

---

### Post by creepa1982 on 2011-02-05
When you specify the path through the bashrc you have to make sure to load idle from the terminal!

This way it works for me on version python 3.12. 

Cheers!

---

### Post by rentzso on 2012-03-14
If you want to make it work without starting it from the terminal, try to write the path you want to add to the PYTHONPATH in a .pth file in your dist-packages directory.

For me it was /usr/local/lib/python2.7/dist-packages

More details at [http://greeennotebook.com/2010/06/how-to-change-pythonpath-in-windows-and-ubuntu/](http://greeennotebook.com/2010/06/how-to-change-pythonpath-in-windows-and-ubuntu/)

---

### Post by erik6d on 2012-05-01
I set PYTHONPATH in .profile instead of .bashrc -- it's then available from IDLE regardless of whether or not I start it from the terminal.

---

