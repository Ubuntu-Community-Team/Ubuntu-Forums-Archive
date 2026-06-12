---
title: "Python from the terminal"
date: 2006-12-10
forum: Programming Talk
---

### Post by CS.Colt on 2006-12-10
I have Dapper 6.06 and it came installed with Python 2.4 in usr/bin/python and I found that typing "python" into the terminal puts me in interactive mode in python. My question is, "why does it do this?" In MS-DOS (I just converted from M$), you change the directory to the place where your .exe is and then type the name of said .exe in to open it. With Linux, all you do is type in the program name? Or is the terminal set to usr/bin by default. i.e. if I typed in python and it was on my desktop would it still work?

I also am wondering, if I make a .py file in emacs, gedit, vim, etc... how do I execute it from the terminal (and where do I save it to?)?

Thanks in advance!

---

### Post by christhemonkey on 2006-12-10
A file will be executed if it is in your $PATH environment variable (for example /usr/bin or /bin) 
This is the same in DOS, the given .bat files (i forget what they are called...) such as cd, dir are all in the path so can be executed in one command.

For .py's you make, you can save them anywhere (recommend in your home folder somewhere so as to avoid permissions problems.) and to execute them you do this:
```
python /path/to/my/python/file.py 
```

---

### Post by CS.Colt on 2006-12-10
Thanks for the reply.
How can I tell what my $PATH environment variable is?

---

### Post by christhemonkey on 2006-12-10
```
echo $PATH 
```

From [here]("http://http://foldoc.org/index.cgi?query=path&action=Search") explains it a bit better:
> The list of directories the kernel (under Unix) or the command interpreter (under MS-DOS) searches for executables. It is stored as part of the environment in both operating systems. 

---

### Post by meng on 2006-12-10
Almost certainly python will be in your PATH. The script you are running doesn't need to be in your PATH though. Just thought I'd clarify.

---

### Post by UbuWu on 2006-12-10
If you add the following line to the start of the program:

#! /usr/bin/env python

And then make the file executable (chmod +x filename)

You can run the program by just typing its name. It doesn't need to have the .py extension.

---

### Post by CS.Colt on 2006-12-10
eric@Lucy:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

Does this mean more than one directory is in my path?

@UbuWu, will it always be #! /usr/bin/env python or is that dependant on where you save the file, etc...

---

### Post by christhemonkey on 2006-12-10
It will always be ```
#! /usr/bin/env python
``` This is known as a shebang, which lets the shell know what interpretor to use for the script.

That means you have 8 different locations in your path:
> [LIST][*]/usr/local/sbin
[*]/usr/local/bin
[*]/usr/sbin
[*]/usr/bin
[*]/sbin
[*]/bin
[*]/usr/bin/X11
[*]/usr/games
[/LIST]


---

### Post by ssam on 2006-12-10
> **UbuWu said:**
> If you add the following line to the start of the program:

#! /usr/bin/env python

And then make the file executable (chmod +x filename)

You can run the program by just typing its name. It doesn't need to have the .py extension.

thats not right.

to run the python script after you have made it use
```
./name.py
```

the './' current directory

---

### Post by pmasiar on 2006-12-10
> **ssam said:**
> thats not right.

to run the python script after you have made it use
```
./name.py
```

the './' current directory

You are mistaken. Read why [here]("http://steve-parker.org/sh/first.shtml").

On windows, extension (after dot) is meaningful, and some extensions mark file as executable. 

On linux, dot is part of the name (you can have many dots) and "executable" is file property. 

If source file (python, perl, ruby etc) begins with #! (shebang), shell will find the file following shebang and uses it to interpret source file. Source file (with valid shebang) can end with .cgi or anything and will work *exactly* the same. 

That's all entry-level shell stuff. You can execute source file also without a shebang, when you explicitly mention interpreter and source file: ```
>python mycode.py
```

---

### Post by Kindred on 2006-12-11
> **pmasiar said:**
> You are mistaken. Read why [here]("http://steve-parker.org/sh/first.shtml").

On windows, extension (after dot) is meaningful, and some extensions mark file as executable. 

On linux, dot is part of the name (you can have many dots) and "executable" is file property. 

If source file (python, perl, ruby etc) begins with #! (shebang), shell will find the file following shebang and uses it to interpret source file. Source file (with valid shebang) can end with .cgi or anything and will work *exactly* the same. 

That's all entry-level shell stuff. You can execute source file also without a shebang, when you explicitly mention interpreter and source file: ```
>python mycode.py
```

I think the only point he was making is that the python file you are writing is likely to not to be in your path and so writing the name alone is not going to work.

---

### Post by pmasiar on 2006-12-11
My bad then. I will try to resist answering too many posts. :-)

---

