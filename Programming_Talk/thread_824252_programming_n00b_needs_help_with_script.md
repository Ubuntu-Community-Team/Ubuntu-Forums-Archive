---
title: "programming n00b needs help with script"
date: 2008-06-09
forum: Programming Talk
---

### Post by NullHead on 2008-06-09
well ... I'm trying to make a script to check if a package is installed or not ... well I have no idea on how to do this, so I gave it my best shot ... here is where the script is located: [http://pastebin.ubuntu.com/18947/](http://pastebin.ubuntu.com/18947/)

any help would be nice... if I don't understand a particular aspect of anyone's help I'll be sure to ask about it. 

Thanks in advance!

---

### Post by geirha on 2008-06-10
I believe this should work 
[php]
if dpkg -l 'python-tk' | grep -q '^i'; then
    echo package is installed
else
    echo package is not installed
fi
[/php]

Alternatively, you can use apturl (which is the program that is run when you open an apt-url in firefox)
```
apturl apt:python-tk
```
If the package is installed, a dialog window will tell you so, if it is not, a dialog window will ask you if you want to install it.

---

### Post by NullHead on 2008-06-10
> **geirha said:**
> I believe this should work 
[php]
if dpkg -l 'python-tk' | grep -q '^i'; then
    echo package is installed
else
    echo package is not installed
fi
[/php]

Alternatively, you can use apturl (which is the program that is run when you open an apt-url in firefox)
```
apturl apt:python-tk
```
If the package is installed, a dialog window will tell you so, if it is not, a dialog window will ask you if you want to install it.

Thank you very much for the reply! What you suggested, dpkg -l ..., will work for what I want to do with this script. 

As a n00b I have to ask what '^i' does after the grep -q :confused: It's so simple ... yet I cannot seem to grasp the understanding of it. 

You can see I tried ... but I didn't know of another way to detect if the package is installed or not.

---

### Post by Martin Witte on 2008-06-10
> **NullHead said:**
> what '^i' does after the grep -q

It is a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression"), this one means print all lines starting with an 'i', where '^' stands for the begin of a line

---

### Post by NullHead on 2008-06-10
Thanks for your help! I've just learned something! :D

---

### Post by altonbr on 2008-06-10
Here's a snippet of one of my scripts checking if certain libraries are installed
```
GUI_LIBS="libx11-6
libxtst6
libxt6
libxrender1
libxi6"
for F in $GUI_LIBS; do
	if [ $NEED_GUI_LIBS -eq 0 ]; then
		INSTALLED=`dpkg --get-selections | grep $F`
		if [ "$INSTALLED" == "" ]; then
			NEED_GUI_LIBS=1
		fi
	fi
done
```

---

