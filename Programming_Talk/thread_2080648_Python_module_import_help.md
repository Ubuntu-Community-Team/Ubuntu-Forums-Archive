---
title: "Python module import help?"
date: 2012-11-04
forum: Programming Talk
---

### Post by leereef on 2012-11-04
I have a folder on my desktop called game. in it it contains python files.  I want to make a program that imports the files into the program and executes them, how would I do this?

---

### Post by Tony Flury on 2012-11-05
Several ways of doing this :
[LIST=1]
[*]Copy the contents of your desktop folder into the folder containing your application. Pros - very simple. Cons - you get duplicates.
[*]Create a symbolic link of youir desktop folder into your application folder. Pros - reasonably simple and quick. No duplication. Cons - you have to do this for ever programe you want to write.
[*]Add the folder on your desktop into the PYTHONPATH environment variable. Pros - the recommended way of including extra modules in the search. Cons - you will need to edit your .profile or .bashrc to make the permanent change to your environment variable. Only applies to your user account.
[*]Copy the folder into one of the folders already included in PYTHONPATH. Pros - available for everyone on the system. Cons - Could contaminate other installed modules.
[/LIST]
I would go for option 3 - unless you need every users to have access to the modules - in which case go with option 4 - if you have a proper DEB installation package for the modules.

If you go with option 3 - don't leave them on your desktop - too easy to loose them with a tidy up.

---

### Post by leereef on 2012-11-08
Thank you sooooooo much!

---

