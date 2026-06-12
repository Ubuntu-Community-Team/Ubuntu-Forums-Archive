---
title: "Importing modules to the Python Interpreter in Ubuntu?"
date: 2007-08-08
forum: Programming Talk
---

### Post by Wolfraptor1 on 2007-08-08
Alright, here it is, I'm learning Python for the first time and I'm using Xubuntu 7.04. The question I have, is where do I keep my modules so I can import them because the official tutorial says just type "import" and then the module name but when I do that I get an error, where do I store the files to get access to them and such? Oh yes, and another question I had, I'm using the Python interpreter from the command line, how do I get the files and is there a good GUI version I can get?

---

### Post by ErnobmaS on 2007-08-08
Well, I'm certainly not the one that should be answering, because I'm just learning too. But I can tell you what you should Google: the environment variable PYTHONPATH. If you add a directory to your PYTHONPATH, say /home/yourname/pythonModules, then any Python modules you put in there will be available to the interpreter; just type "import myModule" for a file myModule.py. I think you have to add the directory to PYTHONPATH in the file ~/.bashrc in order for it to be there when you restart your computer or Python session. As for a GUI, check out Idle from the repositories. Hope I could help!

---

### Post by rjseagraves on 2007-08-08
From [The Python Tutorial, Section 6.1.1 "The Module Search Path"]("http://docs.python.org/tut/node8.html#SECTION008110000000000000000"):
> 
When a module named spam is imported, the interpreter searches for a file named spam.py in the current directory, and then in the list of directories specified by the environment variable PYTHONPATH. This has the same syntax as the shell variable PATH, that is, a list of directory names. When PYTHONPATH is not set, or when the file is not found there, the search continues in an installation-dependent default path; on Unix, this is usually .:/usr/local/lib/python. 

Hope this helps.

---

### Post by smartbei on 2007-08-09
What modules are you trying to import? Some should be no problem (like math, random, pickle) and if they are it is probably the PythonPath, as stated above. However, if you are trying to import PyGTK or something along those lines, you might need to install the equivalent package from the repos - i.e. for PyGTK I believe it is python-pygtk.

---

### Post by steve.horsley on 2007-08-09
You can put your module files in one (or all) of these directories:
> /usr/lib/python2.3/site-packages
/usr/lib/python2.4/site-packages
/usr/lib/python2.5/site-packages

and that then make the module importable to anyone. Alternatively, keep the module in the current directory along with the app if you don't want to publish it. Or set PYTHONPATH of course.

As for an editor, I personally just use gedit or geany.

---

### Post by digby on 2007-08-09
You can also add path locations from inside your script:```
import sys
sys.path.append("/some/dir/path")
```

---

