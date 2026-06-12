---
title: "[Python] Allowing users to script within script"
date: 2011-05-16
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-16
How can I allow my users to write a script within a python script? So if I'm running a script all of the sudden the script will give the interpreter and then when I enter three blank lines into the interpreter, the script will continue running?

Until answer is found temp solution will be to raw input into text file and run from os.system

---

### Post by eltommo on 2011-05-17
You have to go deeper.

But seriously, if you want to bring up the python shell during execution, you can use ```
os.system("python")
```
I don't know about 3 lines to exit though.
They could just press ctrl + d if that's acceptable

---

### Post by ki4jgt on 2011-05-17
> **eltommo said:**
> You have to go deeper.

But seriously, if you want to bring up the python shell during execution, you can use ```
os.system("python")
```
I don't know about 3 lines to exit though.
They could just press ctrl + d if that's acceptable

I've seen it done before (Forgot what website I was on) they actually went into the python prompt, and then brought it back out, into the script. I don't know exactly what the condition was though, that's why I said 3 blank lines. But here is what I'm trying to do. [http://ubuntuforums.org/showthread.php?t=1760558](http://ubuntuforums.org/showthread.php?t=1760558)

---

### Post by eltommo on 2011-05-17
but if you type os.system("python") with no arguments supplied to python, it will enter the python interactive prompt in-script. To exit, you can type exit() or quit() or hold down ctrl + d and that will bring you to the main script

---

### Post by ki4jgt on 2011-05-17
True, but it doesn't give me the ability to close under certain conditions, say the user enters an infinite loop. . . If I could pass exceptions to the command, I could bring it back out, b/c the user wouldn't be able to. Currently the way I have it, it does what you're suggesting, (Except for instant error reporting) but I'm looking for a way to no kill my program when the user messes up (Which they will.)

---

### Post by eltommo on 2011-05-18
hmmm, perhaps you could look into the subprocess module.
this is something that will allow a user to kill the interpreter without killing your script if thats what you want. All they need to do is press ctrl + c to terminate the python shell.
```

import subprocess, signal


print "Started Script"
proc = None


# handler for signals. Don't care about value of the arguments.
def handler(*args):
    try:
        proc.kill()
    except Exception:
        pass

# set the handler for ctrl+c
# this is so that pressing ctrl+c wont kill this script
signal.signal(signal.SIGINT, handler)

proc = subprocess.Popen("python")
proc.wait()

print "\nHere"

```something else that, if you could do, would be really cool is alter the actual python interpreter itself to integrate it with what you are doing, but I'm not sure how you would go about doing that.

---

### Post by ki4jgt on 2011-05-18
found it. . . pty module. I just don't know how to pass exceptions to it.

---

### Post by nvteighen on 2011-05-18
I'd write my own interpreter, following good ol' Read-Eval-Print Loop (REPL) principle invented by the Lisp gods :P

1. Get input.
2. Evaluate the input and store the output somewhere.
3. Print the output.
4. Loop to 1.

The key step is number 2. You can use eval() or exec() if you plan to just call the Python interpreter... eval() is safer because it doesn't allow importing stuff and creates an isolated evaluation environment. On the contrary, exec() actually allows you to modify whatever is being executed by the interpreter, your program for instance. You could also add restraints or new stuff by checking for keywords before passing the input to eval/exec(). I actually recommend you to do it so you have some control over what can be done. Also, eval/exec() pass the exceptions to the caller.

Just making the whole Python interpreter available for the user via your program is bad, IMO. Some call this the "Underlying Platform Syndrome", where you make available the whole platform that underlies your program just because you want give total power to the user; that's impractical because your program is your program, and not Python, because you want it to be a specific solution for a specific problem. Scripting, IMO, should be limited to modify behaivor of the program, but never making your program just be an alternative way for calling Python. (I've got some personal experience on this... PycTacToe had this problem in the past :()

---

### Post by cgroza on 2011-05-18
Why don't you use the input(). The last time I checked, it was evaluating it's input as a python expression. Alternatively, you can use eval() on the input stream.

All you have to do is print the results back.

---

### Post by ki4jgt on 2011-05-18
> **cgroza said:**
> Why don't you use the input(). The last time I checked, it was evaluating it's input as a python expression. Alternatively, you can use eval() on the input stream.

All you have to do is print the results back.

This is what I'm currently doing.

---

### Post by cgroza on 2011-05-18
Your posts are telling me this:


> Until answer is found temp solution will be to raw input into text file and run from os.system

---

### Post by ki4jgt on 2011-05-18
> **cgroza said:**
> Your posts are telling me this:

Sorry, I've updated the script a little.

---

