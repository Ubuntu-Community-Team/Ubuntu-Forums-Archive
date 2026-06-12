---
title: "any way to get a simple list of programs in repo"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by cosmoshell on 2008-10-27
is there a way to get a simple list of all programs/files in repository. like a print list of main, multiverse etc

---

### Post by NewJack on 2008-10-27
Here is the Ubuntu Package Search site:

[http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by eriqjaffe on 2008-10-27
You can also do

```
sudo apt-cahce dump >> file.txt
```

...hope you love huge text files!

---

### Post by cosmoshell on 2008-10-28
already tried [http://packages.ubuntu.com](http://packages.ubuntu.com)
just tried sudo apt-cache dump >> file.txt

im looking for a way to just get a list of all the packages in a section of the repo like just the packages in main or multiverse etc. without any other information. something like this
 
2vcard
3270-common
3dchess
4g8

I want a list going down of all packages in a givin section of a repository

---

### Post by handydan918 on 2008-10-28
> **cosmoshell said:**
> already tried [http://packages.ubuntu.com](http://packages.ubuntu.com)
just tried sudo apt-cache dump >> file.txt

im looking for a way to just get a list of all the packages in a section of the repo like just the packages in main or multiverse etc. without any other information. something like this
 
2vcard
3270-common
3dchess
4g8

I want a list going down of all packages in a givin section of a repository

I believe  the apt-cache dump would do what you want if you commented out the unwanted repos...

---

### Post by cosmoshell on 2008-10-28
> **handydan918 said:**
> I believe  the apt-cache dump would do what you want if you commented out the unwanted repos...

Is there a way to make the list look the way apt-cache pkgnames does. the other way doesnt just give me a list it give me information on the packages that i dont want. I just want a text file with a simple list

---

### Post by bodhi.zazen on 2008-10-28
> **cosmoshell said:**
> Is there a way to make the list look the way apt-cache pkgnames does. the other way doesnt just give me a list it give me information on the packages that i dont want. I just want a text file with a simple list

Pipe the output through awk or cut
[FONT=monospace]
[/FONT]sudo apt-cahce dump | awk > packages.txt

[http://www.linuxjournal.com/article/8913](http://www.linuxjournal.com/article/8913)

---

### Post by cosmoshell on 2008-10-28
> **bodhi.zazen said:**
> Pipe the output through awk or cut
[FONT=monospace]
[/FONT]sudo apt-cahce dump | awk > packages.txt

[http://www.linuxjournal.com/article/8913](http://www.linuxjournal.com/article/8913)

dident work

also tried replaceing the word cahce with cache still dident work

the file was blank

---

### Post by bodhi.zazen on 2008-10-28
LOL

You will need to add additional information in the awk command to specify which fielsd you wish to be printed.

---

