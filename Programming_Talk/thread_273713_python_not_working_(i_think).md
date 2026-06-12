---
title: "python not working (i think)"
date: 2006-10-08
forum: Programming Talk
---

### Post by baldy1324 on 2006-10-08
just got into python (reading dive into python). im making a fibonacci program and heres the code i came up with```
#!/usr/bin/python
def fibiterative():
        n=1000
        first=0
        second=1
        third=0
        print first,"    ",second

        while n>0:
                third=first+second
                first=second
                second=third
                print third,"    "
                n=n-1

```
when i run ```
python fibonacci.py
``` i get nothing at all (runs sucessfully no output).

i made another program that has two lines - ```
def test():
        print 'hi'

```
same thing when i run this

im running debian unstable so this might be a debian problem but i doubt it, if theres any error with my programming please tell me!:)

---

### Post by meng on 2006-10-08
No it's a problem with your programming. You've defined a function (fibiterative) but you haven't called it!
You would call it by adding the line:
fibiterative()

---

### Post by po0f on 2006-10-08
baldy1324,

meng is correct.  The reason your script isn't working is because you haven't called it.  At the bottom of the script, add the lines:
```
if __name__ == "__main__":
    fibiterative()
```

Every Python module (module being either a standard Python module, or a third party one like you wrote) has a __name__ attribute, depending on how it was initialized in the script calling it.  If you run a Python script stand-alone (as opposed to importing it), it's name will be __main__.  Adding that snippet at the bottom insures two things:
[list]1) When you run the script stand-alone, it will call the function one time and exit normally, which is what you were expecting.[/list]
[list]2) You can import this module into later scripts.  It won't output anything automatically since it is imported into a script and is not the __main__ module.[/list]

---

