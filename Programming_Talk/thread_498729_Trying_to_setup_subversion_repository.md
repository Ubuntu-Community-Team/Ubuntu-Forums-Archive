---
title: "Trying to setup subversion repository"
date: 2007-07-11
forum: Programming Talk
---

### Post by l_b on 2007-07-11
Hi all,

I'm trying to setup a subversion repository. But I keep getting errors. These are the steps I take:
```
leon@basil:~$ cd ~
leon@basil:~$ mkdir svn
leon@basil:~$ svnadmin create ~/svn/huisrekening
leon@basil:~$ mkdir /tmp/svn
leon@basil:~$ mkdir /tmp/svn/tags
leon@basil:~$ mkdir /tmp/svn/branches
leon@basil:~$ mkdir /tmp/svn/trunk
leon@basil:~$ svn import -m "Initial import" huisrekening file:///tmp/svn/
svn: Unable to open an ra_local session to URL
svn: Unable to open repository 'file:///tmp/svn'
```

Does anyone has an idea?
This also does't work:
```
leon@basil:~$ cd svn/
leon@basil:~/svn$ svn mkdir huisrekening/branches
svn: 'huisrekening' is not a working copy
svn: Can't open file 'huisrekening/.svn/entries': No such file or directory
```

---

### Post by raja on 2007-07-11
May be a bit off topic, but have you thought of trying esvn ? I have found that very easy to use and intuitive.

---

### Post by DougB1958 on 2007-07-11
You've created a _repository_ in ~/svn/huisrekening; the skeletal working copy you want to import is in /tmp/svn. So I think the command you want is something like
```
svn import -m "Initial import" file:~/svn/huisrekening /tmp/svn
```
But I'll bet subversion won't like my "file:~" syntax (which I'm somewhat making up, I left most of my subversion expertise at the office :)). It might work better if you spell out the whole pathname, e.g., something like
```
svn import -m "Initial import" file://home/yourname/svn/huisrekening /tmp/svn
```
Hope this helps.

---

### Post by l_b on 2007-07-12
Doesn't work. This is the output:
```
leon@basil:~$ svn import -m "Initial import" file://home/yourname/svn/huisrekening /tmp/svn
svn: Invalid URL '/tmp/svn'
```

Maybe I'll try esvn. But I want to set it up the "hard way". So I can learn more about it.

---

### Post by l_b on 2007-07-12
Pfff....

This seems to work:
```
leon@basil:~$ svnadmin create svn/huisrekening --fs-type fsfs
leon@basil:~$ svn import /tmp/svn file:///home/leon/svn/huisrekening/ -m "Dit is een test"
```

Maybe it didn't dig the ~ ?

---

### Post by DougB1958 on 2007-07-15
> **l_b said:**
> Pfff....

This seems to work:
```
leon@basil:~$ svnadmin create svn/huisrekening --fs-type fsfs
leon@basil:~$ svn import /tmp/svn file:///home/leon/svn/huisrekening/ -m "Dit is een test"
```

Maybe it didn't dig the ~ ?

In this one that works, you put the directory you were importing and the repository you were importing to in the right order -- which I apparently very carefully got wrong. My apologies, and glad you figured it out for yourself (like I said in my first post, I left my Subversion expertise at the office -- evidently more so than I realized :)).

---

