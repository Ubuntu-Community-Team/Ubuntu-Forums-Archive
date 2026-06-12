---
title: "How to write something on a text file on a certain line?"
date: 2010-12-17
forum: Programming Talk
---

### Post by leon.vitanos on 2010-12-17
This is how i write something on text file:

```
{system("echo \"Hello\" > /home/$USER/.config/Wallch/Checks/language_selection");
```


But how to write something on a certain line without changing the others?
For example how can i write "Hello" on the third line of my text file without changing the first line... ?

---

### Post by roccivic on 2010-12-17
You could append:
```
{system("echo \"Hello\" **[COLOR="Red"]>>[/COLOR]** /home/$USER/.config/Wallch/Checks/language_selection");
```

Otherwise, if you want your text _inserted_ at a specific line, you'll have to read in the whole file, then add your changes and finally overwrite the original file.

---

### Post by leon.vitanos on 2010-12-17
> **roccivic said:**
> You could append:
```
{system("echo \"Hello\" **[COLOR="Red"]>>[/COLOR]** /home/$USER/.config/Wallch/Checks/language_selection");
```

Otherwise, if you want your text _inserted_ at a specific line, you'll have to read in the whole file, then add your changes and finally overwrite the original file.
The exactly thing someone had answered me.. but this will not go to the certain line that i want but on a new line... Again: For example how can i write "Hello" on the third line of my text file without changing the first line... ? This is what i want... Any ideas?

---

### Post by hakermania on 2010-12-17
```
alex@MaD-pc:~$ cat lol
1
2
Hello
Hello
3
4

alex@MaD-pc:~$ sed -i "5i\Hello" lol
alex@MaD-pc:~$ cat lol
1
2
Hello
Hello
Hello
3
4

alex@MaD-pc:~$
```

---

### Post by Some Penguin on 2010-12-17
Files don't have lines; they have bytes.  Therefore, you have to rewrite the file (or implement a custom filesystem which is meant for edits like this).

---

### Post by leon.vitanos on 2010-12-17
thanx it works :)

---

