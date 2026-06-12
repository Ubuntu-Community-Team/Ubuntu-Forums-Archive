---
title: "Using grep to find an item and printing reslts to a file"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by jimw on 2014-01-22
First, apologies for what must be a simple question.


I once had a command  that would let me find every instance of a particular word in a file containing several subfiles, and printing that result to my Desktop.

Just recently, I have had no success in trying to use that same command, and I  can see no reason why.

Suppose I have a list of .odt files in a file named Goal, and I want to grep every instance of the word "Whitechurch" and print that list to a file in my Desktop, how should I write the command?

I do understand that first I have to get the file in the line before I start.

Any help would be appreciated.

---

### Post by sudodus on 2014-01-22
Do you mean 'a list of files in a file named Goal' or 'a list of files in a directory named Goal?

[SIZE=4]1. File[/SIZE]

```
grep  "Whitechurch" -f Goal
```

prints to terminal

```
grep  "Whitechurch" -f Goal > file.txt
```

prints to the file **file.txt**

[SIZE=4]2. Directory[/SIZE]

First change directory to where you have the files

cd Goal

```
grep  "Whitechurch" -f *
```

prints to terminal

```
grep  "Whitechurch" -f * >  file.txt
```

prints to the file **file.txt**

If you want to include subdirectories, search files with find and execute grep on each of them

```
find . -name "*" -exec grep -i "Whitechurch" {} \;
```

and then examine the files that match according to this search

[SIZE=4]*. Recoll[/SIZE]

A good alternative is to use ***Recoll***

```
sudo apt-get install recoll
```

*Edit*: Due to the special character of odt files, the general method with grep won't work. Thank you *steeldriver* for explaining it :-)

I have used Recoll, and it works well for me.

---

### Post by vasa1 on 2014-01-22
Hi Nio, and New Year's greetings :)

While "recoll" certainly seems as if it should work, there's a thread here for searching within .odt files without using "recoll":
[http://ubuntuforums.org/showthread.php?t=899179](http://ubuntuforums.org/showthread.php?t=899179)

I haven't tried it!

(Recoll seems to want to pull in a lot of qt dependencies.)

And here's something about odt2txt: [http://forums.pcworld.com/index.php?/topic/121183-ubuntu-linux-day-19-using-man-and-grep/page__view__findpost__p__497979](http://forums.pcworld.com/index.php?/topic/121183-ubuntu-linux-day-19-using-man-and-grep/page__view__findpost__p__497979)

---

### Post by vasa1 on 2014-01-22
@sudodus, is it okay if I PM you about something?

---

### Post by steeldriver on 2014-01-22
Newer odt files use a zipped XML container, so you need to jump through some hoops to use grep on them - for example

```

$ for file in *.odt; do unzip -c "$file" content.xml | grep -Ho --label="$file" 'Whitechurch'; done
file1.odt:Whitechurch

```

or to output *only* the filename(s) maybe something like

```

$ for file in *.odt; do unzip -c "$file" content.xml | (grep -q 'Whitechurch' && echo "$file"); done
file1.odt

```

---

### Post by sudodus on 2014-01-22
> **vasa1 said:**
> @sudodus, is it okay if I PM you about something?

Sure, you are welcome *vasa1* :-)

---

### Post by jimw on 2014-01-26
Thanks to  everyone for your responses, including the suggestions for other tools to use.  Back when I was using it, I was searching in *.sxw files, but now that I'm using *.odt, it appears that the situation is different.

I  haven't had a  chance to try all the suggestions, so I don't know which (if  any) work.

Perhaps I should clarify my original situation.  My Directory is named "Goal", and it contains files named Goal-01.odt through to Goal-23.odt.

What  I want to find is every instance  of the word "Whitechurch" in every file.

Thanks

JimW

---

