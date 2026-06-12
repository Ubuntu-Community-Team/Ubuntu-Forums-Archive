---
title: "Trouble running python programs"
date: 2011-08-03
forum: Programming Talk
---

### Post by moorhead98 on 2011-08-03
I am totally new to programming in general. I wanted something that was easy and looked like actual English, and was used in ubuntu.
So I turned to python. Right now I'm just writing basic text programs, nothing advanced. I use IDLE (with python 2.7) for writing/running my puny programs. I saved them to my computer, and marked them as executable with chmod. but when i double click the file, and it gives me the option of running the program, running it in a terminal, or displaying it, clicking run/in terminal, nothing happens.
I thought a solution to that would be right-clicking, open with..., other application; then clicking on idle or something like that. but it shows no such option. 
Is there any way to either: 1) get hitting run/in terminal to produce something
or
2) finding a way to open files with idle

Any thoughts?

---

### Post by 7cardcha on 2011-08-03
You can open files with IDLE and press F5 to run them. Press Ctrl-O to bring up the open menu

---

### Post by cgroza on 2011-08-03
You could follow the above suggestion, but you could just run it from the command line with:

```

python filename.py

```

No need to make it executable.

---

### Post by moorhead98 on 2011-08-03
> **cgroza said:**
> You could follow the above suggestion, but you could just run it from the command line with:

```

python filename.py

```No need to make it executable.

Ok, that worked when i embedded a terminal in nautilus and then ran the code. But in a regular terminal, would it be ```
python your/directory/here/pythonprogram.py
```And, im still just wondering, is there any way to run it in idle without the use of a terminal? or opening idle then the program?
if your wondering why im trying to find another way, its just because i'm lazy.

---

### Post by moorhead98 on 2011-08-03
> **7cardcha said:**
> You can open files with IDLE and press F5 to run them. Press Ctrl-O to bring up the open menu

Im aware of that method. What i am looking for is a way to open up a python program in idle, without opening idle first. sort of like how you double click on a text file and it opens up gedit. 
Im looking for the same thing except a python file and opening up idle

---

### Post by Bachstelze on 2011-08-03
> **moorhead98 said:**
> Im aware of that method. What i am looking for is a way to open up a python program in idle, without opening idle first. sort of like how you double click on a text file and it opens up gedit. 
Im looking for the same thing except a python file and opening up idle

Right click, Open with application, custom command, /usr/bin/idle.

---

### Post by moorhead98 on 2011-08-03
> **Bachstelze said:**
> Right click, Open with application, custom command, /usr/bin/idle.

Yay! that worked perfectly.
Only comment is that it would actually be```
 /usr/bin/idle-pythonV.x
``` where ```
V.x
``` is the version (like 2.7)
But thank you, none the less!

---

### Post by Bachstelze on 2011-08-03
That is if you want to explicitly specify the Python version, but /usr/bin/idle will also work and will use the default Python version on the system (the same version you get when typing just "python" or "idle" in a temrinal).

---

### Post by moorhead98 on 2011-08-04
But if you have different versions of python installed (like 3.1 and 2.7) you have to write idle-pythonV.x , otherwise it just gives you an error saying there is no such file or program.

---

### Post by Bachstelze on 2011-08-04
It doesn't for me. There is always one version of Python that is the default and can be run with just "python" or "idle".

---

### Post by moorhead98 on 2011-08-04
Well whatever works for you. I'll stick with my own methods

---

