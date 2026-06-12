---
title: "[SOLVED] /opt folder"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by waterrr on 2008-07-31
I'm not able to copy files onto the /opt folder on my Ubuntu, I get the error

```
Error while copying to "/opt"
You do not have permission to write to this folder.
```

I am logged on as the admin...what's wrong here?

---

### Post by tuxxy on 2008-07-31
run this command in terminal and then try to move the files again using nautilus

```
gksudo nautilus
```

---

### Post by bodhi.zazen on 2008-07-31
Ubuntu uses sudo ...

So in a terminal :

```
sudo cp ....
```Or i you prefer a gui 

```
gksu nautilus
```

As an administrator you can use sudo ;)

[uhelp]community/RootSudo[/uhelp]

---

### Post by sisco311 on 2008-07-31
you need root privileges to copy files in the /opt directory.

open your file manager  as root
press Alt+F2 and run:
```
gksu nautilus
```or use the cp command from a terminal
```
sudo cp *path/to/file */opt
```[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

EDIT: I'm so slow :)

---

### Post by waterrr on 2008-07-31
the path to the file is located on a ip addy, how would i use "cp" for that?

---

### Post by waterrr on 2008-07-31
nvm i just used nautilus!

---

### Post by waterrr on 2008-07-31
forgot to say thanks!

---

