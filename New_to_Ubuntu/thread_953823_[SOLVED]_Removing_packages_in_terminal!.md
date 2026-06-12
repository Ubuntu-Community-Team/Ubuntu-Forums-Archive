---
title: "[SOLVED] Removing packages in terminal!"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by drakeman007 on 2008-10-20
Can ayone help me with this please? i removed some packages of openoffice 2.4 via command line with the dpkg -r <packagename>, but if i list the openoffice package installed with dpkg -l | grep openoffice, i still see the openoffice packages but with RC in the beginning i have to uninstall the others with ii... why the uninstalled packages dont disappear from the list? i need to have an update or something like that?

---

### Post by drakeman007 on 2008-10-20
Now when i try to remove some of the others packages with ii i got and error "dependancy problems" how can i remove the other packageS?

---

### Post by Dr Small on 2008-10-20
> **drakeman007 said:**
> Now when i try to remove some of the others packages with ii i got and error "dependancy problems" how can i remove the other packageS?
The whole error would be helpful, but have you tried this?
```
sudo apt-get -f install
```

---

### Post by drakeman007 on 2008-10-20
I attach the image with the error i got when i try to remove the other packages! and wwhat is the meaning of the status ii and RC,
thanks! how i can remove the others packages?

---

### Post by kerry_s on 2008-10-20
your also not fully removing them, use:

sudo apt-get --purge remove openoffice*

i just read the man page for dpkg, better you use apt-get and only dpkg -i for local debs.

---

### Post by drakeman007 on 2008-10-20
> **kerry_s said:**
> your also not fully removing them, use:

sudo dpkg -rP openoffice*
or
sudo apt-get --purge remove openoffice*


Thanks, im downloading the openoffice again and installing the uninstalled components, when i finish im gonna try your solution and tell you if it works o not!
Thanks..

---

### Post by drakeman007 on 2008-10-20
> **kerry_s said:**
> your also not fully removing them, use:

sudo dpkg -rP openoffice*
or
sudo apt-get --purge remove openoffice*


Wow Kerry, thanks it works!! i got an error with the first command but with **"sudo apt-get purge remove openoffice*"** everything uninstalled ok!

Thanks for your amazing help!!!:guitar:

---

### Post by kerry_s on 2008-10-20
> **drakeman007 said:**
> Wow Kerry, thanks it works!! i got an error with the first command but with **"sudo apt-get purge remove openoffice*"** everything uninstalled ok!

Thanks for your amazing help!!!:guitar:

yeah, dpkg is not as good as apt-get, after reading the manual, i would not use it. apt-get is what i use.

---

### Post by drakeman007 on 2008-10-20
> **kerry_s said:**
> yeah, dpkg is not as good as apt-get, after reading the manual, i would not use it. apt-get is what i use.


Im going to clone your .bashrc file! heheheeh

---

### Post by Dr Small on 2008-10-20
> **drakeman007 said:**
> Im going to clone your sudoers file! heheheeh
Hmm? That screenshot is of ~/.bashrc

---

### Post by drakeman007 on 2008-10-20
> **Dr Small said:**
> Hmm? That screenshot is of ~/.bashrc


Sorry, you are right Sr. Small, my mistake! thanks for the correction!!!

---

### Post by kerry_s on 2008-10-20
> **drakeman007 said:**
> Im going to clone your .bashrc file! heheheeh

:lolflag: i just changed it to.

```
alias s='apt-cache search'
alias i='sudo apt-get install'
alias r='sudo apt-get --purge remove'
alias upd='sudo apt-get update;sudo apt-get dist-upgrade'
alias old='sudo apt-get clean;sudo orphaner'

```

i'm sure you can figure out how to add your own, but these are all i use.
just in case if the output is long on the cache search,you can make it pause, just press the space bar to scroll a page at a time, example:

s editor | less
or
s browser | more

i prefer less cause you can use the arrow keys to scroll the page up & down, q to quit.

---

