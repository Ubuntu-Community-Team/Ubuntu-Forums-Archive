---
title: "[SOLVED] Livestation TV"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by ibbill on 2008-10-22
Pardon my stupidity but have downloaded this program to my desktop. It says to navigate to the download.

Can someone tell me what to type in the terminal to navigate to the download please. :confused:

[http://www.livestation.com/downloads?tracker=main_menu](http://www.livestation.com/downloads?tracker=main_menu)

---

### Post by Titan8990 on 2008-10-22
Your desktop is located: ~/Desktop.

So:

cd ~/Desktop/NAMEOFFOLDER


This will go in the directory located on your desktop.

---

### Post by ibbill on 2008-10-22
typed the following and got this in the terminal. thanks for the quick reply.

-desktop:~$ sudo cd ~/Desktop/Livestation-2.1.1.run
sudo: cd: command not found

---

### Post by greg@localhost on 2008-10-22
Why are you trying to 'sudo cd'?

See this thread: [http://ubuntuforums.org/showthread.php?t=507718](http://ubuntuforums.org/showthread.php?t=507718)

> The reason it is complaining is because the "cd" command is a shell built-in function, not an external command. Your system must lack an external cd executable. I've run into the same problem before. It's a nuisance. Apparently POSIX compliant systems should have a external cd command.

Edit: 

```

greg-powermac:pwd root# which cd
/usr/bin/cd

```

Looks like i'm OK ;)

---

### Post by ibbill on 2008-10-22
thanks for your help just going to let it go. Just not up on this linux. Heres what I tried again thanks for your help. Will wait for the new ibex and try again.

---

### Post by perlluver on 2008-10-22
That is a .run file, so you will want to, ```
cd ~/Desktop
``` then ```
./filename.run
``` hopefully it is set to run.  If not come back with the error message.

---

### Post by Sarmacid on 2008-10-22
Seems you need to execute that file. Try this

```
cd Desktop
./Livestation-2.1.1.run
```

if it doesn't work, maybe you need to set the permissions to execute it

```
sudo chmod +x Livestation-2.1.1.run
./Livestation-2.1.1.run
```

---

### Post by ibbill on 2008-10-22
Thanks not actuall sure what I did but I am now watching TV marking thread solve thanks again to all that helped

---

