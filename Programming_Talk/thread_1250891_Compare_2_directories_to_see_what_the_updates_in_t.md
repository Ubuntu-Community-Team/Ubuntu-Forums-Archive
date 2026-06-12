---
title: "Compare 2 directories to see what the updates in the program are?"
date: 2009-08-27
forum: Programming Talk
---

### Post by edwardtilbury on 2009-08-27
Sorry if that was unclear, here's what I need to do.. 

I have a php program 1.0 in a directory, and in another directory I have version 1.1

I want to know what the difference in code is, so is there a program that compares each directory and highlights the differences? 

I'm not sure what to search for exactly, or if there's even a name for that type of program.

Thanks :)

---

### Post by DaithiF on 2009-08-27
Hi,
if you are happy to use command line then:
```
diff directory1 directory2
```
or if you want a graphical program, you could try meld
```
sudo apt-get install meld

```

---

### Post by edwardtilbury on 2009-08-27
Thanks for the tip, I did some more digging and found the name of what I'm looking for, diff programs... I tried all 3 gnome ones in 9.04 add/remove, yes Meld is the best... Does netbeans have a diff feature for directories too?

Thanks

---

