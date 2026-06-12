---
title: "Find / Locate"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-02-19
Hi Guys,

I've been trying to find files from the command line and am having some trouble.  The goal is to be able to type part of a file name and find that file on either of my two drives.

Background:
I have the song White Wedding in two places by two different bands.
One is in /media/Elements/MUSIC/ which is an external drive.
The other is in my Dropbox folder ~/Dropbox/

Both songs are in subdirectories.

I can find the Dropbox version of the song by using:
```
locate Wedding
/home/gg/Dropbox/Asdis/Live at the Word - Edited/12 White Wedding Edited.mp3
```

I must be using find incorrectly though because if I run:

```
find . -name 'Wedding'
find: `./.cpan/build/FreezeThaw-0.5001-Ib_x0n/t': Permission denied

```
which has nothing to do with either version of the song I'm trying to find.

Any help would be much appreciated.

---

### Post by codemaniac on 2013-02-19
you can try something like below.

```
find / -name *Wedding* -print 2> /dev/null
```

---

### Post by GrouchyGaijin on 2013-02-19
That worked thank you.
Now the trick is remembering the command.

---

### Post by codemaniac on 2013-02-20
Hi GrouchyGaijin,

You can find the below wiki page useful,

[https://help.ubuntu.com/community/find](https://help.ubuntu.com/community/find)

and also the man pages of find.

cheers!!

---

### Post by Vaphell on 2013-02-20
```
find / -name [COLOR="Red"]*Wedding*[/COLOR] -print 2> /dev/null
```

this will work incorrectly if there are objects matching the glob in current directory. Unquoted glob will expand to the list of matching objects first, then these names will be passed to find as separate arguments.

```
$ touch find1.txt find2.txt
$ find -name find*txt  [COLOR="SlateGray"]# find sees -name find1.txt find2.txt[/COLOR]
find: paths must precede expression: find2.txt
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
$ find -name 'find*txt'
./find2.txt
./find1.txt
```

in other words - always quote globs passed to find.

---

### Post by codemaniac on 2013-02-20
I always use the quotes, forgot this time while copying the string from the OP's post. :D

Thank you.

---

### Post by GrouchyGaijin on 2013-02-23
Thanks guys!

I appreciate the help.

---

