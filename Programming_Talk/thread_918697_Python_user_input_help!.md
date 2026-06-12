---
title: "Python user input help!"
date: 2008-09-13
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-13
I got a python app that defines tons of functions. How can I do so it gets user input (in console) and executes
the command as a normal python command, just like in python interactive console, but while my program is running?
And my program has a main loop.

---

### Post by y-lee on 2008-09-13
maybe something like :

```
a = raw_input("Command ")
# test a for validity first
valid = test_input(a)
if valid:
    exec(a)
```

---

### Post by nebu on 2008-09-13
if u want to execute a string inside python shell....
> exec(STRING_HERE)

if u want to execute a particular unix command in the cwd....
> os.system(STRING_HERE)

---

### Post by crazyfuturamanoob on 2008-09-13
But how can I use raw_input & console inside main loop?? I got multiple windows that need the mainloop!

---

### Post by y-lee on 2008-09-13
> But how can I use raw_input & console inside main loop?? I got multiple windows that need the mainloop!

How are you implementing multiple windows? Some sample code would help. Are you using GUIs or something else?

---

### Post by crazyfuturamanoob on 2008-09-13
> **y-lee said:**
> How are you implementing multiple windows? Some sample code would help. Are you using GUIs or something else?
Yes... The windows & other stuff need to be updated each loop time. But raw_input stops the loop.

E: I use pygame + subprocess to handle the windows. The main application has a main loop,
while the child windows have an update function that updates them. All the update functions
of all child windows are executed in the main loop each loop time.

---

### Post by days_of_ruin on 2008-09-13
> **crazyfuturamanoob said:**
> Yes... The windows & other stuff need to be updated each loop time. But raw_input stops the loop.

E: I use pygame + subprocess to handle the windows. The main application has a main loop,
while the child windows have an update function that updates them. All the update functions
of all child windows are executed in the main loop each loop time.

You could put raw_input in another thread.

---

### Post by crazyfuturamanoob on 2008-09-14
> **days_of_ruin said:**
> You could put raw_input in another thread.

Thanks, but how can I have one thread to be terminal itself?

---

