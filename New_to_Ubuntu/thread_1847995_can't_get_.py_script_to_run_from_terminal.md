---
title: "can't get .py script to run from terminal"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by upupz on 2011-09-21
I am trying my hand at python programming my problem is;

I have written a hello world program. Named hello world.py

It is saved in Documents/ Python/ Basics

I cd over to Basics and then entered


```
python hello world.py
```as the tutorial instructs. The output is 'hello world is not a file...etc

i tried


```
python hello_world.py

```same
I tried the ls command, it lists

```
hello world.py

```
How can get the terminal to recognised and execute the file?

I am sure I am missing some rudimentary command :L

regards and thanks

upupz

---

### Post by jtarin on 2011-09-21
To execute the script, you type python before the script you are trying to execute.

so for a script named test.py that is in /home/upupz type:

python /home/upupz/test.py

I am also assuming that you have python installed. If you do not, you need to install it before you can run any python scripts. It should be available in the repository.

[http://ubuntuforums.org/showthread.php?t=692720](http://ubuntuforums.org/showthread.php?t=692720)

---

### Post by enceladus47 on 2011-09-21
python hello\ world.py

---

### Post by mcduck on 2011-09-22
The problem is the space in the filename, you'll either have to escape the space character using backslash, like enceladus47 suggested, or surround the file name with quotes.
```

python hello\ world.py 
python "hello world.py"
```

---

### Post by upupz on 2011-09-22
Thanks guys, it was the space! I thought it might be!

anyway, real great help, it says hello to me now :D

---

### Post by aura7 on 2011-09-22
Put this as the first line of the program

#!/usr/bin/python


then you can even run the program by typing

$ ./filename.py

directly on the shell

---

### Post by josephmills on 2011-09-22
> **aura7 said:**
> Put this as the first line of the program

#!/usr/bin/python


then you can even run the program by typing

$ ./filename.py

directly on the shell


Yes this is true but you have to be in the dir that holds the script. If you like you can move to /sbin/ or /bin/ or /usr/bin  and then suod chmod +x <filename.py>
then all you have to do is type in the name of the program/script

---

### Post by mcduck on 2011-09-23
> **josephmills said:**
> Yes this is true but you have to be in the dir that holds the script. If you like you can move to /sbin/ or /bin/ or /usr/bin  and then suod chmod +x <filename.py>
then all you have to do is type in the name of the program/script

By the way, ~/bin works fine as well, if you create that directory it will automatically get included in your path.

---

