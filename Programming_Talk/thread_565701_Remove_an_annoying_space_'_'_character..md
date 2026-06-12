---
title: "Remove an annoying space ' ' character."
date: 2007-10-02
forum: Programming Talk
---

### Post by weblordpepe on 2007-10-02
Hello guys.
I am trying to output a few strings into one file on the same line. I want to wrap part of it in quotes, because it is running a wine program, and windows needs the filenames in quotes.

Anyway my problem is that I have space character that I can't get rid of.. Its driving me nuts. I can't work out how to get rid of it.

Here's where I'm at. The user would run **./awsomescript.sh filename.jpg**.  That means the first parameter of my script is a file. Eg: **filename.jpg**
I am using **echo** to output strings to the file **~/.wine/iprog** in hopes of building up a script file to run.

At this point in the script, the output file has > wine /usr/local/IrfanView/i_view32.exe
It is nececary to put the filepath inside quote marks. Although This is where I'm running into trouble:

```
# Output Windows version of the file path to the same text file.
echo -n "\\042" >> ~/.wine/iprog
winepath -w $1  >> ~/.wine/iprog
echo -n "\\042" >> ~/.wine/iprog

less ~/.wine/iprog | tr 'h:' 'H:' | tr 'z:' 'Z:' | tr '\n' ' '  # >> ~/.wine/iprog2


```
The **\\042** provides the quote marks and **-n** stops **echo** from putting a carrage-return on the end of the line. Also, the **tr** is there to help babysit Irfanview with upper/lowercase drive letters.
This outputs the following:
> wine /usr/local/IrfanView/i_view32.exe  "H:\filename.jpg "

Can anyone help me get rid of the space directly after filename.jpg and before the quotation mark? :confused:

---

### Post by ynnhoj on 2007-10-02
just a guess: is the line..
```
winepath -w $1  >> ~/.wine/iprog
```
..putting a newline character at the end?  if so, you're translating '\n' to a space (' '), instead of simply removing it.  maybe..
```
less ~/.wine/iprog | tr 'h:' 'H:' | tr 'z:' 'Z:' | **tr -d '\n'**  # >> ~/.wine/iprog2
```
..would be better?

---

### Post by weblordpepe on 2007-10-03
Hmm it appears I may have narrowed down the problem. But I still can't fix it. The problem is when I direct the output of winepath.

If the filename or filepath includes a backslash  \ to indicate a space, then it retards up the output file.
For example:

The filepath  **/home/pepe/Desktop/Pie\ space\ PEI.gif ** can goof up the code. When that filepath is the first argument ($1) and passed through the code: ```
winepath -w $1 >> ~/.wine/iprog
``` it ends up putting this in the file:
> wine /usr/local/IrfanView/i_view32.exe h:\Desktop\Pie
h:\space
h:\PEI.gif

Maybe I will try ensuring there's no spaces in the path -before- it goes to winepath hmm.

---

### Post by weblordpepe on 2007-10-03
Ok the problem is. When **/home/pepe/Desktop/Pie\ space\ PEI.gif** is passed as an arguement and becomes $1, the contents of $1 are actually **/home/pepe/Desktop/Pie space PEI.gif**.

This means that **Pie**, **space** and **PEI** are all put on seperate lines when passed to winepath within the script.

Does anyone know who I can keep $1 with the backslashes intact?

---

### Post by mssever on 2007-10-03
> **weblordpepe said:**
> Ok the problem is. When **/home/pepe/Desktop/Pie\ space\ PEI.gif** is passed as an arguement and becomes $1, the contents of $1 are actually **/home/pepe/Desktop/Pie space PEI.gif**.

This means that **Pie**, **space** and **PEI** are all put on seperate lines when passed to winepath within the script.

Does anyone know who I can keep $1 with the backslashes intact?

Surround $1 with double quotes. This is why, in bash, you should alwaus surround variables with double quotes unless you know for certain that they will never contain spaces or the like. Bash is really aggressive in expanding variables.
```
winepath -w "$1" >> ~/.wine/iprog
```

---

### Post by weblordpepe on 2007-10-06
Zomg yay!!!
Thanks heaps. That works perfectly.

---

