---
title: "unable to get a software program downloaded using package manager"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by brook on 2008-06-01
i downlaoded an software program using the synaptic, but i could not locate it in my laptop. so where should i look for it cuz the package manager says i bave it downloaded and installed

---

### Post by sdennie on 2008-06-01
You could try:

```

dpkg -L name_of_package | grep bin/

```

For instance:

```

dpkg -L metacity | grep bin/

```

---

### Post by brook on 2008-06-01
well i found that useful, now i can see the packages i downloaded and installed, but still another problem persists, how can i run this program, ....i mean i can't simply run what i have installed in /usr/bin/ , so what to do?

---

### Post by sdennie on 2008-06-01
I'm not completely sure what you mean.  If a program doesn't install itself into the Applications menu, it probably isn't a gui app and so the only way to run it is via what it installs in /usr/bin.  For example:

```

$ dpkg -L pidgin | grep bin/
/usr/bin/pidgin
$ pidgin

```

That should work just fine.

---

### Post by Bradtek on 2008-06-01
It would be helpful to know which program you are talking about so rather than giving you examples we might be able to give you an exact answer.

It could be as simple as making a Launcher on your desktop or in the menu.

---

### Post by brook on 2008-06-01
ok, i didnt say which program it is because it is a program on radio antenna, it is called yagiuda. 

well i can ask another question right? i have another ubuntu server here, which has internet connection, but i could not access the internet cuz ubuntu server is command line and i am not used to it. what command lines might be helpful to download packages to the server, (this time i need packages for ldap)

---

### Post by Bradtek on 2008-06-01
I downloaded and installed it.
It doesnt appear to be a GUI app (but not really sure)
Open a terminal and type 
```
yagi
```
This will give you
```
Yagi-Uda antenna analysis programs, version 1.19
Written by Dr. David Kirkby Ph.D. G8WRB (email:david.kirkby@onetel.net)

USAGE: yagi  [-dhps] filename 

Where options are:
   -d     Display  bar-graphs, proportional to element currents
   -h     Print this help screen
   -p     Print Z matrix to screen.
   -s     Suppress diagnostic output
'yagi' computes the currents at the centre of of each element of an antenna 
described in 'filename', where 'filename' was created by 'input' or 'first'.
After running 'yagi filename' type 'output filename'
```

To your question "Where should I look for it"
Open Synaptic, locate the installed program,
Click on it, Click on Properties, then Installed files Tab.
Often you will find the program starts from within  /usr/bin/
so look for a file that has been installed there and as in this case it is not always named as you might expect.

Edit:
in a terminal type 
```
man yagi
```
for the Manual

---

