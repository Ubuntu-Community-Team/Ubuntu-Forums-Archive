---
title: "C compiler problems"
date: 2008-12-03
forum: Programming Talk
---

### Post by lilbrownjumpsuit on 2008-12-03
Hey guys,

I'm trying to compile my c code but when I type:

[CENTER]gcc file.c[/CENTER]
I get:
[CENTER]gcc: file.c: No such file or directory
gcc: no input files[/CENTER]

Thanks for the help.

---

### Post by jpkotta on 2008-12-03
Where did you save your file?

---

### Post by lilbrownjumpsuit on 2008-12-03
Saved the file under my documents.

---

### Post by Idefix82 on 2008-12-03
You need to be in your documents folder when you type this command.

---

### Post by Joeb454 on 2008-12-03
Make sure you have build-essential installed by running ```
sudo apt-get install build-essential
```

Then make sure you're in the correct directory and run ```
gcc file.c -o file
```

That specifies what you want the output file to be called :)

---

### Post by lilbrownjumpsuit on 2008-12-03
How do I make sure I'm in the correct directory? I think that is my problem.

---

### Post by namegame on 2008-12-03
The command pwd will show you your current working directory.

---

### Post by dexter on 2008-12-03
And cd /your/path lets you navigate to other directories.

---

### Post by snova on 2008-12-03
When operating the command line, you are always "in" a directory. Commands are executed relative to this directory.

Since the default directory to start in when opening a terminal is your home directory and you saved the source to the Documents folder, GCC cannot find your file.

The 'pwd' command is an abbreviation for Print Working Directory. Most of the time you don't need it though, since it should also be part of your prompt.

The 'cd' command means Change Directory. Since the Documents folder is located directly in your home folder, a simple 'cd Documents' should be enough for GCC to be able to find your file.

A useful feature of Bash (that sometimes works elsewhere) is that you can use '~' as short for your home directory. Meaning 'cd ~/Documents' is the same as 'cd /home/<username>/Documents'.

Running 'cd' without arguments returns you to your home directory.

For the purpose of illustration, you could also do:

```
gcc -o Documents/file Documents/file.c
```

By specifying a relative path.

---

### Post by geirha on 2008-12-03
If you are using gnome and gnome-terminal, you may also use drag and drop to aid you. Just type in a terminal "gcc " (gcc followed by a space, but do not hit enter yet). Then locate your file.c with nautilus (the default "explorer"), and drag file.c to the terminal window. It should then fill in the correct path to the file for you. Hit enter to have it compile.

Another way to find your file is to search for it with the find command. ```
find ~ -name file.c
``` If the file is somewhere under your homedir, that find command should find it.

---

