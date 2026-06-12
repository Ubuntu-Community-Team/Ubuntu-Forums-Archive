---
title: "[SOLVED] installing IEs4Linux"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by rockerphil on 2008-06-04
ok, here's the deal, i've got the IEs4Linux tarball downloaded and extracted, and the psychocats tutorial is pretty simple and blow by blow, but i'm not using Gnome, KDE or even Xfce as my DE, i'm using a minimal OS built from the command line up, and i'm using ROX as my filer, so when i click the "ies4linux" as it says in the tutorial i don't get the popup asking me what to do with it, so i can't choose "run in terminal" so is there any way i can run the file with a terminal command? thanx in advance guys



Phil

---

### Post by ChameleonDave on 2008-06-04
Just run it from the command line with "--help" after it.

That will give you all the info you need to run it effectively in the terminal.  For example, it will tell you to put "--no-gui".

---

### Post by rockerphil on 2008-06-04
that's the thing though, i've tried running the file in the terminal and this is what i get



phil@phil:~/ies4linux-2.99.0$ ls
ies4linux  lang  lib  LICENSE  mac  README  ui  winereg
phil@phil:~/ies4linux-2.99.0$ ies4linux
-bash: ies4linux: command not found
phil@phil:~/ies4linux-2.99.0$

---

### Post by ChameleonDave on 2008-06-04
The shell does not look in the current directory for programs to run.  It looks in the paths set for that purpose (e.g. /usr/bin/).

To force it to run software from another location, enter a path for it.  For example:

```
~/ies4linux
```

The path for the current directory is a dot:

```
./ies4linux
```

---

### Post by rockerphil on 2008-06-04
ok, i just tried running ./ies4linux in the directory that the script is in and this is what i got



phil@phil:~/ies4linux-2.99.0$ ./ies4linux
No user interface available. Use command-line ies4linux or install pygtk. Details: [http://www.tatanka.com.br/ies4linux/page/No_GUI](http://www.tatanka.com.br/ies4linux/page/No_GUI)


i've tried sudo apt-get install pygtk and this is what i get


phil@phil:~$ sudo apt-get install pygtk
[sudo] password for phil:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pygtk
phil@phil:~$ 

and [http://www.tatanka.com.br/ies4linux/page/No_GUI](http://www.tatanka.com.br/ies4linux/page/No_GUI) is currently an undeveloped page

---

### Post by rockerphil on 2008-06-04
nevermind, i just made myself feel like a tard, i forgot to put --no-gui. thanx for the help though

---

