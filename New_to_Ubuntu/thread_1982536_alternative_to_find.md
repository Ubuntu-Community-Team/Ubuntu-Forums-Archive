---
title: "alternative to find"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by cheatos on 2012-05-18
So, I need to do some searching via ssh and as its a real pain doing it by always changing directories until I found the right file, I tried using a search command. I already tried find, but this only searches my current working directory (or I'm doing something wrong) but I would like to recursively search all folders beneath my cwd. Is there a commadn which will do this for me? Or an option for find what I just dien't see (looked at the find --help and the man page, but didn't see anything...

---

### Post by billyseth on 2012-05-18
you can tell find where to begin its search, so for example...

```
find / -name SEARCHTERM
```

will locate instances of SEARCHTERM on your system, it'll probably pop up a bunch of "Permission denied" stuff while trying to search some of the lower level system directories.

to get a more specific location search, go with something like

```
find /home/USERNAME/ -name SEARCHTERM
```

---

### Post by cheatos on 2012-05-18
so, will this also work via ssh?
And i can't get sudo privileges on that computer I'm logging in to, would this be a problem then?

---

### Post by billyseth on 2012-05-18
sorry, I edited my previous post, does the new info help you?

---

### Post by David Andersson on 2012-05-18
[QUOTE=cheatos] I already tried find, but this only searches my current working directory (or I'm doing something wrong) but I would like to recursively search all folders beneath my cwd. [/QUOTE]
By default the *find* command will search the current working directory AND all sub-directories. Exactly what arguments did you type to find?
[QUOTE=cheatos]And i can't get sudo privileges on that computer I'm logging in to, would this be a problem then? [/QUOTE]
No problem. The *find* command will not be able to go into directories where you have no read-access, but that should be no problem if you are searching your home directory. (That is, you cannot find other users porn this way.)(*)

As an alternative to *find* you have the *locate* command. It lists all file name pathes on the system that matches you search pattern (except for files in directories you have no read access to, so you cannot find out if other users have porn that way.)(*) Locate uses a database that is updated every night (by default), so it would not find new files. In package *mlocate*.

(*) (With sudo or root access you can find or locate *all* files of other users.)

---

### Post by cheatos on 2012-05-19
Well, this is what I typed to find stuff:

```
find file
```

so no options or something, I also tried find -r but that gave me an illegal value...

---

### Post by jtarin on 2012-05-19
Try "locate" command. First update your data base with the command ```
sudo updatedb
```That will take a few moments to run if it's the first time. When it returns to the command prompt issue the command ```
locate <filename>
```

---

### Post by David Andersson on 2012-05-19
> **cheatos said:**
> Well, this is what I typed to find stuff:

```
find file
```


That is wrong. (Well not always, but mostly.) Have you read the manual page? Command **man find**. Onethousanthrehundredandfourty lines down the manual page there are usage examples.

The simplest use example: searching current directory and all sub-directories:
```
find -name '*Madonna*.mp3'
```

Another example: find files that are *not* mp3 and at most 3 days old:
```
find -not -name '*.mp3' -and -mtime -3
```

---

### Post by cheatos on 2012-05-19
ok, thank you for your help David Andersson, I've looked at the man page, but I haven't scrolled 1000 lines down ;)

But with your examples I'll try it again and then come back here to mark as solved if it worked well.

edit:ANother thing, will find now locate folders as well?
2nd edi: It will

I'll mark this solved now.
Thanks alot for your help!

---

