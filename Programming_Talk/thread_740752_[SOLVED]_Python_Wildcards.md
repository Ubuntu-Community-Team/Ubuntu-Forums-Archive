---
title: "[SOLVED] Python Wildcards"
date: 2008-03-31
forum: Programming Talk
---

### Post by sekinto on 2008-03-31
I'm trying to run a loop while a variable is not a txt file.

I've tried:
while path != *".txt":
while path != "*.txt":
while path != * + ".txt":
while path != (* + ".txt"):
while path != *.txt:

They all either don't work or return errors. Is there something really easy that I'm missing here? Path is a string by the way.

---

### Post by LaRoza on 2008-03-31
> **sekinto said:**
> I'm trying to run a loop while a variable is not a txt file.

I've tried:
while path != *".txt":
while path != "*.txt":
while path != * + ".txt":
while path != (* + ".txt"):
while path != *.txt:

They all either don't work or return errors. Is there something really easy that I'm missing here? Path is a string by the way.

```

>>> x = "file.txt"
>>> x.endswith(".txt")
True

```

---

### Post by sekinto on 2008-03-31
Thank you!

It worked:
> while path.endswith(".txt") == 0:

---

### Post by pmasiar on 2008-03-31
[php]while path.endswith(".txt") == 0: #Meh! It looks like C!
while not path.endswith(".txt") # now this looks nicer - I can read that :-)
[/php]

---

### Post by erginemr on 2008-03-31
Sure Python is full of surprises! I also admire its sheer power and ease of use. It will take over the world soon, given an easy-to-use graphical RAD tool.

---

### Post by LaRoza on 2008-03-31
> **erginemr said:**
> Sure Python is full of surprises! I also admire its sheer power and ease of use. It will take over the world soon, given an easy-to-use graphical RAD tool.

Glade?

---

### Post by erginemr on 2008-03-31
> **LaRoza said:**
> Glade?

Well, I have attempted to use Glade but its way of positioning widgets was way over my head. Besides, as far as I know, you need to keep track of the code and graphical components separately. I will give it another go when I find the courage. There is also PyGTK.. Without them, you are stuck to memorizing Tkinter widgets and commands, such as config(),pack(), place(), etc. I am open to your suggestions...

What I have in mind is a complete RAD tool that integrates and handles both graphics and code, similar to the divine Delphi RAD tool. The closest one to that is Boa Constructor, but it is not ready for prime time, yet.

---

