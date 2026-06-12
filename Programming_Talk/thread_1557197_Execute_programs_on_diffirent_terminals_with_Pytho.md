---
title: "Execute programs on diffirent terminals with Python"
date: 2010-08-20
forum: Programming Talk
---

### Post by esya on 2010-08-20
Hello,

I have been searching for my problem but I could not find a solution.

I am trying to run commands on different terminals from python code.

I can run commands by using os.popen(command) but it is using same terminal for each of them and it is not what I want.

I want to run "Xdmx :2 +xinerama -ac -configfile  ConfigFile - config first" command on one terminal then run "DISPLAY=localhost:1"  "gthumb image.jpg" commands in the second terminal

I have just started to use Python and I don't have enough experience with Ubuntu. I hope somebody can help me.

Thank you...

---

### Post by schauerlich on 2010-08-20
It sounds like you're trying to write a bash script in Python.

---

### Post by esya on 2010-08-20
Actually I am not. 

There is another parts of the code only these three commands for combine more than one screen as a one screen and chance display variable to the new big screen then show the image on the screen. 

First command runs infinity and when some programs wants to use the screen it catches the request. Because of that reason, I need two different terminal.

---

