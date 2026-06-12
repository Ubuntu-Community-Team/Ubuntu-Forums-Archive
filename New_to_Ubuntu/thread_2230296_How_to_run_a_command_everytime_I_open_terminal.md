---
title: "How to run a command everytime I open terminal?"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by Ian.kz.ma on 2014-06-18
I've never used ubuntu before, need to now for work. My instructions state every time I open a new terminal I need to type:

export PATH=/opt/cross-uxl/bin:$PATH

Is there a way where this will automatically be done for me when I open terminal? I believe it has something to do with scripting but I'm a complete newbie.
Clear instructions would be much appreciated, and thanks~

EDIT: Also I'd like to know what this actually does and the meaning behind these commands if possible

---

### Post by Habitual on 2014-06-18
run ```
echo export PATH=/opt/cross-uxl/bin:$PATH >> ~/.bashrc
``` **once.**

exit terminal. 
Start terminal.
Test with ```
"echo "$PATH"
```
done.

---

### Post by Ian.kz.ma on 2014-06-18
thanks man appreciate it

---

### Post by Impavidus on 2014-06-18
> **Habitual said:**
> run ```
echo export PATH=/opt/cross-uxl/bin:$PATH >> ~/.bashrc
``` **once.**
Except that this expands the $PATH variable before writing it to .bashrc, so that .bashrc explicitly sets the complete PATH in the final line. Little difference, but if you later decide to modify the PATH above the last line of .bashrc or even in /etc/environment, you'll wonder why it doesn't work. (It should have been put in single quotes.)

The file .bashrc (it's a hidden file) contains commands that are automatically run when you start a shell. A bash shell that is. That echo command added the last line of it. Open the file in one of the text editors and have a look at it.

PATH is an environment variable that tells your system where to look for executables you want to run. If they are in one of the directories mentioned in the PATH, they will run when you give only their name. If they are not in one of those directories you have to give an explicit path to the file – even if the executable is in the current directory.

---

### Post by Habitual on 2014-06-19
> **Impavidus said:**
> (It should have been put in single quotes.)
+1 and I saw the impact in my own .bashrc right away. It was a quick and dirty response and I'm ashamed I did it.

```
echo 'export PATH=/opt/cross-uxl/bin:$PATH' >> ~/.bashrc
``` is much **cleaner**.

---

