---
title: "Compiling a bash script"
date: 2008-02-03
forum: Packaging and Compiling Programs
---

### Post by psychofish25 on 2008-02-03
I recently started experimenting with bash. I was just wondering how I could compile my script so that I could run it without typing "bash ..." in terminal. 

Thanks,
Jordan

---

### Post by Mantis86 on 2008-02-03
start your script with :
#!/bin/bash

when executing  your script type ./nameofscript from the directory the script is currently in

If you want to execute it without the ./ just place the script within the /bin directory

---

### Post by psychofish25 on 2008-02-03
when I do that it says permission denied. But I want to compile this script to an executable.

---

### Post by geraldm on 2008-02-03
In addition to what Mantis86 said:
The permissions of the script must be executable.  Use the command chmod to set the permissions.  chmod u+x myscript.sh
bash is a shell, so it is not compiled, and bash itself is the executable
and the interpreter.

Gerald

---

### Post by amingv on 2008-02-03
> **Mantis86 said:**
> start your script with :
#!/bin/bash

when executing  your script type ./nameofscript from the directory the script is currently in

If you want to execute it without the ./ just place the script within the /bin directory

Although this would work, I don't think it's advisable to copy custom programs in the /bin folder. These folders are protected for a reason and should not be used as a playground.
I would suggest to create a bin directory in the user's home folder instead.

---

### Post by Compyx on 2008-02-04
And don't forget to set the PATH environment variable accordingly.
Put this in ~/.bashrc:
```

export PATH=$PATH:$HOME/bin

```

Putting stuff in /bin just to be able to run something without providing a path is not the right way to do things. If you need a script/binary to be accessible for all users, put it in /usr/local/bin or /opt/bin and set paths in the global bash config files.

---

### Post by psychofish25 on 2008-02-04
> **Compyx said:**
> And don't forget to set the PATH environment variable accordingly.
Put this in ~/.bashrc:
```

export PATH=$PATH:$HOME/bin

```

Putting stuff in /bin just to be able to run something without providing a path is not the right way to do things. If you need a script/binary to be accessible for all users, put it in /usr/local/bin or /opt/bin and set paths in the global bash config files.
Can you explain that again please?

---

### Post by BoneSaw on 2008-02-04
> **Compyx said:**
> And don't forget to set the PATH environment variable accordingly.
Put this in ~/.bashrc:
```

export PATH=$PATH:$HOME/bin

```

Putting stuff in /bin just to be able to run something without providing a path is not the right way to do things. If you need a script/binary to be accessible for all users, put it in /usr/local/bin or /opt/bin and set paths in the global bash config files.

i think if you open up the bashrc file you can uncomment a line that will look for ~/bin and add it to the path.

---

