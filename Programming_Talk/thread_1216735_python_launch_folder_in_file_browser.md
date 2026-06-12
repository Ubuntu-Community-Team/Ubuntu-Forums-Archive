---
title: "python launch folder in file browser"
date: 2009-07-18
forum: Programming Talk
---

### Post by eggdeng on 2009-07-18
I'm writing a little app where at one point I need to open a folder created by the user in a file browser window. If I specify the folder as in
```
		os.system('thunar /home/eggdeng')

```
it works fine. The problem is that I need to be able to pass the folder name as a variable, something like

```
		os.system('thunar dirname')

```
Obviously this doesn't work as the system looks for a folder called dirname. So, can anyone help me out with the right syntax?
One more (related) question: is there any way to call the file browser as such without specifying thunar, nautilus or whatever?

---

### Post by smartbei on 2009-07-18
For the first question, what you are looking for is string formatting. Take a look at [http://diveintopython.org/native_data_types/formatting_strings.html](http://diveintopython.org/native_data_types/formatting_strings.html) for more information. Specifically, you can have:
```

os.system("thunar %s" % (dirname_variable,))

```
Actually, for something this simple, you can also just concatenate:
```

os.system("thunar " + dirname_variable)

```

As for the second question... See my post here:
[http://ubuntuforums.org/showthread.php?p=7552628&highlight=python+gconf#post7552628](http://ubuntuforums.org/showthread.php?p=7552628&highlight=python+gconf#post7552628)

---

### Post by benj1 on 2009-07-18
@smartbei
wouldn't your approach to getting the file manager require gnome?


i was hoping os.environ[] would have something (it has defaults for web browser and txt editor) but it doesn't 

the only thing i can suggest is looking for the common file managers in /usr/bin

---

### Post by unutbu on 2009-07-18
To make the program file-browser-agnostic, you could use
```

os.system("xdg-open " + dirname_variable)
```

This should work for both GNOME and KDE users.

---

### Post by monraaf on 2009-07-18
> **unutbu said:**
> To make the program file-browser-agnostic, you could use
```

os.system("xdg-open " + dirname_variable)
```

This should work for both GNOME and KDE users.

Ack, but remember that os.system commands are executed by the shell, so better put the directory in quotes otherwise it won't work if there are are spaces in the path.

```

os.system("xdg-open '%s'" % dirname_variable)

```

---

### Post by Can+~ on 2009-07-18
[http://docs.python.org/library/os.html#os.startfile](http://docs.python.org/library/os.html#os.startfile)

In case you need to open a file with the default app, although, I'm not sure what will try to do with a foldername, *testing*.

Lol, it's windows only.

---

### Post by eggdeng on 2009-07-19
Many thanks for all the help. Smartbei solves the first problem neatly.
For some reason however, gconf returns nautilus for the file manager - I am using Fedora 10 XFce spin :?
So Unutbu's suggestion is just the job. Thanks again.

---

### Post by smartbei on 2009-07-19
I assumed that gconf would be updated according to the system it was installed on, but I didn't check. Good to know about xdg-open :-).

---

