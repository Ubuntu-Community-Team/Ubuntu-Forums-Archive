---
title: "Simple bash script: move by file extension."
date: 2013-02-09
forum: Programming Talk
---

### Post by sebastian.s on 2013-02-09
I have just recently started with Bash scripting, and i am trying to move files according to their file extension. Directly at the bash prompt i can do like this:

```
mv *+(.jpg|.jpeg|.gif|.png) ./pictures
```but if i try the same in my script i get a syntax error, this is what the script look like:

```
mv *+(.mp3) ./music

mv *+(.jpg|.jpeg|.gif|.png) ./pictures

mv *+(.doc|.pdf|.odt|.txt) ./document

mv *+(.deb|.zip|.gz) ./packets

mv *+(.iso) ./iso-files

exit 0
```Why is that?

---

### Post by cwsnyder on 2013-02-09
I think your script syntax is aborting on your .mp3 and .iso lines where you only have one option, but you are inserting the + and () which implies multiple options.

---

### Post by Vaphell on 2013-02-09
why don't you use standard globs

```
mv *.jpg *.jpeg *.gif *.png ./pictures
```
or
```
mv *.{jpg,jpeg,gif,png} ./pictures
```

---

### Post by sisco311 on 2013-02-10
+1 for standard globs or brace expansion.

If you want to use extended globs, you have to enable them:
```
shopt -s extglob
```

See:
[http://mywiki.wooledge.org/glob?action=show&redirect=globbing](http://mywiki.wooledge.org/glob?action=show&redirect=globbing)
[http://mywiki.wooledge.org/BraceExpansion](http://mywiki.wooledge.org/BraceExpansion)

---

### Post by Merrattic on 2013-02-10
Have a look here, might give you some help:

[http://ubuntuforums.org/showthread.php?t=2086723](http://ubuntuforums.org/showthread.php?t=2086723)

---

### Post by sudodus on 2013-02-10
There might be a problem with file names containing spaces.

I tested the following command line, and it works with such file names

```
for i in *+(.doc|.pdf|.odt|.txt);do ls "$i";done
```
and you can replace
[FONT="Courier New"][SIZE="3"]do ls "$i"[/SIZE][/FONT] with [FONT="Courier New"][SIZE="3"]do mv "$i" ./documents[/SIZE][/FONT]

---

### Post by Vaphell on 2013-02-10
no, globs are not sensitive to whitespaces at all (that's why they should be used directly as often as possible)

```
$ touch "test 1.txt" "test 2.txt" "test 1.pdf"
$ printf "[%s]\n" *.{txt,pdf}
[test 1.txt]
[test 2.txt]
[test 1.pdf]
$ shopt -s extglob
$ printf "[%s]\n" *+(.txt|.pdf)
[test 1.pdf]
[test 1.txt]
[test 2.txt]
```

---

### Post by sudodus on 2013-02-10
I see, but maybe don't see ;-)

Running a script file containing
```
ls *+(.doc|.pdf|.odt|.txt)
``` or
```
for i in *+(.doc|.pdf|.odt|.txt);do ls "$i";done
```
won't work when run by bash
```
bash script
```
but runs without problems when run by source
```
source script
```
Please explain the difference!

---

### Post by sisco311 on 2013-02-10
> **sudodus said:**
> There might be a problem with file names containing spaces.



EDIT: Yayy! Didn't refresh the page before posting. Vaphell beat me to it.

Nope. The file names produced by the glob do not undergo any further word-splitting, so even if a file contains internal whitespace, the expansion of a glob that matches that file will still preserve each filename as a single word.

If the glob does not match any file name and nullglob is not enabled then it remains unchanged. In this case mv will throw a `no such file or directory' error which can be safely ignored.

---

### Post by sisco311 on 2013-02-10
> **sudodus said:**
> I see, but maybe don't see ;-)

Running a script file containing
```
ls *+(.doc|.pdf|.odt|.txt)
``` or
```
for i in *+(.doc|.pdf|.odt|.txt);do ls "$i";done
```
won't work when run by bash
```
bash script
```
but runs without problems when run by source
```
source script
```
Please explain the difference!

`bash script' will run the script in a subshell where extglob is not enabled. You have to enable it in your script:

```
shopt -s extglob
commmand *+(whatever)
```

The `source' command or the dot (`.') command will run the commands from the script in the current shell.

---

### Post by sudodus on 2013-02-10
> **sisco311 said:**
> `bash script' will run the script in a subshell where extglob is not enabled. You have to enable it in your script:

```
shopt -s extglob
commmand *+(whatever)
```

The `source' command or the dot (`.') command will run the commands from the script in the current shell.
Thank you :-)

---

### Post by sebastian.s on 2013-02-10
Setting the shell options to extended fixed it the way i chose to do it, i found that method in the book i'm reading right now and i missed that i had to enable extglob.

> **sisco311 said:**
> 
If you want to use extended globs, you have to enable them:
```
shopt -s extglob
```

And of course using the standard globbings worked just fine aswell, thanks for the tip :)

> **Vaphell said:**
> why don't you use standard globs

```
mv *.jpg *.jpeg *.gif *.png ./pictures
```or
```
mv *.{jpg,jpeg,gif,png} ./pictures
```

---

