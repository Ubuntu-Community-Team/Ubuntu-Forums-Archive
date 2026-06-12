---
title: "where can i find my bash file."
date: 2008-06-10
forum: Programming Talk
---

### Post by suhailsqm on 2008-06-10
i need to add a few directories to the PATH. could some one tell me which bashrc file to modify and where it is available.

i am currently using ubuntu 8.04, kde 

thanks.

---

### Post by suhailsqm on 2008-06-10
:confused:

---

### Post by ibutho on 2008-06-10
The correct file to add your paths is ~/.bash_profile (a hidden file in your home directory). To append to the path, you would add a line like
```
export PATH=$PATH:/new/path1/bin:/new/path2/bin
```
You may need to logout and back in again for the changes to take effect. If you don't want to do that you can simply run "source ~/.bash_profile" or "bash".

---

### Post by suhailsqm on 2008-06-13
qmss2@hesperus:/home$ ls -a
.  ..  qmss2
i can not find any bash files other that .bash_history in my home folder..:(:(

---

### Post by pedro_orange on 2008-06-13
```
ls -a ~
```

There should be a .bashrc file in there unless it's been moved. Thats the default place for .bash_profile, .bash_logout and .bashrc files.

---

### Post by KingTermite on 2008-06-13
You home directory. You probably want to put that in your .bashrc file.

---

