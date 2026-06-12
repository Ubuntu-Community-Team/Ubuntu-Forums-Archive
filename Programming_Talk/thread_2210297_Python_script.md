---
title: "Python script"
date: 2014-03-10
forum: Programming Talk
---

### Post by nunecas123 on 2014-03-10
I would like to execute commands inside a Python script:
Here's my idea:
```
 
import sys
import time

choose = raw_input("Would you like to execute the command X?" [Y/N]

if choose == "y":
(write command for execution) [COLOR=#ff0000]**<---**[/COLOR]
elif choose == "n"
time.sleep(1)
print "OK. Thank you and goodbye!"
sys.exit(0)
else:
print "That's not a valid command!" 
```

What should I write in there? I wanted to execute these two commands:
```
cd /home/projects/
sudo dpkg -i *.deb 
```

Thank you in advance.

---

### Post by Vaphell on 2014-03-10
[http://docs.python.org/2/library/subprocess.html#module-subprocess](http://docs.python.org/2/library/subprocess.html#module-subprocess)

that said, if these 2 lines are all that needs to happen, why not a bash script?

---

### Post by Carl H on 2014-03-10
You need == for your if statement

```
if choose == "y": 
```

---

### Post by nunecas123 on 2014-03-10
Edited.

---

### Post by ssam on 2014-03-10
You ask for 'Y' or 'N', but check for 'y' or 'n'. You should probably make it case insensitive, eg

```
if choose.lower() == "y":
```

lower() will convert there input to lowercase, or leave it untouched if it already is.

---

### Post by ofnuts on 2014-03-10
> **nunecas123 said:**
> 

What should I write in there? I wanted to execute these two commands:
```
cd /home/projects/
sudo dpkg -i *.deb 
```
You can't execute the CD has a command, because it will  be executed in a subprocess and the directory change will happen in the context of the subprocess. When you execute the "sudo dpkg", this will happen in another subprocess, and the current directory will be the one of your python script. You have to change the current directory of the python script using **[FONT=lucida console]os.chdir('/home/projects')[/FONT]**.

---

### Post by nunecas123 on 2014-03-11
> **ofnuts said:**
> You can't execute the CD has a command, because it will  be executed in a subprocess and the directory change will happen in the context of the subprocess. When you execute the "sudo dpkg", this will happen in another subprocess, and the current directory will be the one of your python script. You have to change the current directory of the python script using **[FONT=lucida console]os.chdir('/home/projects')[/FONT]**.

OK. And how do I do the rest?

---

### Post by Carl H on 2014-03-11
There are several ways that you can pass commands to the operating system in Python. As well as subprocess, have a look at the os module :- [http://docs.python.org/2/library/os.html](http://docs.python.org/2/library/os.html)

You might also want to consider gksudo instead of sudo.

It might be easier to help if you could explain what exactly it is that you are trying to do.

---

