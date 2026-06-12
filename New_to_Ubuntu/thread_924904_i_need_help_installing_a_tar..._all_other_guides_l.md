---
title: "i need help installing a tar... all other guides leave steps out!"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by S6I6X on 2008-09-20
well im new to ubuntu but i have a lot of experience with stuff on the pc but i found that it doesnt really help. i want to learn how to install some tarballs but every forum i find the people are talking about something specific that probably works for that program but wont work for mine or maybe im reading it wrong, im trying to install Floola on my ubuntu. i can get it on xp no problem but im trying to start doing things in linux more. the file is floola-linux.tar.gz

---

### Post by acidsolution on 2008-09-20
```

tar -xvf floola-linux.tar.gz

```

it extracts to folder floola-linux 
now if this is your source file than 
find for some file like install.sh or configure.sh
and run them 

1   ./configure.sh

2     make 

3     make install

---

### Post by quinnten83 on 2008-09-20
well,if you give the link to the file, perhaps we can help further
WTH is floola, i keep hearing about it...

---

### Post by zvacet on 2008-09-20
[Here]("http://209.85.175.104/search?q=cache:vINsmw2aJ3EJ:monkeyblog.org/UBUNTU/installing/+http://monkeyblog.org/ubuntu/installing/&hl=en&ct=clnk&cd=1&gl=in&client=firefox-a")

---

### Post by SteveNorman on 2008-10-13
From here

[http://www.floola.com/modules/wiwimod/index.php?page=docs_install](http://www.floola.com/modules/wiwimod/index.php?page=docs_install)

```
Installation, Linux

It's suggested to use Windows formatted iPods as there are problems mounting Mac formatted (HFS+) iPods.

Make sure your iPod is mounted with read AND write access.

To enable playback you'll need either gstreamer or lib xine to be installed. If both are installed gstreamer will be used.
Floola relies on libstdc++5. To install it (under Ubuntu) type sudo apt-get install libstdc++5 via terminal.
To start Floola, just double click on application icon or from console type ./Floola
```


so download it, change into the directory it is downloaded to (for me I downloaded to the desktop) and extract. Then get libstdc++5. After that, plug in your ipod and open Floola by typing ./Floola

```

$ cd Desktop
$ tar -xvf Floola-linux.tar.gz
$ sudo apt-get install libstdc++5
$ ./Floola

```

after you do this you should get a configuration app asking for your ipod type.

Configure and it should then link up with your ipod.

---

### Post by jpangamarca on 2008-10-13
> **S6I6X said:**
> well im new to ubuntu but i have a lot of experience with stuff on the pc but i found that it doesnt really help. i want to learn how to install some tarballs but every forum i find the people are talking about something specific that probably works for that program but wont work for mine or maybe im reading it wrong, im trying to install Floola on my ubuntu. i can get it on xp no problem but im trying to start doing things in linux more. the file is floola-linux.tar.gz

What exactly are the error messages you are getting?

---

