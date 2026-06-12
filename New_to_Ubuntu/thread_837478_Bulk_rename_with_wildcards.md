---
title: "Bulk rename with wildcards"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by kwacka on 2008-06-22
Hi, 

I've got about half a dozen directories with sub-directories - all numbered, .

e.g. 
/1233_textfiles
/1233_textfiles/1234_somefile.txt
/1233_textfiles/1235_anotherfile.txt

and I want to get rid of the numbers, to rename them:

/textfiles
/textfiles/somefile.txt
/textfiles/anotherfile.txt

preferably without renaming them one-by-one.

I've tried searching but not found a practical answer.

Any suggestions, please?

---

### Post by uclalinux on 2008-06-22
There are a bunch of different ways to do this but I feel the easiest way is with a gui, I think krename is the best to install it goto a terminal and type
```
sudo aptitude install krename 
```
it will allow you to do a bunch of different things.

Just play around with it for abit, its not to hard to figure out. 

just to help out, you can drag and drop folders into it when it ask you to add files, you don't have to use a file path.

---

### Post by kwacka on 2008-06-25
many thanks for the tip, I'll be trying it out over the next few days.

---

### Post by mali2297 on 2008-06-25
There is also a useful bulk renamer in Thunar.

---

### Post by Inxsible on 2008-06-25
If you love the command line, 'find' is an extremely powerful command. Try the man pages to see what it can do.

---

