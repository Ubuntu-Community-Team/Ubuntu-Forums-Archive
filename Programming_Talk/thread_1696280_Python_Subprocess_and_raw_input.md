---
title: "Python: Subprocess and raw_input"
date: 2011-02-27
forum: Programming Talk
---

### Post by evillan on 2011-02-27
This is really just a "cosmetic" bug, but I can't really figure out how to remove it.

From my python script:
```

i = raw_input(subprocess.call("echo -n 'Name of data file? '", shell=True))

```
outputs
```
Name of data file? 0
```
Yes, with an extra 0. Where does the 0 come from and how do I remove it?

---

### Post by ssam on 2011-02-27
i think its the return value of the echo command.

why not do
```

i = raw_input('Name of data file? ')

```

---

### Post by evillan on 2011-02-27
> **ssam said:**
> i think its the return value of the echo command.

why not do
```

i = raw_input('Name of data file? ')

```

Because I have to use some commands in the terminal afterwards using the imput (sed). 
Why am I not just using bash scripting? Well, some of the python functions are missing and would be quite complicated to write in bash. Also, I have more experience with python than bash.

Anyways, is there any way to remove the return value?

---

### Post by MadCow108 on 2011-02-27
> **evillan said:**
> Because I have to use some commands in the terminal afterwards using the imput (sed). 
Why am I not just using bash scripting? Well, some of the python functions are missing and would be quite complicated to write in bash. Also, I have more experience with python than bash.

Anyways, is there any way to remove the return value?

Can you explain in more detail what you are doing?

above code looks very very wrong.
If you really need such a weird method it should be more like this (+ error checking):
```

f = subprocess.Popen(["echo", "-n", "blabla"], stdout=subprocess.PIPE)
s = subprocess.Popen(["sed", "s/b/c/"], stdin=f.stdout, stdout=subprocess.PIPE)
raw_input(s.communicate()[0])

```

---

### Post by ssam on 2011-02-27
> **evillan said:**
> Because I have to use some commands in the terminal afterwards using the imput (sed). 
Why am I not just using bash scripting? Well, some of the python functions are missing and would be quite complicated to write in bash. Also, I have more experience with python than bash.

Anyways, is there any way to remove the return value?

the return value shows because subprocess.call() returns the return value, you have give it as an argument to raw_input, and raw_input displays the argument (it is meant to be the prompt).

MadCow108, has posted how to capture output from subprocesses.

are you sure you can't use pythons string manipulation or regular expressions to do what you are using sed for?

---

### Post by lavinog on 2011-02-28
Can you post the full code.  We could give you better info that way.

Can you explain how ssam's method would not work with sed while yours would?

---

