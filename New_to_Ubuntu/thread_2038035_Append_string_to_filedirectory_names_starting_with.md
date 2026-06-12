---
title: "Append string to file/directory names starting with uppercase letters?"
date: 2012-08-05
forum: New to Ubuntu
---

### Post by thatrandomn00b on 2012-08-05
The title is pretty self-explanatory.

Basically I have a directory /data with some sub-directories, let's call them Dir1 Dir2 Dir3 dir1. I want to rename Dir1 Dir2 Dir3 to dataDir1 dataDir2 dataDir3. How would I do that?

I thought that maybe I could do something like:
```
cd /data
mv [[:upper:]]* data[[:upper:]]* 
```But, obviously, that doesn't work.

So really, my question is how do I specify mv -and any command- to act on the same file, when using a character class (I think they are called?)?

If it was one directory I'd do:
```
sudo mv ./Dir1 ./dataDir1
```Btw is there any way to use | rename Dir1 Dir2 Dir3 to datadir1 datadir2 datadir3with a single command?

PS. I'd apologise for the noob question, but since this sub-forum is " The perfect place to post for your Ubuntu support if you are new to Linux." I think it's redundant.

---

### Post by steeldriver on 2012-08-05
you should be able to do something like

```
rename -nv 's/^[[:upper:]]/data$&/' *
```(try it with the -n in; if it does what you want take the -n out)

or if you want to rename only ALL UPPER names

```
rename -nv 's/^[[:upper:]]+$/data$&/' *
```

---

### Post by thatrandomn00b on 2012-08-07
Thank you, it worked. (Even though, unfortunately, I don't understand how and the man page wasn't of much assistance.)

---

### Post by steeldriver on 2012-08-07
Glad it worked for you

The general format for these things is

```
s/*pattern*/*replacement*/*options*
```where s means substitute, *pattern *is the thing you want to match, and *replacement *is the thing you want to put in its place.

The secret sauce in this case is the '$&' sequence in the replacement string - which expands to equal the actual thing matched by *pattern*.

The ^ and $ just mark the beginning and end of the pattern, i.e. ^[[:upper:]] matches strings beginning with a POSIX upper case character; whereas [[:upper:]]$ would be strings ending with an [[:upper:]] - putting those together gives ^[[:upper:]]+$ which is a non-empty string that is upper case from start to finish.

Hope this helps.

---

