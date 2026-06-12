---
title: "Set output of os.system('command') to variable?"
date: 2011-06-07
forum: Programming Talk
---

### Post by CoffeeRain on 2011-06-07
I'm trying to set the output of os.system('look ' + var1) to another variable, but when I try to do it, it just executes the command and then sets the variable to '0'. Do you know how to make this work, or is there a similar command in python? Thanks.

---

### Post by MadCow108 on 2011-06-07
system returns the exit code of the child process not the output.
use subprocess Popen:
```
p = subprocess.Popen(["echo", "bla"], stdout=subprocess.PIPE, stderr=subprocess.PIPE);
stdout, stderr = p.communicate()
```

or if you have python 2.7 you can use the convinience function check_output:
```
stdout = subprocess.check_output(["echo", "bla"])
```

---

### Post by nvteighen on 2011-06-07
os.system() is the worst option to interface with another program, exactly because of the behaivor you're experiencing: it runs in a new shell and all it returns is the exit code.

The best option is always to look after a library that does what you want; instead of relying on a different program, a library gives your program the ability to something on its own. If none is available, the popen is the second-best, as it allows you to create a connection to the program, but this is only possible when the target program is designed to work with pipes.

But be aware that excessive use of os.system() could be a signal that what you want is a shell script.

---

### Post by CoffeeRain on 2011-06-07
Thanks!

---

