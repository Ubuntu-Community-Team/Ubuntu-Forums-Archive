---
title: "Starting a Python Program via Launcher"
date: 2006-10-18
forum: Programming Talk
---

### Post by thomasaaron on 2006-10-18
Hey, guys.
I just finished writing a python, text-mode program that backs up my files to a remote computer over the internet. 

The program works fine when I run it from IDLE or when I open a terminal and start it.

However, I'd like to start it from a desktop launch icon, but it doesn't work that way. In the launcher command field I typed the /home/thomasaaron/fbu.py and in the program I used the shebang line #!/usr/bin/env python.

So, what do I need to do to make it work that way?

I was also thinking that I'd like to set it up on anacron, but I'm thinking that if it doesn't work from the launcher, it probably won't launch from anacron either...but I've not tried yet.

Best,
Tom

---

### Post by Tomosaur on 2006-10-18
Did you make the file executable?
```

chmod +x myfile.py

```

---

### Post by angustia on 2006-10-18
> However, I'd like to start it from a desktop launch icon, but it doesn't work that way. In the launcher command field I typed the /home/thomasaaron/fbu.py and in the program I used the shebang line #!/usr/bin/env python.

look in /usr/share/applications, there are many *.desktop files, open anyone as text file and you will be happy

---

### Post by ublinux on 2007-09-12
I was having a problem running a python program from a desktop launcher. To get it working I did the following:

In a terminal: chmod +x filename.py
Launcher Command: gnome-terminal -e /home/UserID/filename.py

---

### Post by thomasaaron on 2007-09-12
Thanks guys.
That works perfectly.

---

### Post by JimmyBEng on 2007-09-12
why not put the following in the launcher?
```
/usr/bin/python pythonfile.py
```
Doesn't that work?

---

### Post by thomasaaron on 2007-09-13
Yes, that works too.

---

