---
title: "Where are programs stored?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Hybrid86 on 2008-06-04
in windows, when you want to open a program without a shortcut, you to to C:\Program Files\
In ubuntu, when do I go?

---

### Post by ConMan318 on 2008-06-04
A lot of them are in /usr/lib/, but some are in other places depending on what they do/how you installed them.

---

### Post by Steveway on 2008-06-04
Just type the name of the program into a terminal.
For example firefox will open Firefox and gedit will open gedit.
You don't need to know where everything is don't bother with it.
If you really want to know then read up on the unix-filesystem-structure.

---

### Post by sayakb on 2008-06-04
Most of the installed programs are in /usr/bin and /usr/sbin. Sine both of these folders at added to the PATH variable, you just have to type the program's name at a terminal and execute them as Steveway said.

---

### Post by robertchahine on 2008-06-04
like everyone said.
you can find them in /usr/bin or /usr/lib.

but if you're asking about the place that the folder are stored, you can open your home directory and press Ctrl + H to show hidden files, because the software you install , are hidden in your home directory

---

### Post by ConMan318 on 2008-06-04
> **robertchahine said:**
> like everyone said.
you can find them in /usr/bin or /usr/lib.

but if you're asking about the place that the folder are stored, you can open your home directory and press Ctrl + H to show hidden files, because the software you install , are hidden in your home directory

Yeah, and if you're looking from the command line type "ls -a" in your home directory (without quotes of course) and they'll show up.

---

### Post by Steveway on 2008-06-04
> **robertchahine said:**
> like everyone said.
you can find them in /usr/bin or /usr/lib.

but if you're asking about the place that the folder are stored, you can open your home directory and press Ctrl + H to show hidden files, because the software you install , are hidden in your home directory

That's wrong. Programs normally never get installed into your Home folder.
Only userspecific settings are stored there, systemwide settings are stored in /etc

---

### Post by ConMan318 on 2008-06-04
> **Steveway said:**
> That's wrong. Programs normally never get installed into your Home folder.
Only userspecific settings are stored there, systemwide settings are stored in /etc

I disagree.

In your home directory, if you go (for example) beginning at your home directory:
```

ls -a
cd .firefox
firefox

```

you will have navigated to the hidden firefox folder, and will have started firefox.  Not every program is stored there, but there are a few.  I guess technically the program isn't in the home folder, but a directory containing it is.

---

### Post by Delever on 2008-06-04
[Filesystem Hierarchy Standard]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard")

---

### Post by sayakb on 2008-06-04
> **Steveway said:**
> That's wrong. Programs normally never get installed into your Home folder.
Only userspecific settings are stored there, systemwide settings are stored in /etc

Exactly. Only settings/config files, installed icons, themes, fonts and trash goes to the home folder.

---

### Post by sayakb on 2008-06-04
> **ConMan318 said:**
> I disagree.

In your home directory, if you go (for example) beginning at your home directory:
```

ls -a
cd .firefox
firefox

```you will have navigated to the hidden firefox folder, and will have started firefox.  Not every program is stored there, but there are a few.  I guess technically the program isn't in the home folder, but a directory containing it is.

You can run by typing **firefox** since you have /usr/bin in the PATH variable. Linux searches the path variable when a command is fired. I myself don't have a .firefox folder but a .mozilla folder with no executables.

Only on one occasion that when you compile from source, you might have an executable residing some place other than the /usr/bin

---

### Post by ConMan318 on 2008-06-04
> **LinuxIsInnovation said:**
> You can run by typing since you have /usr/bin in the PATH variable. Linux searches the path variable when a command is fired.

So it's just a link to the actual /usr/bin/ program and not the actual program launcher from the ~/.firefox directory?

---

### Post by sayakb on 2008-06-04
Unless you have compiled from source. firefox should be in your /usr/bin
```
ls -l /usr/bin/firefox
```

---

### Post by Steveway on 2008-06-04
> **ConMan318 said:**
> So it's just a link to the actual /usr/bin/ program and not the actual program launcher from the ~/.firefox directory?

Not exactly, if you type just the name in like you did then your system will look into your so called PATH it's a normally fixed set of adresses to look for an executable with that name for your computer. If you want to execute a binary that is in the folder you are actually in with the terminal then add and ./ to the beginning. ./firefox will make your system look for an executable called firefox in the folder you are in.

---

### Post by robertchahine on 2008-06-04
i'm wrong!
i'm sorry for that.you're maybe right.
but last night i installed matlab and other softwares.
i can only find them in the home directory.
even if i type ```

locate matlab 
```

the output show that matlab is only located in home directory

---

### Post by sayakb on 2008-06-04
> **robertchahine said:**
> i'm wrong!
i'm sorry for that.you're maybe right.
but last night i installed matlab and other softwares.
i can only find them in the home directory.
even if i type ```

locate matlab 
```the output show that matlab is only located in home directory

Did you compile it from source, or installed from a debian package?

---

### Post by Steveway on 2008-06-04
> **robertchahine said:**
> i'm wrong!
i'm sorry for that.you're maybe right.
but last night i installed matlab and other softwares.
i can only find them in the home directory.
even if i type ```

locate matlab 
```

the output show that matlab is only located in home directory

So you did compile from source and did not do a sudo make install.
Or you defined a destination yourself instead of using the normal way.
Look at my frequent use of the word normally and then you know where your case of Matlab falls into.
Also LiI mentioned something like this just a few posts ago.
EDIT: He's fast. ^^

---

### Post by robertchahine on 2008-06-04
installed it from iso Cd.i think a compiled source

---

### Post by sayakb on 2008-06-04
As for example, I have the firefox executable in /usr/lib/firefox-3.0b5 folder.

---

### Post by sayakb on 2008-06-04
> **robertchahine said:**
> installed it from iso Cd.i think a compiled source

As I mentioned earlier, you may have the executable somewhere else when you compile it from source.

---

### Post by The Cog on 2008-06-04
The hidden .firefox directory in your home folder only holds your personal firefox settings - bookmarks, history etc.

To find where a program actually is, use the command **which firefox** which tells you where the executable is, by searching your path for it just as the shell would. For most Ubuntu users, **which firefox** will return **/usr/bin/firefox**. However, **ls -l /usr/bin/firefox** will show that that is is actually a symbolic link to the real executble in its install directory, somewhere in /usr/lib.

---

### Post by The Cog on 2008-06-04
Oops - double-post somehow.

---

### Post by worldy on 2008-06-05
To see which file is called when any valid shell command is given (except for shell built ins)

In terminal, type

```

which 'programname'

```

Eg 
which firefox
which gimp
which python
which which

Use the file command to find whether the called file is a symbolic link to any other file . The destination files can in turn be links to other files

```

file 'filename'

```

---

