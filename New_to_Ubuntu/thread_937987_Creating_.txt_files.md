---
title: "Creating .txt files"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-04
How can I create a .txt file of my .conf files?

---

### Post by homemadejam on 2008-10-04
Can't you just save the file as filename.txt instead of filename.conf ?

Jam

---

### Post by OutOfReach on 2008-10-04
You can open the .conf file and select 'Save As' and save it as a .txt.

---

### Post by JasenGroves on 2008-10-04
If you want to cheat, wine comes with notepad... you can cut and paste the contents of your .conf file into a .txt file there.

---

### Post by Konstabel on 2008-10-04
I am in a terminal (ssh connection) and viewing the .conf files with nano. There is no save as option that I can find. Is there some other way that I can save it as a .txt?

---

### Post by bodhi.zazen on 2008-10-04
Linux does not treat files the same way as Windows. .config files are already text files and changing the tailing extension does not change things.

[http://linux.die.net/man/1/file](http://linux.die.net/man/1/file)

> bodhi@Entropy:~$ file snort-2.8.2.2.tar.gz
[color=blue]snort-2.8.2.2.tar.gz: gzip compressed data, from Unix, last modified: Fri Jul 18 14:54:40 2008, max compression[/color]

bodhi@Entropy:~$ cp snort-2.8.2.2.tar.gz snort.jpg

bodhi@Entropy:~$ file snort.jpg
[color=green]snort.jpg: gzip compressed data, from Unix, last modified: Fri Jul 18 14:54:40 2008, max compression[/color]

---

### Post by Joeb454 on 2008-10-04
As bodhi.zazen stated - you can open your .conf files with any text editor on Linux :)

---

### Post by homemadejam on 2008-10-04
You could always try something like this then:
cp /home/bob/file.conf /home/bob/conf.txt

Jam

---

### Post by iansane on 2008-10-04
Just did this and it worked

If there's some reason you need to make a txt file of it.

copy contents of sample.conf to sample.txt from terminal

```

cat sample.conf > sample.txt

```

or

```

cp sample.conf sample.txt

```

both worked from terminal.

Like they said both are treated as text but that's two ways to do it from terminal.

Then edit either one with nano

---

### Post by Konstabel on 2008-10-04
Jam, thanks the cp thing worked

---

### Post by mumuwenwu on 2008-10-04
for those of you using vi, when you are opening sample.conf,

:w sample.txt (save the whole file)

:1,10 w sample.txt (save 1-10 lines)

:1,10 w! sample.txt (save 1-10 lines, overwrite sample.txt if existed)

---

