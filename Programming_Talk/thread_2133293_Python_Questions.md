---
title: "Python Questions"
date: 2013-04-07
forum: Programming Talk
---

### Post by Bresser on 2013-04-07
I have a few questions about Python:

One what are some real-life applications that are composed from Python.
 
Two using SPE how do I compile a program? I mean you can't test an input feature using SPE, so I want to compile it and run it as a executable like you would for a real program. How would I do that?

---

### Post by trent.josephsen on 2013-04-07
Reddit. Portage. Mercurial. Dropbox. Civ IV, according to Wikipedia. Many GNOME apps and libraries are written completely or partially in Python too.

Being a Vim guy, I've never used SPE.

---

### Post by r-senior on 2013-04-07
You don't normally compile Python scripts but you can make them into "real programs" on Linux and Mac OS by adding this line at the top:

```
#!/usr/bin/env python
```

Make it executable, e.g. chmod +x <your script file>, and run it like you would any compiled program.

---

### Post by Vaphell on 2013-04-07
ad 1: [http://en.wikipedia.org/wiki/List_of_Python_software](http://en.wikipedia.org/wiki/List_of_Python_software)

---

### Post by Bresser on 2013-04-07
Hello when I tried to use
```

chmod +x myprogramname.py

```
It told me no file or directory found. Any Ideas Why?

---

### Post by oldfred on 2013-04-08
See 
man chmod

But I think the command is 
chmod a+x myprogramname.py

where the a is all users, see the man for list of other options.

---

### Post by Tony Flury on 2013-04-08
> **Bresser said:**
> Hello when I tried to use
```

chmod +x myprogramname.py

```
It told me no file or directory found. Any Ideas Why?

Can you do a 
```

ls -al

```
in your directory, can you see the file ? if chmod doesn't work it is nothing to do with python - chmod doesn't care what type of file you are trying to change - it only cares if the file exists and if you have permissions to change the permissions.

[QUOTE=oldfred]
    But I think the command is
    chmod a+x myprogramname.py

    where the a is all users, see the man for list of other options. 
[/QUOTE]
If the file is owned by you, and only you need to run it then you don't need "a+x", "+x" will work fine.

---

### Post by Bresser on 2013-04-08
I used ```
ls -al
``` and it did work. But the program is like highlighted its weird. I am attaching a screenshot of it. [ATTACH=CONFIG]241110[/ATTACH]

---

### Post by ofnuts on 2013-04-08
With the default colors  a link in red is a link that leads to a non-existent file.

---

