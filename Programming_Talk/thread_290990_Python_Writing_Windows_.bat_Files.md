---
title: "Python Writing Windows .bat Files"
date: 2006-11-01
forum: Programming Talk
---

### Post by gerowen on 2006-11-01
I've got a little bit of experience in writing python programs that take information from the user and write a Linux bash script to implement the information collected.  I recently tried to write a program to write a .bat file in Windows and where the "\" would be it inserts a space instead of the \ and the letter following it.  For example if I wanted to write a file to delete a text file named temp.txt located in C:\, here is what I would write:
```

import commands
infile=open("delfile.bat", "w")#Opens the file
infile.write("del C:\temp.txt")#Writes the desired contents to the file
infile.close()#Closes the file
commands.getstatusoutput(delfile.bat)#Executes the file

```
That bat file executes because I see the DOS window flash for a second like normal, but the file remains in C and the contents of the .bat file would be:
```

del C:	emp.txt

```
I think this is because python regards backslashes as symbols, like how \n will insert a new line, does somebody know how I could get it to keep the \ and actually write it into the file?

---

### Post by gerowen on 2006-11-01
Nevermind, two backslashes does the trick.

---

### Post by deepwave on 2006-11-01
Hmm... how about \\?

Python treats a \ as an escape character.  Two \\ together should escape and write one \.

Also I would use Python's sys and os modules and run system commands using the API, instead of creating a batch file and executing it.

---

### Post by Hendrin on 2006-11-01
I was too slow on the draw. ;)

---

### Post by gerowen on 2006-11-02
> **deepwave said:**
> Hmm... how about \\?

Python treats a \ as an escape character.  Two \\ together should escape and write one \.

Also I would use Python's sys and os modules and run system commands using the API, instead of creating a batch file and executing it.

Yeah I'm new-ish to python, I figured it out, thank you for your help.

---

