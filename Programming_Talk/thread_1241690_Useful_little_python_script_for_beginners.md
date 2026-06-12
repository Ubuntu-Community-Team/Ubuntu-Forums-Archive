---
title: "Useful little python script for beginners"
date: 2009-08-16
forum: Programming Talk
---

### Post by pepperphd on 2009-08-16
I've been studying Python for a few days, and wrote my first neat little script. It will compile your .py files into a .pyc, and chmod it for you so you can execute it from the shell with a ./filename

[php]
import py_compile #get the compile module
import sys #get the system module for argv
import os #get os so we can call chmod

if len(sys.argv) != 3: 
#if the user didnt pass the correct amount of arguments
    print "usage:", sys.argv[0],"infile","outfile" 
    #show them how to use it
    quit() 
    #and exit

infile = sys.argv[1]
outfile = sys.argv[2]

py_compile.compile(infile, outfile) 
#compile the .py to a .pyc (or whatever extension specified)

chmod_macro = "chmod +x " + outfile
#this command will allow the user to execute the outfile with a ./outfile

os.system(chmod_macro) 
#execute the chmod macro

print "success!" 
#and if all went well, inform the user and quit

[/php]

This script will compile itself if you invoke it at the command line.

```
 you@computer$ python pycompile.py pycompile.py pycompile.pyc
```That will generate a file called pycompile.pyc that you can invoke with a simple:
```
you@computer$ ./pycompile.pyc
```Then use that script to further compile your python files.
```
you@computer$ ./pycompile.pyc otherpythonfile.py otherpythonfile.pyc 
```I thought it was pretty neat and it demonstrates pythons simplicity and awesomeness.

---

### Post by MrJoeyUK on 2009-08-16
That's a handy script indeed, I think I'll take it! Thanks!

Will report back with how I got on with it. But how exactly does it work? Do I just add it onto a piece of code I've already written?

---

### Post by pepperphd on 2009-08-16
Edited to include in first post.

---

### Post by MrJoeyUK on 2009-08-16
Wow, it works great.. thanks for the further explaining.

No more typing python before my filenames!

---

### Post by nvteighen on 2009-08-16
Er... interesting, though the compiling part is just not necessary. You can execute scripts directly only by adding this as your first line in the script:

```

#!/usr/bin/env python

```

And then, chmod'ing it. The "Shebang" is not only used in Python, but in almost all scripting languages and it tells the shell to search for the correct interpreter. Chmod +x will give you execution permissions... executing it through calling the interpreter is actually regulated by the read permission :)

---

### Post by pepperphd on 2009-08-16
According to the Python documentation, "compiling" Python programs decreases the time it takes to load them into memory, so it has to be somewhat useful right?

---

### Post by Can+~ on 2009-08-16
> **pepperphd said:**
> According to the Python documentation, "compiling" Python programs decreases the time it takes to load them into memory, so it has to be somewhat useful right?

When you run a python program:

```
python mything.py
```

It will get compiled immediately and be stored as a mything.pyc.

The second time you call it, it will go look at both timestamps: if the .py has been modified, it gets recompiled, otherwise, it just goes for the .pyc.

Also, you can force compilation using the -c flag.

---

### Post by unutbu on 2009-08-16
You can also use the incron package to monitor your ~/bin directory so that any file that is placed there is automatically chmod'ed to have execute permission.

---

### Post by wmcbrine on 2009-08-17
> **Can+~ said:**
> When you run a python program:

```
python mything.py
```

It will get compiled immediately and be stored as a mything.pyc.It won't -- the .pyc isn't saved for files launched that way. However, you can start an interactive session, and type "import mything"; that saves a .pyc. (Modules imported from a script are compiled and saved too, of course.)

> *Also, you can force compilation using the -c flag.*That's not the function of "-c" that I'm seeing...

---

### Post by wmcbrine on 2009-08-17
> **pepperphd said:**
> [php]chmod_macro = "chmod +x " + outfile
#this command will allow the user to execute the outfile with a ./outfile

os.system(chmod_macro) 
#execute the chmod macro[/php]

Avoid the overhead of a system() call:

```
os.chmod(outfile, 0755)
```

---

### Post by nvteighen on 2009-08-17
What the interpreter does is to first compile the .py into a .pyc **in memory** and execute the compiled version. Python always will run compiled code.

But, of course, that is a loading overhead... That's why imported modules get compiled, to reduce time.

My comment was that compiling is not needed to make a Python script executable, but that the shebang and the execution permission are.

---

### Post by Can+~ on 2009-08-17
> **wmcbrine said:**
> It won't -- the .pyc isn't saved for files launched that way. However, you can start an interactive session, and type "import mything"; that saves a .pyc. (Modules imported from a script are compiled and saved too, of course.)

Forgot to say "in memory", but thank for correcting.

> That's not the function of "-c" that I'm seeing...

I'm really surprised by this actually. I remember doing the -c before, now I'm reading the man pages and realize I didn't.

*edit: Now I get where I got confused, it was:
[PHP]python -c "import py_compile; py_compile.compile('%f')"[/PHP]

which is pretty much what the code above does.

---

