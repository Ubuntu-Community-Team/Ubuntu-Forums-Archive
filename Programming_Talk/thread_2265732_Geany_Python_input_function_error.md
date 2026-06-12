---
title: "Geany Python input function error"
date: 2015-02-17
forum: Programming Talk
---

### Post by Ethan_Wright on 2015-02-17
I recently switched from Windows to Ubuntu so I wanted to see what python IDEs are available, I tried Geany first, the print function seems to work fine but the input function doesn't seem to work. 
If I type in print("hello,world") the terminal comes up and displays hello world all normal there, however when i try a simple input string like input("wht is your favorte colour") I get this:
what is your favorite colour orange
Traceback (most recent call last):
  File "untitled.py", line 1, in <module>
    input("what is your favorite colour ")
  File "<string>", line 1, in <module>
NameError: name 'orange' is not defined


------------------
(program exited with code: 1)
Press return to continue

also If i take the same code and put it into another IDE I get the intended result.
if the kind people of the Ubuntu forum could assist me in trying to solve the problem tha would be great :)

---

### Post by steeldriver on 2015-02-17
At a guess, one of them is running your code in python3.x whereas the other is using python2.x 

```

$ python3 -c 'ans = input("enter color: "); print(ans)'
enter color: orange
orange

```
whereas
```

$ python -c 'ans = input("enter color: "); print(ans)'
enter color: orange
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "<string>", line 1, in <module>
NameError: name 'orange' is not defined

```

In python2.x, you would need to use raw_input I think:

```

$ python -c 'ans = raw_input("enter color: "); print(ans)'
enter color: orange
orange

```

---

