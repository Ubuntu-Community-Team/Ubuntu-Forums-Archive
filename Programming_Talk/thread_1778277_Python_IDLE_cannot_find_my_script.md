---
title: "Python IDLE cannot find my script"
date: 2011-06-08
forum: Programming Talk
---

### Post by yltang on 2011-06-08
Ubuntu 11.04 and idle-python3.2

From the terminal, I started Python IDLE from the directory of my module (let's say the name of  the module is 'testmod.py'). Now, I can do "import testmod", however, I cannot  run the module by directly entering its name "testmod". The error message  was "NameError: name 'testmod' is not defined". It seems that IDLE cannot  find the module. Why is that and how to fix it? Thanks.

---

### Post by epicoder on 2011-06-09
As far as I know, to import a custom module, you have to save the program that imports the module in the same directory as the module. It shouldn't matter what directory you started IDLE in. If it's already saved there, you need to give us this info:

-- Name of the module
-- Name of the file that imports the module
-- Line of code that throws the error
-- Line of code that imports your module

Also, if you are trying to directly run your module as a function -
```
testmod()
```- this can't be done. You need to define a function in the module.

testmod.py
```
def function():
    print("Doing stuff...")
    # do stuff

```program-that-imports-testmod.py
```
import testmod
testmod.function()
```

---

### Post by Barrucadu on 2011-06-09
You can't run a module like that, you can however run functions that are defined within the module.

---

### Post by yltang on 2011-06-10
Thanks for the replies. To conclude, the only three ways I can run a script as a main program are listed as follows. Is that right?

1. In a terminal: enter the command "python testmod.py"
2. In IDLE: open the program file, and then choose "Run --> Run Module" (or hit F5)
3. In Gnome: double click the script file

---

