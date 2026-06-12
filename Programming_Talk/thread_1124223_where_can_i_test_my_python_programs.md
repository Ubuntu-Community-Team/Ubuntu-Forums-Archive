---
title: "where can i test my python programs?"
date: 2009-04-13
forum: Programming Talk
---

### Post by superplasmafist on 2009-04-13
im new at programming so i dont know this.
but i write my codes in a text editor and save it as a .py.

now where can i check that it works? can i install something for this?

i tired the shell but that wasnt good

thanks

---

### Post by benj1 on 2009-04-13
just cd to the directory where your program is and 
```
python your_program.py
```
runs your program in the python shell

or you can make your script executable

```
chmod +x your_program.py
```

then you can just run it by typing the program name.
just don't forget to add

```
#! /usr/bin/env python
```
to the start of your script

---

### Post by superplasmafist on 2009-04-13
but the program doesnt work in the shell. is it something wrong with the program then?

arent there any other way? some app?

---

### Post by benj1 on 2009-04-13
if you're using ubuntu, python is installed by default

if you type 'python' in the terminal it should take you to a python shell
( your user name etc will be replaced by '>>>') you can quit by pressing ctrl-d. if this works and 'python script.py' doesn't, its something wrong with your script, if you post it we might be able to help

---

### Post by superplasmafist on 2009-04-13
but i tried to write alittle more complex program. maybe i wrote the program wrong cause the simple ones works.

i post again when and if im sure it wasnt the code.

thanks

---

### Post by drubin on 2009-04-13
> **benj1 said:**
> ```
#! /usr/bin/env python
```
to the start of your script

This is called a [Shebang]("http://en.wikipedia.org/wiki/Shebang_(Unix)").

---

