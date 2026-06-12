---
title: "Java jar file problems"
date: 2013-11-23
forum: New to Ubuntu
---

### Post by timlash on 2013-11-23
[FONT=arial]Using Ubuntu 11.10 on AMD64 machine.

Command:

root@mypc:/usr/[/FONT][FONT=arial]myApp# java -jar junk1.jar

Works great!


File:  /usr/myApp/junk1.sh looks like this:

#myApp Launcher
#
[/FONT][FONT=arial]java -jar [/FONT][FONT=arial]/usr/myApp/[/FONT][FONT=arial]junk1.jar


Command:

[/FONT][FONT=arial]root@mypc:/usr/[/FONT][FONT=arial]myApp# sh junk1.sh

Yields:

[/FONT][FONT=arial]Unable to access jarfile /usr/myApp/[/FONT][FONT=arial]junk1.jar

I've already run the following and get the same results:

[/FONT][FONT=arial]root@mypc:/usr/[/FONT][FONT=arial]myApp# [/FONT][FONT=arial]chmod 777 junk1.sh
[/FONT][FONT=arial]root@mypc:/usr/[/FONT][FONT=arial]myApp# [/FONT][FONT=arial]chmod 777 junk1.jar

What now?

TIA,
Tim[/FONT]

---

### Post by timlash on 2013-11-23
Runs from the command line, but not in a script file?  It must be something stupid.  Something in addition to the user. Ultimately, I want the script file to run at boot or login.  I thought this would be a softball.  Any help?

---

