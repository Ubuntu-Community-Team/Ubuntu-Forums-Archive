---
title: "[Python] Newbie question"
date: 2008-09-24
forum: Programming Talk
---

### Post by Aphexe on 2008-09-24
```
name = raw_input("What is your UserName: ")
password = raw_input("What is your Password: ")
print "To lock your computer type lock."
command = None
input1 = None
input2 = None
while command != "lock":
    command = raw_input("What is your command: ")
while input1 != name:
    input1 = raw_input("What is your username: ")
while input2 != password:
    input2 = raw_input("What is your password: ")
print "Welcome back to your system!"

```

i get a error that says

[COLOR="Red"]Traceback (most recent call last):
  File "/home/*****/Practice.py", line 1, in <module>
    name = raw_input("What is your UserName: ")
TypeError: 'str' object is not callable[/COLOR]
What does this error mean?

---

### Post by LaRoza on 2008-09-24
Works fine for me. I copied and pasted the code and run it with no problems.

---

### Post by Aphexe on 2008-09-24
hmm could it possibly be a setting i have wrong?

---

### Post by gomputor on 2008-09-24
It's not the way I would write this script, but definitelly I can't see any error at line 1 as the error message says. I can't figure out. Do you have this error all the time? Can you post when that error came, what you did at the time?

---

### Post by Aphexe on 2008-09-24
I started a new window and ran the code again and the error didn't come up. guess it must of been a bug or something

---

### Post by pmasiar on 2008-09-24
pebkac ;-)

---

### Post by WW on 2008-09-25
You would get that error if you had previously assigned a string value to raw_input.  For example,
```

>>> raw_input = "Enter your name: "       # Oops, that's not how to use raw_input.
>>> name = raw_input("Enter your name: ") # Now this won't work.
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object is not callable
>>> 

```

---

### Post by NovaAesa on 2008-09-25
> **WW said:**
> You would get that error if you had previously assigned a string value to raw_input.
Wow, I always thought that Python was one of those "safe" languages (unlike C or C++ where it relies on the programmer not to screw up).

---

### Post by pmasiar on 2008-09-25
> **NovaAesa said:**
> Wow, I always thought that Python was one of those "safe" languages (unlike C or C++ where it relies on the programmer not to screw up).

You have it wrong: C, C++ and Java are those "safe" languages what do not trust programmer and require to explain and prove you know what you are doing, and fail to compile if they are just a little bit suspicious. Focus is on being flexible and easy to use: if you want to be safe like in C++, you have to take care of a lot of things which Python does for you for free, and does it correctly in 99% cases.

Python is language what tries hard to make programmer's life easier  and relies on common sense but trusts programmer to do right thing (and checks at runtime if something is missing).

Replacing function with a string is stupid but possible, so it is allowed (and of course blows  at runtime when you want to execute that string).

---

### Post by nvteighen on 2008-09-25
Actually, it's a feature. Why shouldn't be you be allowed to define something as "raw_input"? If I want to have a variable of that name, I should be able to have it... but understanding the consequences that will have, of course.

(Of course, Lisp goes to the extreme and let you redefine + to be - or 5 or "Hello")

---

