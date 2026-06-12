---
title: "[SOLVED] error message"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by misswham on 2008-11-06
I am getting this error message when I try to do an update.

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

what do i do?

---

### Post by jenkinbr on 2008-11-06
try ```
sudo apt-get install -f
```
This will attempt to repair any broken packages you have on your system.

---

### Post by misswham on 2008-11-06
i did the command and this is what came up

desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglide2
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

am I supposed to do anything else?

---

### Post by jenkinbr on 2008-11-07
Try running your update again.  According to your output, you should be good to go.

---

### Post by misswham on 2008-12-17
I added a new user last night and when i tried to log on this morning under my username and password, it wouldnt take it and i had to log on under my new username.  Now all of my documents are under the other name and I it wont take my old username or password.  I also tried to make a new thread and for some reason I cant make a new one. I couldnt have been banned because I didnt do anything.  I think its because I cant get to my main username.  Does anyone know what has happened and how can I get back into my main username without wiping my harddrive clean and starting over.

---

