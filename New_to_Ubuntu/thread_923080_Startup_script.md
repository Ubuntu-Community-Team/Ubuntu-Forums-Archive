---
title: "Startup script"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Spardra on 2008-09-18
How exactly do you run Startup scripts? In the file it has something like this

```
#!/bin/csh -f

# Set the port number.
set port = 9000
if ( "$1" != "" ) set port="$1"

# Change to area directory.
cd ../area

# Set limits.
nohup
nice
limit stack 1024k
ulimit -Sc unlimited
if ( -e shutdown.txt ) rm -f shutdown.txt
```

How would I run the file so that Ubuntu executes that? I am using Ubuntu 8.04 Hardy

---

### Post by aloshbennett on 2008-09-18
If you want it to be run only for your user, you could add it to System -> Preferences -> Sesssions -> Startup

---

