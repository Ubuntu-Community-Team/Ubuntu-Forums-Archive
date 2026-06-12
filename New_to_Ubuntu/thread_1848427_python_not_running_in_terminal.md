---
title: "python not running in terminal"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by upupz on 2011-09-22
I ran the below in terminal more than once. When this didn't work I ran it in IDLE 3. The code worked perfectly. can anyone explain? thanks :)
```
upupz@upupz-laptop:~$ cd Documents/Python/Basics
upupz@upupz-laptop:~/Documents/Python/Basics$ python "output input.py"
python: can't open file 'output input.py': [Errno 2] No such file or directory
upupz@upupz-laptop:~/Documents/Python/Basics$ python "input output.py"
type in some words:hello
Traceback (most recent call last):
  File "input output.py", line 1, in <module>
    some_text = input('type in some words:')
  File "<string>", line 1, in <module>
NameError: name 'hello' is not defined
upupz@upupz-laptop:~/Documents/Python/Basics$ 

```



the python code is

```
some_text = input('type in some words:')
print(some_text)
```

---

### Post by dave01945 on 2011-09-22
i think it may be due to IDLE3 using python 3 but when you run it in the terminal it is using an older version of python if you just type

```
python
```

in the terminal it will tell you what version it is using you may need to start it with 

```
python3
```

or something like that if you type python then press tab twice it will list the available versions

---

### Post by upupz on 2011-09-22
I actually got the reason right!

Didn't have a clue how to fix it tho. Thanks :)

---

### Post by dave01945 on 2011-09-22
i dont think i understand, what was the reason

---

### Post by drmrgd on 2011-09-22
> **upupz said:**
> I ran the below in terminal more than once. When this didn't work I ran it in IDLE 3. The code worked perfectly. can anyone explain? thanks :)
```
upupz@upupz-laptop:~$ cd Documents/Python/Basics
upupz@upupz-laptop:~/Documents/Python/Basics$ python "output input.py"
python: can't open file 'output input.py': [Errno 2] No such file or directory
upupz@upupz-laptop:~/Documents/Python/Basics$ python "input output.py"
type in some words:hello
Traceback (most recent call last):
  File "input output.py", line 1, in <module>
    some_text = input('type in some words:')
  File "<string>", line 1, in <module>
NameError: name 'hello' is not defined
upupz@upupz-laptop:~/Documents/Python/Basics$ 

```



the python code is

```
some_text = input('type in some words:')
print(some_text)
```


Not sure about the file not found error.  I think there's an error in your Python code leading to problem number 2.  When entering a string into a query, I think you need "raw_input", not "input".  By using input, when you type 'hello' in, it thinks it's a variable (which you've not yet assigned) rather than the string you intended.

---

### Post by upupz on 2011-09-22
It was because my terminal was running python2.(something).

Instead
```
Python3.1 "file.py"
```
runs the file

---

