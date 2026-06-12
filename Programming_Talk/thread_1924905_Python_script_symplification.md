---
title: "Python script symplification"
date: 2012-02-13
forum: Programming Talk
---

### Post by conradin on 2012-02-13
Hi all, I want a script o list all the user-names on my system.
I saw a script that has that feature on line, and tore it down, But I'm stuck on how to simplify it any more. 
Heres where Im at:
```
#!/usr/bin/python
import pwd
import operator

# Load all of the user data, sorted by username
all_user_data = pwd.getpwall()
userz = sorted((u 
    for u in all_user_data 
    if not u.pw_name.startswith('_')),
    key=operator.attrgetter('pw_name'))

# Print the data
for u in userz:
    print (u.pw_name)
```


and here is where this script came from:
[http://www.doughellmann.com/PyMOTW/pwd/](http://www.doughellmann.com/PyMOTW/pwd/)


Any insight would be much appreciated.

---

### Post by MadCow108 on 2012-02-13
in what way do you want to simplify it more?
its almost at the minimal line number, you could still move the pwd.getpwall() into the generator and replace the attrgetter with a lambda to save the operator import.
if you really only want the user name you can use sorted((u.pw_name for u in pwd.getall()))
but thats more compactification than simplification, simplification should also make the code easier to read and understand.

---

### Post by conradin on 2012-02-14
Thanks mad cow, that was actually helpful. I thought about it, and said to hack with the sorting. so now Im looking at 4 lines.
 ```
#!/usr/bin/python
import pwd
# Load all of the user data, sorted by username
for u in pwd.getpwall():
	print (u.pw_name)
```

---

### Post by conradin on 2012-02-15
Because my boss will kill me if I put zero error checking in my scripts, this is my simplified improved version.
```
#!/usr/bin/python
import pwd
try:
	# Load all of the user data, sorted by username
	for u in pwd.getpwall():
		print (u.pw_name)

except:
	print("Something went terribly wrong.")
```

---

### Post by StephenF on 2012-02-15
$ awk -F: '{print $1}' /etc/passwd

Quick and dirty.

---

