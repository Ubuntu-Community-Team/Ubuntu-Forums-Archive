---
title: "command line help"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by Donald Spaulding on 2013-02-07
Hello
I'm trying to use thr command line to go to a file and open it
I type into the cl the ls-a command and then I want to look at a file listed there.
what command do I use to open the listed file.:(

---

### Post by Impavidus on 2013-02-07
How you can open the file depends on what kind of file it is.

Elaborate.

---

### Post by sudodus on 2013-02-07
> **Donald Spaulding said:**
> Hello
I'm trying to use thr command line to go to a file and open it
I type into the cl the ls-a command and then I want to look at a file listed there.
what command do I use to open the listed file.:(
thank you for answer, you can email me the answer if needed.at 



Welcome to the Ubuntu Forums :-)

0. Please don't publish your email address. Spammers might find it.

1. Change directory to where the file is located. Let us say it is a pdf file in your directory Documents

```
cd
```brings you to your home directory

```
ls -l
``` lists your files with the long list format

```
ls -la
``` lists also the hidden files. There are hidden files and directories in your home directory.

```
cd Documents
``````
ls -l
``` list your files in the current directory (now ~/Documents), and you should find your [FONT=Courier New][SIZE=3]file.pdf[/SIZE][/FONT] that you open with the pdf viewer evince
```
evince file.pdf
```You can view text files with less and edit text files with nano (or a GUI editor, different depending of the flavour of Ubuntu) or gedit

```
less file.txt
nano file.txt
gedit file.txt
```

---

### Post by Cheesemill on 2013-02-07
To open a file with the associated application you can use the xdg-open command...
```
xdg-open filename.pdf
```

---

### Post by mörgæs on 2013-02-07
Removed the e-mail address. Please keep the answers here where everybody benefits.

More on the command line:
[http://ubuntuforums.org/showthread.php?t=2015424](http://ubuntuforums.org/showthread.php?t=2015424)

---

### Post by Donald Spaulding on 2013-02-07
I have all my files in a dir My Dir which I cannot open with the cl.\
listed ls -l but could not open that file.
how do I open a file like my files where i would have all my files.

---

### Post by sudodus on 2013-02-07
> **Donald Spaulding said:**
> I have all my files in a dir My Dir which I cannot open with the cl.\
listed ls -l but could not open that file.
how do I open a file like my files where i would have all my files.
If there is a space in the name of the file or directory you must enclose it in quotes or escape the space with a \

```
cd "My dir"
less "my file.txt"
```
or
```
cd My\ dir
less my\ file.txt
```

In Linux it is also important to use the correct case (upper case or lower case)

"[FONT=Courier New]My dir[/FONT]" is another name than "[FONT=Courier New]my dir[/FONT]"

---

