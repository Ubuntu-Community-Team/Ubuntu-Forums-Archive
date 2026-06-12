---
title: "cannot run script"
date: 2008-11-13
forum: Programming Talk
---

### Post by creta on 2008-11-13
hello to everyone

i am trying to run a script (rapidget) (in order to download from rapidshare
i had no problems till i started to do some chmod staff in order to run 
openFOAM. Anyway now every time i try to execute the script i get a message:
sh: Can't open rapidget
Moreover i although i can see the contents of the file where i extracted the script in the graphical interface, whenever i type dir to the directory tha the script is extracted, from the terminal, it doesn't seem to have anything inside.

creta@creta-desktop:~$cd rapidshare
creta@creta-desktop:~/rapidshare$ sh rapidget -f down.txt
sh: Can't open rapidget
creta@creta-desktop:~/rapidshare$ dir     
creta@creta-desktop:~/rapidshare$ 

the rapidget script has 
owner:creta
access:r and w
group:creta
access:r
otehers
access:r

and i have allowed executing the programm

....and after posting the prblm 
found out that i cannot see the contents from the terminal of any directory i create at my desktop 

thanks in advance

---

### Post by geirha on 2008-11-13
The default directory you're in when you open a terminal is your homedir. The desktop is a subdir of your home directory. To get to your desktop:
```
~$ xdg-user-dir DESKTOP
/home/geirha/Desktop
~$ cd Desktop
~/Desktop$ ls

```

If you put the rapidshare folder on your desktop, that should be where you'll find it.

---

### Post by creta on 2008-11-13
thanks a lot geirha!

---

