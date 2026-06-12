---
title: "Running Python Script in Terminal"
date: 2013-04-07
forum: Programming Talk
---

### Post by Bresser on 2013-04-07
Hello I made a little python script (I'm learning it right now) that I named SecondConverter. I put the ```
#!/usr/bin/python
``` in and everything, I made it executable. But still when I click on it and click run nothing at all happens. What do I do to run it? I can't run it in terminal because it doesn't show the output which I need to see.

---

### Post by slooksterpsv on 2013-04-07
Does the program output anything via the print command? In terminal it should show that, otherwise, it'll just run the program when you double click on it.

---

### Post by Bresser on 2013-04-08
Yes it asks the user how many secs to convert into hrs, minutes, and secs. So when I run in terminal it asks the first question I enter and then terminal closes

---

### Post by ofnuts on 2013-04-08
Of course... if you start it by click on it, then that's the only process and the windows closes when the program exits, which happens milliseconds after it printed its output. So either you add another read operation after your output so that the program doesn't exit immediately, or you run your python from a terminal, or you beef up your code to use a windowing interface..

---

### Post by Bodsda on 2013-04-08
[HR][/HR]You should also consider changing your shebang line to use the standard python environment variable. 
This will ensure that you're scripts still work if the python executable location is changed
```

#!/usr/bin/env python

```

The terminal only closes because it was opened just to run your script, when that finishes it then closes. If you launch your terminal by hand and then execute your script, you will see the output
```

python ~/path/to/your/script.py

```

Bodsda

---

### Post by Tony Flury on 2013-04-10
> **Bresser said:**
> Yes it asks the user how many secs to convert into hrs, minutes, and secs. So when I run in terminal it asks the first question I enter and then terminal closes

If you are running the script from the command line then the terminal should not close under Linux. The application may close but the terminal shouldn't - it sounds like you have an interesting bug - or you are running the command in a strange way.

When you double click an application icon in linux, it has no idea if that program needs to open a terminal to display output, so it doesn't open one. The actual process is likely to just fail silently as it has nowhere to send it's output.

This is different to windows which (I think) opens a terminal if the program needs it.

Can you show us : 

1) Exactly what command you are using to run you application in the terminal

2) The code of your application.

---

### Post by schragge on 2013-04-10
Or you can specify ```
Terminal=true
``` in the .desktop file for your application. See [Desktop Entry Specification](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s05.html#key-terminal).

---

### Post by Bresser on 2013-04-10
To execute it I'm clicking on it and running from terminal because it says it doesnt exist as for the code inside is:

```

first_seconds = input("Please Enter Amount of Seconds to Convert")
hours = first_seconds // 3600
seconds_after_hours = first_seconds % 3600
minutes = seconds_after_hours // 60
seconds = seconds_after_hours % 60

print(hours, "Hours", minutes, "minutes", seconds, "seconds")

```

---

### Post by Tony Flury on 2013-04-10
> **Bresser said:**
> To execute it I'm clicking on it and running from terminal because it says it doesnt exist as for the code inside is:

```

first_seconds = input("Please Enter Amount of Seconds to Convert")
hours = first_seconds // 3600
seconds_after_hours = first_seconds % 3600
minutes = seconds_after_hours // 60
seconds = seconds_after_hours % 60

print(hours, "Hours", minutes, "minutes", seconds, "seconds")

```

What command are you running to execute this from the terminal ? Is the above the full contents of the file ?

---

### Post by Bresser on 2013-04-10
im not using a terminal command I am double-clicking on the file and clicking run from terminal
and no at the top is
```

#!/usr/bin/env python

``` 
and i already checked to make sure that was the right hash bang

---

### Post by Mikeb85 on 2013-04-11
> **Bresser said:**
> Hello I made a little python script (I'm learning it right now) that I named SecondConverter. I put the ```
#!/usr/bin/python
``` in and everything, I made it executable. But still when I click on it and click run nothing at all happens. What do I do to run it? I can't run it in terminal because it doesn't show the output which I need to see.

It works fine.  

Save it as **file.py**, cd into the directory you put it in (if you put it into documents, type **cd Documents** into the terminal then hit enter), and then run it using the command **python file.py**

---

### Post by msandoy on 2013-04-12
This is a script that displays text in the terminal only. To run it and see the output, open a terminal, cd to the directory where you have the file, start it by typing ./file.py
This will either run the program, or display any errors found. Remember to use chmod +x file.py before trying to run it. (Only needs to be done once, the execute permissions does not change even if you edit the file.)

---

### Post by Vaphell on 2013-04-12
get used to using terminal at least during coding, debugging is much faster when you can simply tap up arrow to recall the last command (or type *!!*) and you get to see all previous outputs. Doubleclicking and 'selecting run in terminal' every single time gets old really fast.

---

### Post by Mikeb85 on 2013-04-12
> **Vaphell said:**
> get used to using terminal at least during coding, debugging is much faster when you can simply tap up arrow to recall the last command (or type *!!*) and you get to see all previous outputs. Doubleclicking and 'selecting run in terminal' every single time gets old really fast.

Yup, not to mention being able to test functions in the interactive Python shell.  I mainly do Ruby, still kind of a beginner, but I couldn't imagine trying to program without the terminal...

---

### Post by Vaphell on 2013-04-12
i forgot to mention: and if you use text editor that can have embedded terminal (eg geany, gedit) it's even better because everything you need is in one place and you don't have to switch windows every 5 seconds.

---

### Post by ofnuts on 2013-04-13
> **Vaphell said:**
> i forgot to mention: and if you use text editor that can have embedded terminal (eg geany, gedit) it's even better because everything you need is in one place and you don't have to switch windows every 5 seconds.

Not to forget Kate, for the KDE users...


All this reminds me of that colleague who set about writing his first .BAT using... MS-Word. At least he had it formatted in Courrier ($deity knows what happens when you run a .BAT written in Comic ans).

---

### Post by Carl H on 2013-04-23
What you have written so far is a command line program. It needs to be run from the command line - i.e. a 'terminal' window. Like Bodsda said previously.

---

### Post by alan9800 on 2013-04-24
> **ofnuts said:**
> Not to forget Kate, for the KDE usersor even leafpad for Xubuntu/Lubuntu users ;) .
Apart this, it might be interesting to make a more user-friendly output by using the [Tkinter](http://docs.python.org/release/2.7.3/library/tkinter.html#module-tkinter) module.

---

