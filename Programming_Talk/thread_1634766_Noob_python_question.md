---
title: "Noob python question"
date: 2010-12-01
forum: Programming Talk
---

### Post by travmanx on 2010-12-01
I am trying to get the current user on the machine which I know I can get from os.system() but when I execute the command

print 'Welcome %s' % (os.system('echo $USER'))

I get this in return

travis
Welcome 0
Script terminated.


-----

Why is the user being printed up top and a leading 0?

Thanks

---

### Post by TheWeakSleep on 2010-12-01
When a command is completed succesfully, os.system() returns a 0

That means that the 'value' of os.system('echo $USER') is the 0, not the output of the command itself.

The 'travis' is just the output of the command.

try it for yourself! :) 

```
 os.system('echo $USER') == 0
```and it should print out 'True'

..unfortunately i don't know how to help other than that. If my explanation was wrong in anyway I'm sure someone will correct me.

EDIT: try os.getlogin() it should fix your problem :)

---

### Post by travmanx on 2010-12-01
> **TheWeakSleep said:**
> When a command is completed succesfully, os.system() returns a 0

That means that the 'value' of os.system('echo $USER') is the 0, not the output of the command itself.

The 'travis' is just the output of the command.

try it for yourself! :) 

```
 os.system('echo $USER') == 0
```

and it should print out 'True'

..unfortunately i don't know how to help other than that. If my explanation was wrong in anyway I'm sure someone will correct me.

Thank you :) I get it. It was a stupid mistake of mine in the beginning.

---

### Post by TheWeakSleep on 2010-12-01
There are no stupid mistakes while you're learning :)

if you didnt see my edit, there is also from the getpass module

'import getpass'

you could use getpass.getuser() and that should be portable across *nix and windows. At least I think :p

---

### Post by DaithiF on 2010-12-01
in python environment variables are stored in the os.environ dictionary.

so you can do:
```

import os
user = os.environ['USER']

```

---

### Post by TheWeakSleep on 2010-12-01
Wow how did I miss that! :o good to know!

---

### Post by Cheesehead on 2010-12-02
> os.system(command)
Execute the command (a string) in a subshell. This is implemented by calling the Standard C function system(), and has the same limitations. Changes to sys.stdin, etc. are not reflected in the environment of the executed command.

**On Unix, the return value is the exit status** of the process encoded in the format specified for wait(). Note that POSIX does not specify the meaning of the return value of the C system() function, so the return value of the Python function is system-dependent. Source: [http://docs.python.org/library/os.html]("http://docs.python.org/library/os.html")



There are sveral ways to get the current username: [http://stackoverflow.com/questions/842059/is-there-a-portable-way-to-get-the-current-username-in-python]("http://stackoverflow.com/questions/842059/is-there-a-portable-way-to-get-the-current-username-in-python")

---

