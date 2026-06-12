---
title: "is there a c:program files equivalent in linux?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by m1ck on 2008-08-21
i'm probably thinking in a windows mentality but say for instance when i install a program where is it stored. :confused:

---

### Post by LowSky on 2008-08-21
/usr is where the file will load from

/home/.*program's_name* is where your personal settings are stored.

---

### Post by Too Late on 2008-08-21
Many programs are installed in /usr/bin/. To see where a specific program is stored, go to terminal and type "which program", eg:
```
which nautilus
```

---

### Post by m1ck on 2008-08-21
thanks for that.

the which command is really handy

---

### Post by Titan8990 on 2008-08-21
Also, whereis command will give you a bit more information than which.

Example:

jordan@einstein:~$ whereis nautilus
nautilus: /usr/bin/nautilus /usr/lib/nautilus /usr/share/nautilus /usr/share/man/man1/nautilus.1.gz

jordan@einstein:~$ which nautilus
/usr/bin/nautilus

---

### Post by Too Late on 2008-08-21
In addition, to see every possible "Program Files folder", type:
```
echo $PATH
```
When the program is installed in one of those folders, you don't have to type the full path of that program when launching it.

---

### Post by jerome1232 on 2008-08-21
linux the *which* hunter

```
whereis which
which: /bin/which /usr/bin/which /usr/share/man/man1/which.1.gz

```

I don't know why but I thought it was funny

---

### Post by Titan8990 on 2008-08-21
They can also tell about themselves:

jordan@einstein:~$ which which
/usr/bin/which

jordan@einstein:~$ whereis whereis
whereis: /usr/bin/whereis /usr/share/man/man1/whereis.1.gz


I have too much time on my hands at work....

---

### Post by m1ck on 2008-08-21
> **jerome1232 said:**
> linux the *which* hunter


I don't know why but I thought it was funny

hehe sounds like the title of a good horror film :D

---

### Post by Too Late on 2008-08-21
[offtopic]
My favorite is ```
man man
```[/offtopic]

---

### Post by philinux on 2008-08-21
This pic gives a good explanation of where files are stored.

---

### Post by WRDN on 2008-08-21
```
apt-get moo
```

:)

---

### Post by jerome1232 on 2008-08-21
> **WRDN said:**
> ```
apt-get moo
```

:)

```
aptitude -v moo
```
keep making it more verbose

---

### Post by mali2297 on 2008-08-21
If it's a package in Synaptic, then there is an option to view a list of the files that will be installed. 

You can also view file lists at [packages.ubuntu.com](packages.ubuntu.com). For example, here is the [file list for gedit]("http://packages.ubuntu.com/hardy/i386/gedit/filelist").

---

### Post by hufferd on 2008-08-21
> **Titan8990 said:**
> Also, whereis command will give you a bit more information than which.

Example:

jordan@einstein:~$ whereis nautilus
nautilus: /usr/bin/nautilus /usr/lib/nautilus /usr/share/nautilus /usr/share/man/man1/nautilus.1.gz

jordan@einstein:~$ which nautilus
/usr/bin/nautilus

Thanks for this info :)

---

### Post by zenithdave on 2008-08-21
> **philinux said:**
> This pic gives a good explanation of where files are stored.

My search is over, thanks for that :)

roots are usually at the bottom!

---

