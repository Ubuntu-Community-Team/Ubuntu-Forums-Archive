---
title: "a.out"
date: 2006-08-18
forum: Programming Talk
---

### Post by Jonas_Henricsson on 2006-08-18
I wrote a program in emacs and then compiled it using g++. The result is a.out. According to the instructions for a lab I'm doing, I'm supposed to be able to run the a.out file by typing a.out. I only get the answer "Command not found". 

What do I need to do? Thank you for any help!

/Jonas

---

### Post by gerbman on 2006-08-18
The command would be "./a.out", not "a.out"...the system needs to know where to find your program ("./" tells it to look in the current directory).

---

### Post by waldschm on 2006-08-18
First, make sure you are in the correct directory with the executable a.out by doing an ls -l. If you are, check the permissions that showed up to make sure you are allowed to execute the file. If you only see r's or w's, you need to make the file executable by typing:
chmod +x a.out

Then type 
./a.out

Give this a try and see if it works.

---

### Post by Jonas_Henricsson on 2006-08-18
Yes!

./a.out works excellently! May the sun shine over you and may beautiful women massage your feet!

/Jonas

---

### Post by gerbman on 2006-08-18
> **Jonas_Henricsson said:**
> May the sun shine over you and may beautiful women massage your feet!Haha. It's cloudy and I am in an engineering building (hint hint, no women). Thanks anyway :)

---

### Post by IYY on 2006-08-19
The reason that you have to specify the directory (./) is that the current directory is not a part of your path by default. To add it:

```
PATH=$PATH:.
```

---

### Post by gerbman on 2006-08-19
> **IYY said:**
> The reason that you have to specify the directory (./) is that the current directory is not a part of your path by default. To add it:

```
PATH=$PATH:.
```Good point, but you might want to put "PATH=$PATH:." in your ~/.bashrc file unless you want to do it every time you open a terminal.

---

### Post by wmcbrine on 2006-08-19
Bear in mind that "." is left out of the default path for a reason. However, it's probably not nearly as much of a security risk at the end of the path as it is at the beginning (where it is, implicitly, in Windows).

---

### Post by gerbman on 2006-08-19
> **wmcbrine said:**
> Bear in mind that "." is left out of the default path for a reason. However, it's probably not nearly as much of a security risk at the end of the path as it is at the beginning (where it is, implicitly, in Windows).Good point - hadn't thought about the security implications.

---

