---
title: "Python Script Window Not Staying Open"
date: 2011-02-16
forum: Programming Talk
---

### Post by Zarkinator on 2011-02-16
Hi,

I am new to using Linux, and programming in Python. I am attempting to teach myself, but it is slow going at times. I am using a book called Python Programming for the Absolute Beginner, Third Edition by Michael Dawson.

In it, the first program is as follows:

```
# Game Over 
# Demonstrates the print function 
 
print("Game Over") 
 
input("\n\nPress the enter key to exit.")
```The purpose of the last line is to have the terminal wait for the user to press enter, so it doesn't automatically close. But it doesn't work. I saved the file as .py, made it executable, and open it; but the script doesn't stay on the screen for more than .1 seconds.

It works when I test it in IDLE, but not when I just open the file.

I have Python 3.1 installed, and am using Ubuntu 10.10.

So what is the issue?

Thanks for the help!

*Edit: After some research, I was thinking that perhaps the issue is that my default Python interpreter may be 2.6, instead of 3.1, but I don't know how to check that, or how to change it if it is.

---

### Post by MadCow108 on 2011-02-16
to do this you must place an
```
#!/usr/bin/env python
```
at the top of the script so the kernel knows what to do with it and make it executable by typing this in a terminal:
```
chmod u+x path/to/script
```

then you should be able to execute it by clicking on the file.

you can also execute it directly in a terminal without above change by typing:
```
python /path/to/script
```
in this case you also do not need the input line to keep the terminal open.

---

### Post by Zarkinator on 2011-02-16
Thanks for the quick reply!

When I open it with the
 ```
python3 /path/to/script
``` command, it works fine, and stays open. (I had to change it to python3, instead of just python, for it to work without errors.)

But adding the
 ```
#!/usr/bin/env python
``` to the top still makes it only stay open for .1 seconds. I also tried
 ```
#!/usr/bin/env python3
```which didn't help. I ran the command to make it executable before I tried it.

So, is this program just not meant to be able to be run like I am attempting to, or is there some other issue still at work here? I really want to make this work if possible, as he uses the 
```
input("\n\nPress the enter key to exit.")
```
  command in most of his example programs to keep then open when executed.

Thanks again for the help!

---

### Post by Zarkinator on 2011-02-17
So, is there any way to fix this? Or is it just not meant to be?

Thanks

---

### Post by cgroza on 2011-02-17
Your code is fine, something goes wrong when double clicking the file. I am sure that that flashing window shows an error that is too fast too see. If you could see it somehow you could solve the problem.

---

### Post by forrestcupp on 2011-02-17
You have to run console programs in a console or they don't work. It's been a while for me, but it seems like when you click on a file like this, you have the options to run or run from a console. When you start getting into GUI stuff, like pyGTK, then you will be able to run it without using the console.

I think you can set in the file properties to run in a console, too. But I've been in Windows for a while, so I don't know if things are still the same.

---

### Post by Zarkinator on 2011-02-17
Thank you both for the help. That is what I will do then.

---

