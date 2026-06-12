---
title: "move and delete files"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-07-04
I have some files that have the "lock" icon beside them.

I have tried sudo chmod etc but have no idea how to access these files so that I can move or delete them.

---

### Post by unutbu on 2008-07-04
Can you post a screenshot of the files? 
Showing the location (path) would help a lot too.

---

### Post by sayakb on 2008-07-04
```
sudo rm filename
sudo chown username:group filename
```

Try either of these. The first one deletes it. The second one changes ownership to the specified user.

---

### Post by saskatchewan on 2008-07-04
Here are the readouts that I got

allan@allan-laptop:~$ sudo chown allan:group Work Search 2008
[sudo] password for allan: 
chown: invalid group: `allan:group'
allan@allan-laptop:~$ sudo chown allan Work Search 2008
chown: cannot access `Work': No such file or directory
chown: cannot access `Search': No such file or directory
chown: cannot access `2008': No such file or directory
allan@allan-laptop:~$ 


the location is /home/allan.Documents

---

### Post by Vivaldi Gloria on 2008-07-04
```
chown: invalid group: `allan:group'
```

Use "allan:allan". Your group name is also allan.

```
allan@allan-laptop:~$ sudo chown allan Work Search 2008
```

Use quotation marks (") around filenames which contain spaces.

---

### Post by Vivaldi Gloria on 2008-07-04
Better, press Alt+F2 and start

```
gksudo nautilus
```

Now find and right click on the file and choose properties. Now you can change ownership and rights from their tabs.

---

### Post by saskatchewan on 2008-07-04
This is the response that I received.

allan@allan-laptop:~$ sudo chown allan Work Search 2008
chown: cannot access `Work': No such file or directory
chown: cannot access `Search': No such file or directory
chown: cannot access `2008': No such file or directory
allan@allan-laptop:~$

---

### Post by Vivaldi Gloria on 2008-07-04
As I told, use " for names with spaces:

```
allan@allan-laptop:~$ sudo chown allan "Work Search 2008"
```

or

```
allan@allan-laptop:~$ sudo chown allan Work\ Search\ 2008
```

---

### Post by saskatchewan on 2008-07-04
Yep, that did it
Thanks everybody!!

---

### Post by Vivaldi Gloria on 2008-07-04
> **saskatchewan said:**
> Yep, that did it
Thanks everybody!!

Have fun.

---

### Post by zzatz on 2008-07-04
As already mentioned, you need to quote file names with spaces. You asked it to remove three files: one named Work, one named Search, and one named 2008. If you are trying remove a single file, you have choices:

"Work Search 2008" is one file name. Expressions, like $HOME, are expanded inside double quotes.

'Work Search 2008' is one file name. Single quotes preserve the literal text, preventing expansion.

Or you can escape individual characters (such as space) by preceding them with a backslash. Example: Work\ Search\ 2008

File names can contain any character except slash. But many characters have special meaning to the shell, so you need to tell the shell to ignore (escape) the special meaning and use the literal characters. Graphical interfaces don't usually go through the shell, and don't need to do this. But the command line is powerful, and useful to learn. For example: 'for i in *JPG;do mv -vi "$i" "${i/.JPG/.jpg}";done' renames all files ending in JPG to jpg.

---

