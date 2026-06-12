---
title: "Help in Installing Scilab 5.4.0 in Ubuntu 12.04"
date: 2013-03-18
forum: New to Ubuntu
---

### Post by zemega on 2013-03-18
Hello, how do I install the application Scilab 5.4.0 (.tar.gz package) into Ubuntu 12.04? The available Scilab in the Software Center is 5.3.3 and I would lik to use version 5.4.0..

---

### Post by Perfect Storm on 2013-03-18
unpack it:
```
tar zxf scilab-5.4.0.bin.linux-x86_64.tar.gz
```

to run it:
```
cd scilab-5.4.0/bin
./scilab
```

---

### Post by zemega on 2013-03-18
I can run the program now. But can I add a shortcut or something to the Unity Launcher? Simply lock it to the launcher, close it and try to run it by clicking the launcher didnt work.

---

### Post by Perfect Storm on 2013-03-18
Then you need to use the command like;
```
sh -c "cd /path/to/bin && ./scilab"
```

---

### Post by zemega on 2013-03-18
I gotten the reply of 'Permission denied', even with sudo.

---

### Post by Perfect Storm on 2013-03-18
Pull out one of the launcher from dash to the Desktop (doesn't matter which app you pull to the Desktop). Right click and hit Properties.

Change the comman (in my case):
```
sh -c "cd ./Downloads/scilab-5.4.0/bin && ./scilab"
```

You can also give it a name, icon and comment.

---

### Post by zemega on 2013-03-18
How do you pull out the launcher? I tried dragging it from the launcher area to the desktop area, but nothing happened.

---

### Post by Perfect Storm on 2013-03-18
No, drag a whatever launcher from 'Dash'.
Hit the 'Super Key' to display Dash (the window button).

---

### Post by zemega on 2013-03-18
It worked, thank you. It took me quite a while because when I used the LibreOffice Writer launcher, the launcher file broke. I used Calculator instead.

---

