---
title: "Close a program from command line"
date: 2016-03-29
forum: New to Ubuntu
---

### Post by gino4 on 2016-03-29
Hello I want to know if there is a way to close/kill a program from the Terminal but without force the closing of it, is possible to kill a program as if I am closing it with the "X" in the corner of the window?

---

### Post by slickymaster on 2016-03-29
Hi gino4, welcome to the forums.

In a terminal window (Ctrl+Alt+T) find the process ID of the application you want to kill```
ps -aux | grep application_name 
```That will show the process id of the application. You can then stop that application```
kill -9 processID_number
```

---

### Post by QDR06VV9 on 2016-03-29
> **slickymaster said:**
> Hi gino4, welcome to the forums.

In a terminal window (Ctrl+Alt+T) find the process ID of the application you want to kill```
ps -aux | grep application_name 
```That will show the process id of the application. You can then stop that application```
kill -9 processID_number
```
+1
And as you asked as if closing it with The X in the corner.
```
killall application_name
``` 

IE: nautilus...**"killall nautlius"**

---

### Post by gino4 on 2016-03-29
Hi, thank you for your answer but if I close a program with the command you told me I'm actually forcing the closure of it, mostly using the signal SIGKILL (-9) that you told me, I've tried to kill a program also with SIGTERM, SIGQUIT and SIGINT but with everyone the closure of the program is "forced", am I wrong?

---

### Post by Impavidus on 2016-03-29
**kill** can kill a process by sending it a signal. There are many signals available. Use```
kill -l
```to get a list. **kill -9** sends the KILL signal (SIGKILL), forcing immediate termination of a process. By default **kill** sends the TERMINATE signal (SIGTERM), which is a friendly request to close the process. If the process has a handler for SIGTERM, it can do whatever it wants. In a well-behaving program this means saving some files and closing. This is more or less equivalent to clicking the X, but not the same. Internally it works rather differently and sending signals also works with processes that don't open a window, but the effect may be exactly the same.

Edit: Didn't see your post #4. Gave the answer more or less. If the process has no handler for SIGTERM, it must either ignore it or terminate immediately, the same result as with SIGKILL.

---

### Post by gino4 on 2016-03-29
So the "kill" command isn't the equivalent to click the "X" so is there a command that is the equivalent?

---

### Post by sudodus on 2016-03-29
Probably not exactly equivalent. I have not heard of anything better than what impavidus explained.

Please tell us what you intend to do - why you want to close 'any' program from a terminal window. If you tell us, we might be able to find a good solution for task behind the task you are asking us to solve.

---

### Post by jim_deadlock on 2016-03-30
From the terminal you can do

```
xkill
```

which will allow you to click on the window that you want to kill. Very useful when the program freezes.

---

