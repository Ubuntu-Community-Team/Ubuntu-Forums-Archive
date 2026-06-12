---
title: "Cutecom"
date: 2009-10-27
forum: Programming Talk
---

### Post by LiaGalanodel on 2009-10-27
Hi!

I have to use cutecom and It's work but when I want transfer a file .bz2 or .gz. It doesn't work, I use zmodem for the transfer.

The transfer start but even I wait few minutes it's not finished.

Can you help me?

Thank you

[[IMG]http://img29.imageshack.us/img29/1905/screenshotvq.th.png[/IMG]](http://img29.imageshack.us/i/screenshotvq.png/)

---

### Post by LiaGalanodel on 2009-10-27
Now I have a matter when i want to execute in cutecom with this code:

```
./filename
```

He tell me: 

```
-bash: ./hello: No such file or directory
```

I don't understand why. I compile the program with arm-linux-gcc because I execute in arrm9.

But it doesn't work!

---

### Post by LiaGalanodel on 2009-10-28
I don't understand why he telle me : no such fill or directory, I have the right name.

---

### Post by Zugzwang on 2009-10-28
I don't know the program but in your screenshot, you have a lot of Window-style backslashes instead of "/". Maybe these cause your problems?

If this doesn't help, please start by explaining that "Cutecom" actually does, how you apply it and post some copy&pasted error messages. Normally, bash error messages do not start with "-", so I assume that yours isn't.

---

### Post by LiaGalanodel on 2009-10-29
That's ok!

Thank you very much for your answer.

*CuteCom* is a graphical serial terminal, like minicom (or Hyperterminal on Windows I use it because I want to execute program for arm but to execute it I must created an interface between the PC and the target arm. So to entered in the target arm I need a graphical terminal.

---

### Post by Zugzwang on 2009-10-29
So you did theck that the following holds, right?:
[LIST=1]
[*]The first was transferred correctly (i.e. it is displayed by "ls" and the size matches).
[*]After transferring the file, it has executable permissions.
[*]It is in the current directory (on the remote side) when trying to execute it
[*]you really started it with "./filename" where filename is exactly the name of the file with the same capitalisation.
[/LIST]

---

