---
title: "Problems Running Python Scripts"
date: 2007-10-31
forum: Programming Talk
---

### Post by jusael on 2007-10-31
Hi, 

I'm new to Ubuntu and Linux in general, and I have a problem making a Python script run without the terminal. I'm wondering whether this is possible in Linux, but I'd like to have Ubuntu execute the .py file when I either double-click it or right-click it and select "Open with 'python'".

I tried adding "#! usr/bin/env python" to the script and also doing chmod +x <scriptname>. That way the system seems to create the compiled .pyc when running the script, but the UI I have in the script doesn't show. I'm using tkinter for the UI and have installed the python-tk package.

I also want to make the script so that it will execute this way on most Linux flavors, not just Ubuntu.

Any help is welcome :)

---

### Post by LaRoza on 2007-11-02
That would not create a compiled python script.

Try using: #! /usr/bin/python

---

### Post by dataw0lf on 2007-11-03
Neither would create a .pyc (compiled) python file.  To compile a module, you need to either import it (so, a quick way to compile the file would be to simply instantiate the python interpreter and type "import file_name"), or explicitly specify it, ala py_compile:
```
import py_compile
py_compile.compile("file_name.py")
```
The added benefit of py_compile is that it doesn't execute the code, like import will do.

Cheers!

---

### Post by ankursethi on 2007-11-03
When you run the script via the terminal, does the Tk UI show up? Try it and post the output here.

---

### Post by WinterWeaver on 2007-11-03
If you added the line:
```
#! /usr/bin/env python
```

and then made the file executable, then you can execute it by typing
>  ./program.py

the 'dot' , 'forward-slash' is neccessary

Note that does not mean it creates a 'compiled' version tho. Follow suggestions from the other posters on creating compiled python scripts :)

have fun

WW

---

### Post by jusael on 2007-11-04
Yes, the tk interface does show up and the program works normally when I run the script from the terminal.

But is it not possible to make the script run without the terminal in Ubuntu, or do I need to have the script compiled for that to work? That sounds like there would be problems when running the script in systems with different Python versions.

Thanks for the help, 
JS.

---

### Post by ankursethi on 2007-11-04
Try right clicking on the script -> permissions -> check the "Allow executing this file as a program" box. Does it still not work?

(This is a pretty strange problem you have)

---

### Post by jusael on 2007-11-04
I looked at the permissions of the script, and I'm having trouble changing myself to be the owner of the file. It says that the current owner is root, and that I'm not the current owner so I cannot change the permissions. I tried doing sudo chown myusername script.py but that didn't seem to have an effect even though I tried logging out.

---

### Post by ankursethi on 2007-11-04
Run Nautilus through sudo and try changing ownership via the GUI.

---

### Post by red_Marvin on 2007-11-04
or *sudo chown YourUserName:YourUserName Yourfile.py*

---

### Post by jusael on 2007-11-05
This is weird. sudo chown myusername:myusername script.py didn't have any effect. I tried sudo nautilus, and now the permissions menu for the script were enabled, but when I changed myself to be the owner of the file, it changed back to root almost instantly.

---

### Post by geirha on 2007-11-05
What file system is it located on? If it's on a fat partition for instance, you can't change ownership that way.

---

### Post by jusael on 2007-11-05
That seemed to work. I moved the script to another drive and I was able to change the permissions.

I checked the "Allow executing this file as a program", but nothing seems to happen when I double-click the script. I also tried "Run" and "Open with python" options from the right-click menu, but they didn't work either.

---

