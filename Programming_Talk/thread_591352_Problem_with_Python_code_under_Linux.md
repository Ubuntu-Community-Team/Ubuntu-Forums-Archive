---
title: "Problem with Python code under Linux"
date: 2007-10-25
forum: Programming Talk
---

### Post by dmsynck on 2007-10-25
Hi all,

I am working on moving a small Python script from Windows to Linux and am running into a problem with one section of the code. Here is the snippet that is giving me problems.

```

for x in Dict1.keys():
        return_code = subprocess.call(["/bin/ping -q -c 3",Dict1[x]])
        if return_code == 0:
            f.write(str(roomNo[i]) + ": \t " + str(Dict1[x]) + "\t Pass \n")
            i = i + 1
            num_pass = num_pass + 1
        elif return_code == 1:
            f.write(str(roomNo[i]) + ": \t " + str(Dict1[x]) + "\t Fail \n")
            i = i + 1
            num_fail = num_fail + 1
        else:
            pass

```

This code, modified accordingly, runs just fine under windows. Under Linux, it has a problem with the subprocess call.

Thanks in advance

---

### Post by basic0 on 2007-10-25
What is the exact error this produces?

---

### Post by dmsynck on 2007-10-25
Here is the traceback.

```

Traceback (most recent call last):
  File "./IPinger_Dev.py", line 323, in ?
    main()
  File "./IPinger_Dev.py", line 304, in main
    testIP()
  File "./IPinger_Dev.py", line 129, in testIP
    return_code = subprocess.call(["/bin/ping -q -c 3",Dict1[x]])
  File "/usr/lib/python2.4/subprocess.py", line 412, in call
    return Popen(*args, **kwargs).wait()
  File "/usr/lib/python2.4/subprocess.py", line 542, in __init__
    errread, errwrite)
  File "/usr/lib/python2.4/subprocess.py", line 975, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

```

Thanks 

dmsynck

---

### Post by hecato on 2007-10-25
The child cannot be executed, thought havent seen the subprocess module, are you sure is the correct way to call 


> subprocess.call(["/bin/ping", "-q -c 3", "home"])


From what I remember from launching subpresses in C (haha, I dont remember the name of the function, isnt fork... thus env... vfork??, blah dont remember it) the point is that the first argument is the only the name of the process to launch ;), and if it have extra arguments thus others, not the string that you will use when in cmd line...

---

### Post by basic0 on 2007-10-25
That's what it looks like to me too. Admittedly, I don't know a whole lot about Python, but I think subprocess.call() wants the first argument to be the command and the second to be all of the arguments. It's looking for a command called "/bin/ping -q -c 3", which of course, doesn't exist. I think it should be more along the lines of (in pseudocode):

```
subprocess.call("ping", "-q -c 3");
```

---

### Post by nanotube on 2007-10-26
> **basic0 said:**
> That's what it looks like to me too. Admittedly, I don't know a whole lot about Python, but I think subprocess.call() wants the first argument to be the command and the second to be all of the arguments. It's looking for a command called "/bin/ping -q -c 3", which of course, doesn't exist. I think it should be more along the lines of (in pseudocode):

```
subprocess.call("ping", "-q -c 3");
```

i'd even say
```
subprocess.call(["ping","google.com","-c 3"])
```
(separate each arg into a different list item)

---

