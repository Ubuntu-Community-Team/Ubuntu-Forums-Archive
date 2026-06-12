---
title: "[SOLVED] Python - permanently altering sys.path"
date: 2008-07-30
forum: Programming Talk
---

### Post by Erdaron on 2008-07-30
I have my own Python library that I use in my scripts, and I would like to be able to easily invoke using import statement.

In Python Docs I found a section on modifying Python search path (4.1 in Installing Python Modules), which said I can load module sys, then run sys.path.append('path_to_new_library'). I did that and it worked - I could invoke the library by using 'import sda' (sda is the name of the library).

However, after I restarted the library, sys.path went back to its original state, and running 'import sda' again yielded an error message, "No module sda"

It seems like I'm missing something simple and I just keep overlooking it. How can I make this addition permanent?

---

### Post by days_of_ruin on 2008-07-30
Where are you changing sys.path? In the file importing it?

---

### Post by skeeterbug on 2008-07-30
> **Erdaron said:**
> I have my own Python library that I use in my scripts, and I would like to be able to easily invoke using import statement.

In Python Docs I found a section on modifying Python search path (4.1 in Installing Python Modules), which said I can load module sys, then run sys.path.append('path_to_new_library'). I did that and it worked - I could invoke the library by using 'import sda' (sda is the name of the library).

However, after I restarted the library, sys.path went back to its original state, and running 'import sda' again yielded an error message, "No module sda"

It seems like I'm missing something simple and I just keep overlooking it. How can I make this addition permanent?

On my shared host I edited .bash_profile in my home directory and added this:

```

export PYTHONPATH=$PYTHONPATH:$HOME/django_src:$HOME/django_projects
```

Pretty sure that is what you are looking for.

---

### Post by Erdaron on 2008-07-30
> **days_of_ruin said:**
> Where are you changing sys.path? In the file importing it?

I launch python from terminal.

Then execute:
[PHP]import sys
sys.path.append('path_to_library')[/PHP]

[quote=skeeterbug]On my shared host I edited .bash_profile in my home directory and added this...[/quote]

Where's .bash_profile supposed to be located? I looked in /home and /home/borisg but it was not there (I've turned on "view hidden files"). The only copy I could find was in /usr/share/doc/adduser/examples/adduser.local.conf.examples/skel.

It just seems like python should have a configuration file somewhere that I could edit...

---

### Post by unutbu on 2008-07-30
You can either put

```
#!/usr/bin/env python
import sys
sys.path.append('path_to_library') 
import sda
```


at the begining of your script(s), or you can define the environment variable PYTHONPATH.
Try looking for ~/.profile if you don't have ~/.bash_profile.

If you have neither, then copy /etc/profile to ~/.profile and then put something like this in it at the end:

```
PYTHONPATH=path_to_library
export PYTHONPATH
```

---

### Post by days_of_ruin on 2008-07-30
/usr/local/lib/python2.5/site-packages

Put a path file (.pth) in that directory.
path files are just simple files with one library path per line.

---

### Post by Erdaron on 2008-07-30
> **days_of_ruin said:**
> /usr/local/lib/python2.5/site-packages

Put a path file (.pth) in that directory.
path files are just simple files with one library path per line.

This has worked on my Windows installation (in Python25/Lib/site-packages), and I will try it on Linux when I get home. Thanks!

@unutbu: I figured out your first suggested method, but I was trying to avoid having to do every time I write one of the scripts relying on SDA.

Your second method, I will also try when I get home.

---

### Post by WW on 2008-07-30
As suggested above, put your file in /usr/local/lib/python2.5/site-packages.  There is no need to create a .pth file; Ubuntu python looks here automatically.

---

### Post by Erdaron on 2008-07-31
Creating the .pth file worked on Ubuntu. All is well!

> **WW said:**
> As suggested above, put your file in /usr/local/lib/python2.5/site-packages.  There is no need to create a .pth file; Ubuntu python looks here automatically.

I would like to be able to access the library from Windows as well, and it's better to have just one copy of it. So it actually resides on an NTFS partition that's shared by XP and Ubuntu.

---

### Post by cagri on 2011-08-31
Go to ~/.bashrc
to the end of the file , insert " export PYTHONPATH=$PYTHONPATH:*your path*"
then restart the operating system.
Thats all

---

