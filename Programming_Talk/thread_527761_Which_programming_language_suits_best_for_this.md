---
title: "Which programming language suits best for this?"
date: 2007-08-17
forum: Programming Talk
---

### Post by Acglaphotis on 2007-08-17
Hi

What programming language suits best for this:

-Integrating with bash ,by that i mean being able to call bash command  /scripts and use variables from the programming language when i call the bash script, something similar to this

a = hello;

system("mkdir" a);

And the result being a directory named hello.

-Gui (you know, so it works with something like glade, but i dont ming having to specify by hand all the gui as long as is relatively easy to learn)

Thats it. I don't mind if its interpreted or compiled.

Thanks!

---

### Post by Quikee on 2007-08-17
For example: Python, Perl, Ruby, Bash itslef.

---

### Post by LaRoza on 2007-08-17
I would use Python. With Python, you will not have to use Bash at all, and use the os module to create directories and manipulate them. This will result in a script that will work on any OS with Python. You can use [EasyGUI]("http://www.ferg.org/easygui/") to make simple dialog boxes easily.

I didn't test these because I am at school with Windows XP
In Python:
```

import os

#I didn't try this, and you would want to add exception handling, and checking for the existance of a directory with the same name
#Prototype for the function:  os.mkdir(string *DirectoryName*,[mode])
os.mkdir(raw_input("Name: "))


```

In Python with EasyGUI:
```

import easygui
import os

#same deal as the previous, but with a gui
#you should check for the same as above and an empty string

os.mkdir(easygui.enterbox("Name:","MKDIR",""))


```

---

### Post by Dark Star on 2007-08-17
Python ftw . :) Really a gr8 language to start with :D

---

### Post by pmasiar on 2007-08-17
EasyGUI is **the** simplest GUI on the market - it even does not have events, so some people will say it it not real GUI (And I may even agree - depends on your definition of GUI), but is totally simple to use.

And of course Python is the most beginner-friendly language which scales up to real problems.

---

### Post by LaRoza on 2007-08-17
> **pmasiar said:**
> E

^See, I trimmed :D.

Will my code work?

EasyGUI is like the alert(), confirm(), and prompt() functions you see on the Web. (VBScript has similar functions too.)

---

### Post by Acglaphotis on 2007-08-17
Can python call things like mv, cp, rm and chroot ? thats basically what im looking for.

---

### Post by pmasiar on 2007-08-17
Sure: Python is "batteries included" language!
[http://docs.python.org/lib/os-file-dir.html](http://docs.python.org/lib/os-file-dir.html)

---

### Post by slavik on 2007-08-18
Perl ...

$stuff = "hello";
$output = `echo $stuff`; #(note backticks)

---

### Post by Acglaphotis on 2007-08-19
What about opening a terminal (like konsole or gnome-terminal)? Is it possible?


-Thanks

EDIT: i think popen does that, am i correct?

---

### Post by Nekiruhs on 2007-08-19
> **Acglaphotis said:**
> What about opening a terminal (like konsole or gnome-terminal)? Is it possible?


-Thanks

EDIT: i think popen does that, am i correct?
Both os.popen(command) and os.system(command) work. Popen is generally used if you want to get the output of the command. System just runs it.

---

