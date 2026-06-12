---
title: "Very stupid question"
date: 2007-08-12
forum: Programming Talk
---

### Post by ASPCartman on 2007-08-12
Hi guys. So, i whant to create a script that will install and configure ati drivers for me. But i need to edit xorg.conf and add few strings at the end. So what should i do to make this strings to appear there? :)

---

### Post by nichipet on 2007-08-12
It should go without saying that the first line of the script should be something to the effect of:

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

To add lines at the end of the file, try this:

```
echo "This is what I'm adding" >> /etc/X11/xorg.conf
```

A single > makes it into a new file, a very bad idea in this case. Two >> means append to the end of the file.

Editing lines already in xorg.conf is noticably more complicated, but possible.

If you post what you have already for the script, we can look at it and get everything figured out. For example, echo " " is only correct in certain cases. It may be better as echo ' ' (single quotes).

And it's not a very stupid question. :)

---

### Post by rekahsoft on 2007-08-12
I made a little script to fix fglrx after a kernel update...u might find it handy :P
```
#!/bin/sh

if [ $(id -u) = "0" ]; then
	echo "Fixing fglrx"
	rm /usr/src/fglrx-kernel*.deb
	module-assistant prepare
	module-assistant update
	module-assistant build fglrx
	module-assistant install fglrx
	depmod
	depmod -a
else
	echo "You must have administrative privledges. Rerun as root."
fi
exit 0
```

---

### Post by ASPCartman on 2007-08-13
So look. Made in 5 minutes at 8 am . Going to bed now :lolflag:

I deleted " sign somewhere . So exactly cos of " " all becomes crazy.
And i really dont know what is this "echo" is. I just saw in another script that if there is ( echo "bla_bla" ) then u can see "bla_bla" in terminal :) I really need to learn ... whatever this language is. Some help? :confused:

---

### Post by Lux Perpetua on 2007-08-13
echo is a program that displays its command line arguments to its standard output. (Type "echo blah blah blah" in a terminal.)

---

### Post by tgalati4 on 2007-08-13
This crazy language is called BASH.  It stands for Bourne Again Shell.  There are several good on-line books and tutorials.  A simple google search on "bash tutorial" will get you scripting in no time.

---

### Post by ASPCartman on 2007-08-13
Thank u guys :popcorn:

---

