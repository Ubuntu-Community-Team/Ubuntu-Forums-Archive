---
title: "Need Help with GUI programming"
date: 2009-04-29
forum: Programming Talk
---

### Post by captainobvious62 on 2009-04-29
I am working on a college project, and I am at a loss. I need to design a GUI for a program, but I have no idea how to do so. What is the most painless way to go about doing this? I have very little prior experience ---help!!

---

### Post by simeon87 on 2009-04-29
What language are you writing the program in?

---

### Post by captainobvious62 on 2009-04-29
Python - and i need to somehow roll it into an installer

---

### Post by grepgav on 2009-04-29
I don't have too much experience with python GUI programming, but I did brief work with pygtk using Glade to design the interface and it seemed like a pretty nice system.

I would do some Googling about those and design your interface with Glade to get the file describing the UI first, then start working in python to do the backend and event listener code.

---

### Post by stevescripts on 2009-04-29
You have tkinter available for Python, and also EasyGUI (a wrapper around tkinter) - about the simplest I can think of.

Steve

---

### Post by Nevon on 2009-04-29
They didn't teach you that before giving you the assignment?

---

### Post by Carl Hamlin on 2009-04-29
> **Nevon said:**
> They didn't teach you that before giving you the assignment?

Seriously - either you didn't read the materials, or this is some kind of clown college. I've never heard of a programming class where they just throw you in and say 'come up with something' without giving you some idea of how to go about it.

---

### Post by samjh on 2009-04-29
> **captainobvious62 said:**
> I am working on a college project, and I am at a loss. I need to design a GUI for a program, but I have no idea how to do so. What is the most painless way to go about doing this? I have very little prior experience ---help!!

What platform?  Linux, BSD, Solaris, Mac, Windows?

On Linux or other Unix-like systems, PyGTK with Glade is probably the easiest.

On Windows, just stick to Python's built-in Tkinter module.  PyGTK programs are extremely difficult to distribute on Windows in a clean, professional installation package.  I tried it for days and developed an allergic reaction to it. ;)

Google is your friend. :)

---

