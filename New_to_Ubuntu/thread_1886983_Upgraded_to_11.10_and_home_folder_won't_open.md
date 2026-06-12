---
title: "Upgraded to 11.10 and home folder won't open"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by neilp.18 on 2011-11-26
I upgraded to 11.10 and my home folder won't open.  It loaded and then doesn't open.  None of my pc's folder open.  Can someone help me please

---

### Post by insomniaccanuck on 2011-11-26
Can you open a terminal and run 'ls'?
That should give you the contents of your home folder in you Ubuntu install.

If your looking for files from another partition, say a windows partition, you have to mount that partition.  Usually giving your 'sudo' password, which by default is your user password.

---

### Post by Gone fishing on 2011-11-26
If you run gksu nautilus and then navigate to the home folder can you then see all the files etc?

If you can which is my guess you will then it is a permissions problem which can be solved by changing the permissions so that you the user owns the files by running sudo chown -R username /home/username in a terminal

if you are not sure of your username run whoami just to check

---

