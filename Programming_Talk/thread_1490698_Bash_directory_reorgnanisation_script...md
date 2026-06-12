---
title: "Bash directory reorgnanisation script.."
date: 2010-05-22
forum: Programming Talk
---

### Post by newsman on 2010-05-22
I made a dummy script to clean up my desktop / home folder it tends to become messy after downloading few things.....  

```

#mv *.jpg ~/Pictures
#mv *.pdf ~/pdf
#mv *.odt ~/office
#mv *.docx ~/office
#mv *.zip ~/zip
#mv *.rar ~/zip
#mv *.py ~/python

```

There was a problem with this script in that it does not check for existence of folders (in which case it would rename the files found by the first argument.

I was thinking of using this
```

[ -d "~/Pictures" ] || mkdir ~/Pictures
[ -f "*.jpg" ] && mv *.jpg ~/Pictures

```

But the first line tries to create the folder even though it exists.. thats not what i wanted, i only wanted it to be create it if it does not exist and move the files if they do exist.....

---

### Post by MadCow108 on 2010-05-22
an or is not the negation of and
do this:
[ ! -d directory ] && mkdir directory
although this will also fail when directory is a file
you should also check for that with -f

you should also add a trailing / to the directory to make the mv fail if the directory does not exist instead of renaming the file

---

### Post by stylishpants on 2010-05-22
You don't need the existence test at all.

Just do this:

```
mkdir -p ~/Pictures
```

With -p, the mkdir command will attempt to create the directory if the directory does not exist.  If the directory already exists, the command will exit with a 0 (success) error code anyway.

If a regular file (not a directory) exists with that name, then you'll get a non-zero exit code, which is also what you want.

---

### Post by kaibob on 2010-05-22
I don't think you can quote the tilde. Instead do something like

```
~/"my directory"
```

In your situation,

> $ [ -d "~/Pictures" ] || mkdir ~/Pictures
mkdir: cannot create directory `/home/kaibob/Pictures': File exists

$ [ -d ~/"Pictures" ] || mkdir ~/Pictures
$

Like stylishpants, I would omit the directory test and use the mkdir -p option.

---

### Post by diesch on 2010-05-22
> **newsman said:**
> I
I was thinking of using this
```

[ -d "~/Pictures" ] || mkdir ~/Pictures
[ -f "*.jpg" ] && mv *.jpg ~/Pictures

```But the first line tries to create the folder even though it exists.. thats not what i wanted, i only wanted it to be create it if it does not exist and move the files if they do exist.....

The ~ and * doesn't get expanded when you enclose it in quotes.
```
[ -d ~/Pictures ] || mkdir ~/Pictures
``` should work. Or use *mkdir -p* as stylishpants suggested.

---

### Post by newsman on 2010-05-23
Now my code looks somewhat like thisl

```
mkdir -p ~/txt
[ -f *.txt ] && mv *.txt ~/txt/

```

This gives a strange error when it comes across a text file(in this example 1.txt):


[: 18: 1.txt: unexpected operator

---

### Post by diesch on 2010-05-23
*[ -f ]* works only with exactly one file, not with multiple files. As shell patterns get expanded first they  don't work if they match not exactly one file.

But you can just run *mv* and ignore any error it throws when there's nothing to move.

---

### Post by kaibob on 2010-05-23
> **newsman said:**
> Now my code looks somewhat like thisl

```
mkdir -p ~/txt
[ -f *.txt ] && mv *.txt ~/txt/

```

This gives a strange error when it comes across a text file(in this example 1.txt):


[: 18: 1.txt: unexpected operator

The following FAQ provides some ways to do this:

[http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)

For your purposes, the simplest solution may be to eliminate the test and use the mv command by itself as diesch suggests. If the shell script is run from a terminal window and the error messages are bothersome, they can be eliminated by redirection to /dev/null.

> $ mv *.jpg ~/Pictures
mv: cannot stat `*.jpg': No such file or directory

$ mv *.jpg ~/Pictures 2> /dev/null
$

---

