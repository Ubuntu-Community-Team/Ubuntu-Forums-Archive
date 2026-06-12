---
title: "Python - module can not be used until I add .py extension."
date: 2009-09-28
forum: Programming Talk
---

### Post by credobyte on 2009-09-28
Any ideas ? If I rename ifnet to ifnet.py ( + extension ), everything works like a charm.

```
sysinfo: a python script text executable
ifnet: a python script text executable
```

```
-rwxr-xr-x 1 dainis dainis 404 2009-09-29 00:06 ifnet
-rwxr-xr-x 1 dainis dainis 629 2009-09-28 21:46 sysinfo
```

**sysinfo**
```

#!/usr/bin/env python
import ifnet
```

**ifnet**
```
#!/usr/bin/env python
```

[COLOR=Red]**Error**[/COLOR]
```
Traceback (most recent call last):
  File "./sysinfo", line 4, in <module>
    import ifnet
ImportError: No module named ifnet
```

---

### Post by DaithiF on 2009-09-28
python modules must be named with the .py suffix, when you say import foo, the import statement looks for a file name foo.py, thats just the way it is...

---

### Post by credobyte on 2009-09-28
> **DaithiF said:**
> python modules must be named with the .py suffix, when you say import foo, the import statement looks for a file name foo.py, thats just the way it is...

Sad .. Anyway, thnx for help :)

---

### Post by -grubby on 2009-09-28
How is this sad? It makes perfect sense.

---

### Post by credobyte on 2009-09-28
> **-grubby said:**
> How is this sad? It makes perfect sense.

No, it doesn't make sense if someone in another thread argued that Python and other scripting languages in Linux, doesn't relay on extensions.

---

### Post by -grubby on 2009-09-28
> **credobyte said:**
> No, it doesn't make sense if someone in another thread argued that Python and other scripting languages in Linux, doesn't relay on extensions.

It makes sense. Let me explain:

There's this OS called Windows, that uses extensions to determine file type. 90% of the world runs this operating system. Python likes consistency, so they keep the same rules for the other OSes

---

### Post by credobyte on 2009-09-28
> **-grubby said:**
> It makes sense. Let me explain:

There's this OS called Windows, that uses extensions to determine file type. 90% of the world runs this operating system. Python likes consistency, so they keep the same rules for the other OSes

I'm confused ( [CLICK HERE TO KNOW WHY]("http://ubuntuforums.org/showpost.php?p=7887395&postcount=8") ) :-k

---

### Post by doas777 on 2009-09-28
welcome to teh intarweb. these are all opinions, in the long run. the only fact is that the .py is needed by the compiler. perhaps it's for windows compatibility, and perhaps it's so that you can have both executable and content resources within the project folder with the same name save the extension. 
who knows.

---

### Post by -grubby on 2009-09-28
> **credobyte said:**
> I'm confused ( [CLICK HERE TO KNOW WHY]("http://ubuntuforums.org/showpost.php?p=7887395&postcount=8") ) :-k

Er, what exactly is confusing about my explanation? Windows depends on extensions to determine filetype, and is the most popular operating system.

Python is going to keep a consistent requirement for a .py extension regardless of whether the underlying system supports mimetypes or not, because Python is supposed to behave the same on every platform.

It might not make since in Linux's case individually, but if you look at the larger picture it makes perfect sense.

---

### Post by credobyte on 2009-09-28
> **-grubby said:**
> Er, what exactly is confusing about my explanation? Windows depends on extensions to determine filetype, and is the most popular operating system.
 
Python is going to keep a consistent requirement for a .py extension regardless of whether the underlying system supports mimetypes or not, because Python is supposed to behave the same on every platform.
 
It might not make since in Linux's case individually, but if you look at the larger picture it makes perfect sense.
 
Sorry, you missed the point ( my fault ). Your explanation was enough good to not to ask for a different version. Anyway, I've finally got the idea, in which cases I need to use appropriate file extensions ( credit to doas777 ).

---

### Post by jpkotta on 2009-09-28
It's not because of Windows, or at least that's not the only reason.  There is a difference between running a Python file from the command line vs. importing it as a module.  In particular, many Python files follow this idiom:
```

#!/usr/bin/env python

def foo():
    print "I'm a module!"

if __name__ == "__main__":
    def foo():
        "I'm a script!"
    foo()

```

Now, if you run it from the commmand line, it will print "I'm a script!".  If you import it and run *module_name*.foo(), it will print "I'm a module!".  So at the very least we can conclude that Python can treat imports and scripts differently.

The first line, starting with "#!", is called a shebang line, and it tells the shell to run python on the following file.  That is how Linux knows it's a Python script instead of, say, a Perl script.  Windows of course uses a file extension ".py" instead.

But when you import a file, it's the Python interpreter (which mostly functions the same way on any platform) that finds and interprets the file.  It needs to find a file given a name; it shouldn't care about the contents, because that would be much slower.  And now you can debate about why the creators of Python didn't allow it to fall back on an extensionless file matching the module name, but they didn't, and as others have said, that's the way it is.

Here's where I argue that Windows's insistence on file extensions isn't the reason.  Windows isn't doing anything with the file when it's imported (python.exe is searching the PYTHONPATH for it).  Python isn't doing anything when you double click a .py file in Windows (explorer.exe or whatever is consulting the file associations to decide how to open it).

---

