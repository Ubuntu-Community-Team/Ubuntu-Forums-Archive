---
title: "using nano to navigate the linux file system"
date: 2013-09-07
forum: Programming Talk
---

### Post by twsLeGR on 2013-09-07
Can't seem to get to grips with nano when i want to open a file in a different directory than Home. For example, if i wanted to start up nano and open a file at the same time (the file is in my Football directory), i typed: nano /Football/filename. But all i get is nano opens as a new file? Hope someone can help this noob, please.

---

### Post by steeldriver on 2013-09-07
The leading slash says 'start from the root of the filesystem tree' - if the file is in *your* Football directory that would be

```
[COLOR=#ff0000]**/**[/COLOR]home/*yourusername*/Football/filename
```

or, for short

```
[COLOR=#ff0000]**~**[/COLOR]/Football/filename
```

---

### Post by sudodus on 2013-09-07
When in the home directory try the relative path

```
nano Football/filename
```

or from any directory the absolute path

```
nano ~/Football/filename
```

Tilde '***~***' is short for the home directory alias **/home/$USER**

---

### Post by twsLeGR on 2013-09-07
Very big thanks for the help guys

---

### Post by DarkAmbient on 2013-09-07
Could add that in Ubuntu you can see where you are located on your filesystem in the PS1 (the text prior to input is called that)

Example: (below is my PS1)

```
r@i7:~$
```

Means I am r, at computer i7, in folder ~.

```
r@i7:~/Dokument$
```

Means I am in **/home/r/Dokument**, you get the idea...

You can always type **pwd** to get full path or where you are located, and just like the guys explained above about path with nano, you use either full or relative path with **cd** to move around. 

Like **cd /home/r** takes me to **~** no matter where I am located. (or **cd ~** or just **cd** for that matter)

If I'd be in **/home/** and type **cd r** it would also take me to **~**.
**cd ..** takes you to the parent-folder, aslong as you'r not located in **/**, which is the top.

You can see what folders there are in the location you'r in using **ls**.

---

### Post by tgalati4 on 2013-09-07
You can also use dot (.) notation.  The dot means "here".

```
cd
mkdir test_directory
nano ./testdirectory/test_file.txt
```

You can also use double dot (..) notation.  Double dot means up one directory from here.

Hence:

```
cd
cd test_directory
nano ../test_directory/test_file.txt
```

I hope that sorted your football pool.

---

### Post by Tony Flury on 2013-09-07
Just to be clear in case twsLeGR or any other new user is confused - the file name shortcuts that people have mentioned in this thread : ~, .., and . are not specific to nano - they work with every command that uses file names - they are provided by the command line interpreter which you are typing into.

---

### Post by tgalati4 on 2013-09-07
Yes, but that spoils the fun of picking winners in the football pool.  And since we are talking about football, one needs to know how to *[bash]("https://help.ubuntu.com/community/Beginners/BashScripting")*.

---

