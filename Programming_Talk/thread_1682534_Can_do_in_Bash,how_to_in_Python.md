---
title: "Can do in Bash,how to in Python"
date: 2011-02-06
forum: Programming Talk
---

### Post by nipunreddevil on 2011-02-06
There's a small piece of code i need to modify LCD brightness and i've managed to get it done by sudo -su
followed by

echo -n 100 > /proc/acpi/video/VGA/LCD/brightness

on terminal.
However i wish to do the same using a python script and also using Java.How can it be done,esp since i gotta require root permissions for this

---

### Post by hakermania on 2011-02-06
As, in my opinion, this is not such an important file (for security e.g.), I think you can change its permissions to simple user
```
sudo chown $USERNAME:$USERNAME /proc/acpi/video/VGA/LCD/brightness
```
After this, you'll probably don't need root privileges to write to this file...

---

### Post by nipunreddevil on 2011-02-06
For now what i've been able to do is ```

echo -n 100 > /proc/acpi/video/VGA/LCD/brightness
```

using the following
```
import subprocess,os
subprocess.call(["sudo ./try.sh"],shell=True)
```

where contents of try.sh are:
```
#!/bin/bash
echo -n 10 > /proc/acpi/video/VGA/LCD/brightness
```

But this only seems a temporary solution.
I tried it to extend it like:
```
import subprocess,os
#subprocess.call(["sudo ./try.sh"],shell=True)

subprocess.call([" sudo echo -n 100 > /proc/acpi/video/VGA/LCD/brightness"],shell=True)
```
But this ain't working
```
/bin/sh:cannot create..../brightness:Permission denied
```

---

### Post by nipunreddevil on 2011-02-06
> **hakermania said:**
> As, in my opinion, this is not such an important file (for security e.g.), I think you can change its permissions to simple user
```
sudo chown $USERNAME:$USERNAME /proc/acpi/video/VGA/LCD/brightness
```
After this, you'll probably don't need root privileges to write to this file...

Thanks seems to work.But would be interested to get it working without changing permissions.But for now the purpose is solved.Thanks again

---

### Post by hakermania on 2011-02-06
> **nipunreddevil said:**
> Thanks seems to work.But would be interested to get it working without changing permissions.But for now the purpose is solved.Thanks again
Well, if you could write to any file that you're not permitted to do so, then Ubuntu wouldn't be so safe. So, the only way to write to a file you're not permitted to do so, is to change the file's permissions AFAIK.

---

### Post by mcduck on 2011-02-06
> **hakermania said:**
> Well, if you could write to any file that you're not permitted to do so, then Ubuntu wouldn't be so safe. So, the only way to write to a file you're not permitted to do so, is to change the file's permissions AFAIK.

Well, there's also the option of adding your user the permissions to execute *that single script* without requiring a password.

No need to change the file's permissions, so things would work in the normal way for any other user than the one you specifically give such privilege in /etc/sudoers.

Sudo is much more than just a simple command to execute things as root. :)

---

### Post by MadCow108 on 2011-02-06
> **nipunreddevil said:**
> 
subprocess.call([" sudo echo -n 100 > /proc/acpi/video/VGA/LCD/brightness"],shell=True)[/CODE]
But this ain't working
```
/bin/sh:cannot create..../brightness:Permission denied
```

this executes echo with root privileges. What you want is writing to the file with root. This can be done e.g. by tee:
```

echo -n 100 | sudo tee /proc/acpi/video/VGA/LCD/brightness

```

and you can also do it without shell=True (which is safer in certain situations as explained in the documentation):
```

e = subprocess.Popen(["echo", "test"], stdout=subprocess.PIPE)
subprocess.Popen(["tee", "test.txt"], stdin=e.stdout)

```

---

### Post by DaithiF on 2011-02-06
just curious ... if you're going to do it using python, why not actually do it using python, rather than using python to call your original script/command.

```
f = open('/proc/etc/blah...', 'w')
f.write(100)
f.close()

```or similar?

---

