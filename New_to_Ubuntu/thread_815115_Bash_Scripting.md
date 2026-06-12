---
title: "Bash Scripting"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by ezufelt on 2008-06-01
I am a absolute beginner to Ubuntu and Bash programming.  The last time I looked at Linux was RedHat 6, when it was new.

I am attempting to write a simple HelloWorld script.  I am getting a Bash: command not found error.  

Here is what I've done:
1. created hello.sh in gedit with following content.
[CODE]
#!/bin/bash
echo "Hello World!"
[CODE]

2. The file is saved in my home directory ~.
3. I set chmod +x hello.sh.
4. tried to run : hello.sh and sudo hello.sh with same problem.
5. I'm sure that I am in the directory with the script and that I am aware of the case of the filename.

Any help appreciated.

---

### Post by aos101 on 2008-06-01
To run the script you need to type "./hello.sh" (without the quotes) while in your home directory.

---

### Post by Joeb454 on 2008-06-01
By default Ubuntu won't look in your current directory for the command. Hence the need for ./

you could also run ```
sh script.sh
```

---

### Post by aos101 on 2008-06-01
If you run "sh script.sh" on Hardy, it will run the script through dash and not Bash (because sh is just a symlink to dash).  If you want to run it like that, you should use "bash script.sh" I think.

---

### Post by Prospero2006 on 2008-06-01
You could also copy it to a directory in the system path.
ie:
cp hello.sh /usr/local/bin

Then type hello.sh

---

### Post by Joeb454 on 2008-06-01
> **Prospero2006 said:**
> You could also copy it to a directory in the system path.
ie:
cp hello.sh /usr/local/bin

Then type hello.sh

Actually you would need ```
sudo cp hello.sh /usr/local/bin
```

---

### Post by Barriehie on 2008-06-01
You could make a folder called *myscripts* and then add that to your path in your .bashrc file.  

I have this appended to the end of my .bashrc file.

```

#
#    Add my paths to the environment variable $PATH
#
PATH=$PATH:/home/barrie/myscripts

```Barrie

---

### Post by sdennie on 2008-06-01
Copying it to a /usr/local is a bad idea though.  It's much better to make a ~/bin directory, add it to your path and put your scripts there.  It's surprising how fast your script collection can build up and, they are then localized in your user directory and not spread allover the system.

---

### Post by Joeb454 on 2008-06-01
> **vor said:**
> Copying it to a /usr/local is a bad idea though.  It's much better to make a ~/bin directory, add it to your path and put your scripts there.  It's surprising how fast your script collection can build up and, they are then localized in your user directory and not spread allover the system.

+1 to that...which reminds me, I need to consolidate mine into a programming folder, then separated by language :)

---

### Post by noynac on 2008-06-01
> **Barriehie said:**
> You could make a folder called *myscripts* and then add that to your path in your .bashrc file. I have this appended to the end of my .bashrc file....

I also do it this way, and it works well. I started with 2 or 3 scripts but this number has now grown to 24. I still find myself editing some of these scripts on a semi-regular basis, so it's good to have them close at hand.

---

