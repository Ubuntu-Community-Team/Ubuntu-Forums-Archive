---
title: "Howto: Print with Opera"
date: 2006-01-12
forum: Outdated Tutorials &amp; Tips
---

### Post by desperado666 on 2006-01-12
In order to print documents with Opera do this

Needed package libcupsys2-dev

Open terminal 
sudo apt-get install libcupsys2-dev

After that you need to do a softlink in /usr/lib
Open terminal

cd /usr/lib 

ln -s libcups.so.2 libcups.so 

Finish.
After that close and open Opera again and you should be able to print with Opera.

---

### Post by James Keating on 2007-05-26
Thank you. In addition to the symbolic link, I also needed one more step:

Under Print, Printer Program, Parameter, enter 
-stdin

Opera should already have listed the possible printer program or programs. Only this crucial parameter is missing (plus the libcups.so symbolic link).

Alternatively but not as simply (I've seen this on the Opera forums), one can make a file (any name, any location) with the lines

#!/bin/sh
lpr -stdin

and select it as the printer program in Opera. 
Different people's systems will need different initial commands, such as 
kprinter -stdin
or
gnome-printer -stdin

---

