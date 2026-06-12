---
title: "SyntaxError: invalid syntax"
date: 2013-01-15
forum: Programming Talk
---

### Post by xenazfire on 2013-01-15
```
#!/usr/local/bin/python
until phew.py; do
        echo "'phew.py' crashed with exit code $?. Restarting..." >&2
        sleep 1
done
```

```
 File "./phew.sh", line 2
    until phew.py; do
             ^
SyntaxError: invalid syntax
```

Hi, I need help in fixing this error. Please help. Should I place the python files in the same directory as this bash file? Currently I place this bash file in my root folder and the python files in ```
/usr/local/bin/
```

I've done
```
which python
```
and outputs
```
/usr/local/bin/python
```

---

### Post by MadCow108 on 2013-01-15
shell is not python
run your shell script from a shell, e.g. bash
```
#/bin/bash
...
```

for the until line to work phew.py must be in a directory in the PATH variable

---

### Post by xenazfire on 2013-01-15
> **MadCow108 said:**
> shell is not python
run your shell script from a shell, e.g. bash
```
#/bin/bash
...
```

for the until line to work phew.py must be in a directory in the PATH variable

**EDIT:**
Refer to post #4

---

### Post by xenazfire on 2013-01-15
**UPDATE:**
Copied the python files to
```
/usr/local/bin/
```
run
```
nohup ./phew.sh &
```
and it outputs
```
from: can't read /var/mail/random
from: can't read /var/mail/time
from: can't read /var/mail/settings
from: can't read /var/mail/rest
/usr/local/bin/phew.py: line 8: syntax error near unexpected token `('
/usr/local/bin/phew.py: line 8: `def autoScan():'
'phew.py' crashed with exit code 2. Restarting...
```

---

### Post by xenazfire on 2013-01-15
Solved!
Placed on the first line on each *.py files:
```
#!/usr/local/bin/python
```

Thanks!

---

