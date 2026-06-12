---
title: "Four Python Interpreter questions"
date: 2009-01-27
forum: Programming Talk
---

### Post by ktzqbp on 2009-01-27
Hey everyone,

Recently having compiled Python 3.0 on my Ubuntu partition, I realised that the interactive interpreter has to be called by 'python3.0', rather than 'python' on Windows (which is what I've grown used to). Having done some research, I learnt that the reason for this is that many applications on Ubuntu require the Python 2.5 interpreter to function, which is fine.

However. to save myself the bother of typing that extra '3.0' every time I call the interpreter, I want to be able to call it by 'py3' or something short - how would I go about doing this?

Secondly, I also had it under Windows such that when I was loading a module at the top-level (ie, at the command prompt, rather from within the Python interpreter), I didn't have to type 'python module.py', but simply: 'module' - when loading a module, is there a way in Linux to save developers having to call the interpreter or to type the file extension?

Thirdly, in the Python interpreter in Windows I was able to navigate among previous commands using the up and down directional arrows - identical to the behaviour of the terminal. I realise that this perk isn't available in Ubuntu (up and down returns ^[[A and ^[[B respectively). Is this a gnome-terminal specific problem, is there some setting somewhere to fix this issue, or do Windows-developers simply have the one-up on this?

Finally, under Windows, if I wanted change the startup directory when launching the command prompt (to save the bother of 'cd D:/code')  was as easy as loading the shortcut's properties window. Is there a way to do this with gnome-terminal? (I have a link to /media/Stuff/code, so that it now resides in '~/Python').

Thanks in advance for your help! I'll keep looking for answers to these questions in the meantime.

---

### Post by geirha on 2009-01-27
> **ktzqbp said:**
> 
However. to save myself the bother of typing that extra '3.0' every time I call the interpreter, I want to be able to call it by 'py3' or something short - how would I go about doing this?


Easiest way is to create an alias. Edit ~/.bashrc and add a line ```
alias py3='python3.0'
```
It will not take affect until you open a new shell, so if you want it in a currently running shell, just run the line manually in that shell.

The sh-bang should still refer to python3.0 though, not py3.

> **ktzqbp said:**
> 
Secondly, I also had it under Windows such that when I was loading a module at the top-level (ie, at the command prompt, rather from within the Python interpreter), I didn't have to type 'python module.py', but simply: 'module' - when loading a module, is there a way in Linux to save developers having to call the interpreter or to type the file extension?


If you make the file executable, and make sure the first line of the script (the sh-bang) refers to the correct python binary, something like ```
#!/usr/bin/env python3.0
or
#!/usr/local/bin/python3.0
```
depending on where you installed it. You should at least be able to run it with ```
./module.py
``` after that.

> **ktzqbp said:**
> 
Thirdly, in the Python interpreter in Windows I was able to navigate among previous commands using the up and down directional arrows - identical to the behaviour of the terminal. I realise that this perk isn't available in Ubuntu (up and down returns ^[[A and ^[[B respectively). Is this a gnome-terminal specific problem, is there some setting somewhere to fix this issue, or do Windows-developers simply have the one-up on this?


The readline library handles this behavior. I haven't tried to build python 3.0, but you probably need to have libreadline-dev installed when you build python.

> **ktzqbp said:**
> 
Finally, under Windows, if I wanted change the startup directory when launching the command prompt (to save the bother of 'cd D:/code')  was as easy as loading the shortcut's properties window. Is there a way to do this with gnome-terminal? (I have a link to /media/Stuff/code, so that it now resides in '~/Python').


[nautilus-open-terminal](apt:nautilus-open-terminal) might give you the same, or at least close to that behavior.

---

### Post by eightmillion on 2009-01-27
> **ktzqbp said:**
> 
Finally, under Windows, if I wanted change the startup directory when launching the command prompt (to save the bother of 'cd D:/code')  was as easy as loading the shortcut's properties window. Is there a way to do this with gnome-terminal? (I have a link to /media/Stuff/code, so that it now resides in '~/Python').

Thanks in advance for your help! I'll keep looking for answers to these questions in the meantime.

About this, I'm not sure how this works on gnome, but you should be able to edit the link in the menu that launches gnome-terminal. You'll need to change it to **gnome-terminal --working-directory=/media/Stuff/code** note here that you have to use the full path.

Alternatively, if you want to always have any terminal you open start in the same directory, you can add  **cd /whatever/directory/you/choose** to your ~/.bashrc file.

---

### Post by ktzqbp on 2009-01-27
Couldn't ask for much more, really - all your advice worked flawlessly.

Thanks a ton, fellas :)

---

