---
title: "Weird python bug"
date: 2008-02-27
forum: Programming Talk
---

### Post by JaggedOne on 2008-02-27
I am just starting out coding python and I keep getting this one error with the input command that confounds me. 

Here is my very simple boring program:
```
a = input("Input a number: ")
print a
```

And here is the output:
```
Traceback (most recent call last):
  File "/home/sam/Python Programs/begin.py", line 1, in <module>
    a = input("Input a number: ")
TypeError: 'str' object is not callable
```

Raw_input works just fine btw.

Whiskey Tango Foxtrot?

---

### Post by LaRoza on 2008-02-27
input doesn't do what you think it is doing...It isn't a bug.

Use raw_input not input. Read the following article:

[http://linuxgazette.net/issue83/evans.html](http://linuxgazette.net/issue83/evans.html)

---

### Post by JaggedOne on 2008-02-27
When I said a bug I meant a bug in my software. And I am pretty sure I  know the difference between input and raw_input. 

Both should prompt me to enter something at the very least. Input is giving me that error even before it prompts me to enter any data. I would expect an error if input gave me a prompt and I fed it a non valid python expression.

---

### Post by LaRoza on 2008-02-27
> **JaggedOne said:**
> When I said a bug I meant a bug in my software. And I am pretty sure I  know the difference between input and raw_input. 

Both should prompt me to enter something at the very least. Input is giving me that error even before it prompts me to enter any data. I would expect an error if input gave me a prompt and I fed it a non valid python expression.

How are you running this?

---

### Post by JaggedOne on 2008-02-27
I am using IDLE, opening a new window, writing out the whole program, saving it and running it in the python shell.

Edit: I just tested it running the command alone int he shell. Same error.

---

### Post by LaRoza on 2008-02-27
> **JaggedOne said:**
> I am using IDLE, opening a new window, writing out the whole program, saving it and running it in the python shell.

Edit: I just tested it running the command alone int he shell. Same error.

I am not sure what is going on, try this:

* Open a terminal
* type "python"
* enter the code line by line
* Press enter

Does it still do it?

---

### Post by JaggedOne on 2008-02-27
Same thing in the terminal. :confused:
```
>>> a=input("gimme a number")
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object is not callable

```

However this did work. Didn't give me the prompt I told it to though... :confused:
```
>>> input=("gimme a number")
>>> 5
5

```

---

### Post by Siph0n on 2008-02-27
>>> a=input("gimme a number")
gimme a number7


Don't know what u got going on... but it worked for me.... Sorry... did u try raw_input like LaRoza suggested?

---

### Post by pmasiar on 2008-02-27
> **JaggedOne said:**
> 
```

    a = input("Input a number: ")
TypeError: 'str' object is not callable
```


Looks like somehow you got builtin function input redefined as string variable. Are you sure you don't have any other code, just these two lines?

---

### Post by WW on 2008-02-27
> **pmasiar said:**
> Looks like somehow you got builtin function input redefined as string variable.
I think pmasiar has it right; this line given earlier by JaggedOne redefines input:
```
>>> input=("gimme a number")
```

EDIT: This sequence recreates the error message:
```
>>> ans = input("Enter a number: ")   # This works
Enter a number: 100
>>> input = ("gimme a number ")       # This redefines input
>>> input 
'gimme a number '
>>> ans = input("Enter a number: ")   # Now this does not work, because input is now a string
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
TypeError: 'str' object is not callable
>>> 

```

---

