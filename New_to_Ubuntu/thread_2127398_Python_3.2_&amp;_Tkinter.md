---
title: "Python 3.2 &amp; Tkinter"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by Sky001 on 2013-03-19
Hello everyone, 
I've recently bumped into a problem when istalling my the Tkinter package for Python3. I'm using a personal computer and these are the steps i went through to install Python3 and Tkinter. 

```
sudo apt-get install python3
sudo apt-get install python3-tk
```

Synaptic shows that python3-tk is indeed installed, yet when using **python3 -m Tkinter** i get **/usr/local/bin/python3: No module named Tkinter**. I'm pretty sure i'm doing something wrong. I just don't know what it is. 

Typing **whereis python3** in terminal gives:

python3: /usr/bin/python3.2 /usr/bin/python3 /usr/bin/python3.2mu /etc/python3.2 /etc/python3 /usr/lib/python3.2 /usr/lib/python3 /usr/bin/X11/python3.2 /usr/bin/X11/python3 /usr/bin/X11/python3.2mu /usr/local/bin/python3.2 /usr/local/bin/python3 /usr/local/bin/python3.2-config /usr/local/bin/python3.2m-config /usr/local/bin/python3.2m /usr/local/lib/python3.2 /usr/include/python3.2mu /usr/share/python3 /usr/share/man/man1/python3.1.gz

A little while back, I had the same problem with my default Python installation. I did some research and found this solution: 

```
sudo apt-get install python-support
sudo update-python-modules -a
```

Modifying the above code to what is below does not fix my problem. 

```
sudo apt-get install python3-support
sudo update-python-modules -a 
```

So then how do i go about fixing this?

---

### Post by Sky001 on 2013-03-27
Anyone there? I need help!  . . . Please

---

