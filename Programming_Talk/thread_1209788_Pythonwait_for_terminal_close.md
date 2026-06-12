---
title: "Python:wait for terminal close"
date: 2009-07-10
forum: Programming Talk
---

### Post by alkatron on 2009-07-10
Suppose a bash script like this
```

#!/bin/bash
echo "Hello what's your name?"
read name
echo $name

```

Called mytest.sh

If I want to call it in a python script I use something like this

```

#!/usr/bin/env python
import subprocess
return_code = subprocess.call("gnome-terminal --command='./mytest.sh'", shell=True)
if return_code == 0:
    print "success"
else:
    print "failed"

```

BUT if I insert this code in a loop

```
#!/usr/bin/env python
import subprocess
a=[1,2,3,4,5]
for x in a:
   return_code = subprocess.call("gnome-terminal --command='./mytest.sh'", shell=True)
   if return_code == 0:
       print "success"
   else:
       print "failed"
```

It does not wait the first terminal close before open the second e so on...
it open 5 terminal with mytest.sh running

I wold like to wait a terminal close before opening the next...is it possible?

Thanks to all

---

### Post by master_kernel on 2009-07-10
You can try Popen, Popen.returncode and Popen.communicate(), all in the subprocess module.

[http://docs.python.org/library/subprocess.html#popen-objects](http://docs.python.org/library/subprocess.html#popen-objects)

**Edit:**

I was bored, so I did it for you. The problem with the method you requested is that you are capturing the return code for gnome-terminal, not the process gnome-terminal called. You could probably edit myTest.sh to kill gnome-terminal if it runs into an error.

*myTest.sh*
[PHP]#!/bin/bash

echo -n "Hello what's your name? "
read name
echo $name
read
exit 0
[/PHP]

*1209788.py*
[PHP]#!/usr/bin/env python

import subprocess
a=[1,2,3,4,5]
for x in a:
   pid = subprocess.Popen("gnome-terminal" + " --command='./myTest.sh'", shell=True)
   pid.communicate()
   if pid.returncode == 0:
       print "success" # not python3 format
   else:
       print "failed" # not python3 format[/PHP]

---

### Post by alkatron on 2009-07-11
Nothing change, same problem, BUT.....

I tried this code
```

import subprocess
a=[1,2,3,4,5]
for x in a:
   pid = subprocess.Popen("gnome-terminal" + " --command='./myTest.sh'", shell=True)
   rtnm=pid.wait()
   if rtnm == 0:
       print "success" # not python3 format
   else:
       print "failed" # not python3 format  
```

and misterious thing :p, using it by eclipse + debug everything is ok while if i launch it on the terminal, the same problem rise again......

why

Thanks

---

### Post by lavinog on 2009-07-11
Why not use os.system?

---

### Post by alkatron on 2009-07-11
Because here
[http://docs.python.org/library/subprocess.html?highlight=subprocess#module-subprocess]("http://docs.python.org/library/subprocess.html?highlight=subprocess#module-subprocess")

they say it's obsolete....:?:

---

### Post by lavinog on 2009-07-11
I can't get bash to wait for gnome-terminal either.
the pid given doesn't exist once the terminal is displayed.
xterm seems to work though

Update: If I open an xterm terminal then execute gnome-terminal, xterm will wait for gnome-terminal to exit. If I try and do it with a gnome-terminal already open it wont wait.
The same thing happens with other programs started from the terminal: If I run gedit& then execute gedit again, it will give me a prompt because the process was already in the background.
This explains why eclipse was working, but launching from a terminal wasn't. If you were to launch it from nautilus or alt-f2 with no terminal open it should work.

---

### Post by alkatron on 2009-07-12
Thanks a lot for the explanation

Alkatron

---

### Post by master_kernel on 2009-07-12
I guess the only reason it worked for me was because I executed it from tilda and geany.

---

### Post by dgovaerts on 2010-07-08
If you want to wait for the terminal to close you should use the --disable-factory option. By default gnome-terminal reuses an already running gnome-terminal process and ask it to simply open a new window. --disable-factory disables that feature and starts a new process anyway. The full command should thus read:
```

gnome-terminal --disable-factory --command='./myTest.sh'

```

---

