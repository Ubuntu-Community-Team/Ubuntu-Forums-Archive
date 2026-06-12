---
title: "[SOLVED] Problem with Eclipse, denied permission"
date: 2008-09-02
forum: Programming Talk
---

### Post by echelonIV on 2008-09-02
Hey everyone, I just had this problem with Eclipse, whenever I try to run a program (new projects, old ones work fine), I always get this this error:

```
java.io.IOException: Permission denied occurred generating launch configuration XML.
```

I am also getting this error periodically:

```
Could not save master table.
```

I started having these problems after running the command 

```
gksudo eclipse
```

so I could update Eclipse (via Software updates in the help menu).

Is there any easy way to fix this at all?  Even after reinstalling via Synaptic I'm still getting the same errors.

---

### Post by jespdj on 2008-09-03
If you've run Eclipse as root once, it might have written configuration files with owner root instead of your own username, and if you then run Eclipse under your own account later, you don't have permission to write those files.

Try deleting the Eclipse configuration files in your home directory; they are in /home/username/.eclipse

---

### Post by echelonIV on 2008-09-03
Thanks, that solved my problem. 
:)

---

### Post by cas118 on 2009-05-25
Sorry to bring an old topic back to life.

I had a similar problem, but it was the files in the eclipse download that were the problem.

Changing to the directory and running
```
sudo chmod -R john:john . 
```
did the trick.

---

