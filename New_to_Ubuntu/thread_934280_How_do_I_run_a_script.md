---
title: "How do I run a script?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by avalenc on 2008-09-30
I think that this is so basic that it doesn't get articulated.

How do I run a script? I want to install ALSA updates, as per
[http://ubuntuforums.org/showpost.php?p=5792918&postcount=104](http://ubuntuforums.org/showpost.php?p=5792918&postcount=104)

_but_ then I don't know how to open it, or untar it, or anything. I don't knwo what application I should use, and if I use tar -zxvf and then the file name, it tells me no such file or directory.

Maybe it's because I don't really know what directory it landed in? (And have no idea how to check it.) 

Help! (And thank you! I will be _so_ excited when I can finally record sound.)

---

### Post by kk0sse54 on 2008-09-30
the command tar xfvz <path to file here> will work just fine in untaring the package for you. From there if it's just a shell script just run it in the terminal by cd'ing to the directory and then sh ./<filename>.sh

---

### Post by jakupl on 2008-09-30
you need to find it first. Check your home folder and some subfolders.

---

### Post by cariboo on 2008-09-30
Firefox downloads to the desktop by default. All you have to do is double click the file and File-Roller will automatically open and ask you want to extract it to.

Once you have the file extracted check out the the read me file as it will tell you what depends you need to install before running the script.

Jim

---

### Post by Idefix82 on 2008-09-30
Are you using firefox? If you are then you check where the file landed by starting firefox and going to Edit->Preferences and see what the "Save files to" field says.
If the file is on the desktop, say, then you need to type in
```
cd Desktop
```
and then type in the tar command

---

### Post by nhasian on 2008-09-30
to help you find the file, in a terminal type

```
sudo updatedb
```


then you can use the command *locate* to find where your file is.  for example to find all files that end with .zip you would type

```
locate *.zip
```

---

