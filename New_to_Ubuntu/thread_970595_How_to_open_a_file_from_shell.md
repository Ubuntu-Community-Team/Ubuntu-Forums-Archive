---
title: "How to open a file from shell?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-11-04
Hi everyone, I'm pretty new in Ubuntu. I just don't know how to open those files in a certain directory from shell. for example, I have some pdf files in a folder called Document. I use "cd" to get in the directory. Then what command I should type in shell to have the pdf file open in Adobe reader?

Thanks,

---

### Post by EdThaSlayer on 2008-11-04
All you have to do is type the name of the program you're going to use.
For ex: if you have KDE-> KPDF, then all you have to do is type in the terminal
> kpdf filename and it will open that file for you.

---

### Post by aktiwers on 2008-11-04
Type the command you use to open the program and then the file name. Like I open txt files in the program  gedit, I type:
```
gedit textfile.txt
```

---

### Post by taurus on 2008-11-04
But if you are using Gnome, then try

```
evince filename.pdf
```

---

### Post by Keith Hedger on 2008-11-05
To open a file in the default application use:```
xdg-open /path/to/file
```
You dont have to know what the default app is as this command will look it up itself

---

### Post by tagabukid on 2008-11-05
> **Keith Hedger said:**
> To open a file in the default application use:```
xdg-open /path/to/file
```
You dont have to know what the default app is as this command will look it up itself

thanks for that! it is a very useful command. although i have to admit i looked up 'man xdg-open' first. once again, thanks!

---

### Post by Keith Hedger on 2008-11-06
Thanks for your thanks! You did exactly right to look the command up first as even the most experienced linux users can make a typo which could be disastrous if you dont know what the command does.

---

### Post by billgoldberg on 2008-11-06
> **Keith Hedger said:**
> To open a file in the default application use:```
xdg-open /path/to/file
```
You dont have to know what the default app is as this command will look it up itself

Thanks for that, it will come in handy.

*(btw, a spelling error in your sig, it's kernel, not kernal)*

---

### Post by Keith Hedger on 2008-11-06
OMG it's been two years and nobody has spotted that before! Just goes to prove that nobody takes any notice of sigs:(:(

---

