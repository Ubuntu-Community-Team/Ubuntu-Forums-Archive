---
title: "scripting/.bat files help."
date: 2012-09-15
forum: Programming Talk
---

### Post by notsocomputerguy12 on 2012-09-15
I'm new to Ubuntu. when I had windows as my primary operating system I used to make small text based games using .bat files. how do I do the same thing with ubuntu and is it even possible?

all help is greatly appreciated.[-o<

---

### Post by mastablasta on 2012-09-15
have a look at the free ebook at linuxcommand.org

scripts are easy to do in Linux.

---

### Post by notsocomputerguy12 on 2012-09-15
thanks, I tried following the instructions and did every thing like it said, i keep getting an error saying no such directory exists when i try and run the file

---

### Post by Habitual on 2012-09-15
[CommandLineResources]("https://help.ubuntu.com/community/CommandLineResources") is the Mother Lode

---

### Post by kaytrance on 2012-09-15
> **notsocomputerguy12 said:**
> thanks, I tried following the instructions and did every thing like it said, i keep getting an error saying no such directory exists when i try and run the file
post the command you are using here, we'll see.

---

### Post by Bucky Ball on 2012-09-15
*Thread moved to **Programming Talk***

---

### Post by Some Penguin on 2012-09-15
> **notsocomputerguy12 said:**
> thanks, I tried following the instructions and did every thing like it said, i keep getting an error saying no such directory exists when i try and run the file

You probably need read up on shells and the PATH environmental variable.

For anything complicated, I'd personally recommend learning something like Python or Perl rather than one of the interactive shells such as bash or csh, because the former are substantially more fit for purpose and also have large repositories of useful code (CPAN is ridiculously useful, notably).

---

### Post by ofnuts on 2012-09-16
> **notsocomputerguy12 said:**
> thanks, I tried following the instructions and did every thing like it said, i keep getting an error saying no such directory exists when i try and run the fileIn Unix, 

[LIST]
[*]files are not executable by default
[*]the "executables path" does include the current directory
[/LIST]
So you have to:

[LIST]
[*]mark the script as executable
[/LIST]
```

chmod +x ./the_script

```

[LIST]
[*]start it by explicitly specifying the directory
[/LIST]
```

./the_script

```

---

