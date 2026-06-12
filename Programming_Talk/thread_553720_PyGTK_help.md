---
title: "PyGTK help"
date: 2007-09-18
forum: Programming Talk
---

### Post by jimma on 2007-09-18
Hi All

I'm relatively new to Ubuntu and Python. I want to write a graphical program using glade, pyGTK and python that displays to the user via the textview area what is happening to the program. 

What I dont know how to do is to get the program to update, which is to get the latest data from a file to update the textview for the user. How do I do that?

Thanks

---

### Post by Wybiral on 2007-09-18
I would spawn a thread that reads the file and inserts text into the TextView. Have you messed with using Pythons threads yet?

Which part are you curious about, starting the process or writing to the textview?

---

### Post by pmasiar on 2007-09-18
If you are new into python, start with command-line text-only programs until you get firmer grip on language. Wiki in my sig will geive you links to trainig task for beginners. I recommend PythonChallenge.

---

### Post by jimma on 2007-09-18
thanks I managed to solve the problem.

---

