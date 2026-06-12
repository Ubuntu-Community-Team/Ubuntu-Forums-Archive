---
title: "Monodevelop Runtime 2.0 doesn't complie"
date: 2007-01-28
forum: Programming Talk
---

### Post by moeFinley on 2007-01-28
I using Edgy and Monodevelop 0.12

I have an application that compiles and runs fine using runtime version 1.1 but as soon as I switch to 2.0 it would create an .exe

There are no errors when it compiles but when I try and run it I get```
cannot open assembly /home/moefinley/Projects/Network Test v1/Network Test v1/Network Test v1.exe
``` and there is not .exe in the output folder?

I just starting to learn Mono so I'm sure I might be doing something wrong but I don't know what.  Could any help shed any light?  Thanks

---

### Post by blanky on 2007-01-28
Are you trying to compile it on purpose? Did you already know there's a debian package for monodevelop?

sudo apt-get install monodevelop

:) Also, you don't learn 'mono', mono is the 'framework', or 'platform', if you will. Instead, you learn a language like C#, VB.Net, Boo, or any other [CLI Compliant]("http://www.dotnetpowered.com/languages.aspx") language. :)

**EDIT**: Oh, woops! Misread your post. So you can't get the application to run? Try to run it with the command line **mono** program. i.e. **mono myprogram.exe**. Could you rephrase your question? I don't really understand what you're saying.

---

### Post by mostwanted on 2007-01-28
> **blanky said:**
> Are you trying to compile it on purpose? Did you already know there's a debian package for monodevelop?


He's not trying to compile monodevelop, he's trying to compile something *using* monodevelop.

---

### Post by moeFinley on 2007-01-28
Thanks for the replies, yes I'm just trying to compile a program that I have written in Monodevelop - not to compile Monodevelop itself.

> Try to run it with the command line mono program. i.e. mono myprogram.exe
I have not .exe to run.  It's didn't make one.

I did read in another post that you can compile outside of Monodevelop just at the command line.  It didn't explain how though, does anyone know?

Thanks

---

### Post by st4rdr1ft3r on 2007-01-28
```
mcs --help (.NET 1.1)
gmcs --help (.NET 2.0)
```

---

### Post by moeFinley on 2007-01-28
Super fast response! Thanks.

It seems I don't have gmcs
```
gmcs --help
bash: gmcs: command not found

```but I do have mcs.

I guess I need to install something?

---

### Post by st4rdr1ft3r on 2007-01-28
Yup, give:
```
sudo apt-get install mono-gmcs
```
a try. see if that helps.

---

### Post by moeFinley on 2007-01-28
Wahoo! That work.  Thanks man, perfect end to my weekend :D

---

### Post by st4rdr1ft3r on 2007-01-28
my pleasure, glad to help.

---

### Post by sillv0r on 2007-12-12
Saweet.  Thanks.  This helped me too.

---

