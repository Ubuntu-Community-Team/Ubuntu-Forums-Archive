---
title: "sed difficulties. batch strip apostrophes from filename"
date: 2007-10-20
forum: Programming Talk
---

### Post by thespinesplitter on 2007-10-20
hello people, so i've been using linux for a long time but i've always avoided sed like the plague for the sole reason that it gets ridiculous really quicklly when i try to work with it and up to now i was able to do all my file renaming chores with perl's rename or graphical interfaces but now i've come accross a problem, i cant for the life of me, get sed to strip all the apostrophes from a batch of files.. 15,000 to be exact :)

so far i have this:

```
 find . -iname "*.jpg" | sed "s/'/mv "&" "1"/" | sh 
```

only problem is, it doesnt work and i dont get why :confused:


any help is much appreciated

---

### Post by cwaldbieser on 2007-10-20
> **thespinesplitter said:**
> hello people, so i've been using linux for a long time but i've always avoided sed like the plague for the sole reason that it gets ridiculous really quicklly when i try to work with it and up to now i was able to do all my file renaming chores with perl's rename or graphical interfaces but now i've come accross a problem, i cant for the life of me, get sed to strip all the apostrophes from a batch of files.. 15,000 to be exact :)

so far i have this:

```
 find . -iname "*.jpg" | sed "s/'/mv "&" "1"/" | sh 
```

only problem is, it doesnt work and i dont get why :confused:


any help is much appreciated

You did not say whether you were getting an error, or it renamed the files incorrectly, or it just had no effect.  A little more information would be helpful.

---

### Post by thespinesplitter on 2007-10-20
this is the error i get

```
 find . -iname "*.jpg" | sed "s/'/mv "&" "1"/" | sh
[1] 11937
sed: -e expression #1, char 7: unterminated `s' command
-bash:  1/: No such file or directory
[1]+  Exit 1                  find . -iname "*.jpg" | sed "s/'/mv "
```


i notice that the sed command is getting chopped off at the second quote but bash is giving me an error too saying 1 isnt a directory, im at a real loss here

---

### Post by ghostdog74 on 2007-10-20
you can use  bash inbuilt string replacement 

```

# var="test'dd.jpg"
# echo $var
test'dd.jpg
#echo ${var//"'"/}
testdd.jpg
# var="te'st'd'd.jpg"
# echo $var
te'st'd'd.jpg
# echo ${var//"'"/}
testdd.jpg


```

---

### Post by arsenic23 on 2007-10-20
Also, why can't you do this with rename ?
You said you normally perfer it, but never said why you couldn't just *[COLOR="DarkRed"]rename "s/'//g" *[/COLOR]* .

---

### Post by thespinesplitter on 2007-10-20
the files are in 89 different folders and rename doesnt work recursively

---

### Post by ghostdog74 on 2007-10-20
> **thespinesplitter said:**
> the files are in 89 different folders and rename doesnt work recursively

yeah, but find works recursively...anyway, you can try this with GNU find
```

# find /give_full_path -type f -name "*.jpg" -printf "%h %f\n" | while read path file ; do mv "$path/$file" "$path"/${file//"'"/} ;done >/dev/null 2>&1

```

---

### Post by thespinesplitter on 2007-10-20
thanks man, thats perfect, i can see it works for just about anything you want to strip.

---

