---
title: "[C++] File Read Woes"
date: 2008-09-28
forum: Programming Talk
---

### Post by azan00 on 2008-09-28
Hello, I am currently loading a text file (python code specifically) into a string. However it seems to be reading it incorrectly as the python interpreter complains of a syntax error when I execute the code.

I am currently reading the file character by character using the following code...
```

while(file.get(c))
{
   buffer += c;
}

```

When I display the buffer the file seems to be stored correctly, however if I change the code to be the following...
```

while(file.get(c))
{
   if(c!='\n')
      buffer += c;
}

```

One would expect the data to all be displayed on one line, and it is... however random bits of the file are cut off or simply missing. I have no idea what could be causing this. I also attempted other methods such as getline(file, buffer); but that also produced odd results.

This is a simple text file, if necessary I can post it. If anyone can offer any insight I would greatly appreciate it!

---

### Post by Mindzai on 2008-09-28
Silly question maybe but there's no chance this file could have non-unix line endings? Just a stab in the dark from a non-C programmer!

---

### Post by azan00 on 2008-09-28
Hi, thanks for the reply. I'm not sure, but the file was made in gedit... if that makes a difference.

---

### Post by dwhitney67 on 2008-09-28
> **Mindzai said:**
> Silly question maybe but there's no chance this file could have non-unix line endings? Just a stab in the dark from a non-C programmer!
+1

I just wrote a similar program to that specified in the OP, and had it parse a gedited text-file, character by character, disregarding the newline character.  Everything worked as expected.

To the OP - see if you system has the "dos2unix" command, and if so, take your Python text-file and run it through the filter:
```
dos2unix file.py
```

P.S.  Parsing a file, character by character, seems (and is) awfully inefficient.  Read the file a line at a time, or in larger blocks (e.g. 1024 bytes at a time).

---

### Post by azan00 on 2008-09-28
That fixed it, thanks for the help everyone!

---

