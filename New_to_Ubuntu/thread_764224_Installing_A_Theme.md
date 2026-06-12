---
title: "Installing A Theme"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by hikujk123 on 2008-04-23
I am using xubuntu 64 hardy heron.  I downloaded a theme from xfce look.  How do I install it?

---

### Post by Paqman on 2008-04-23
Extract it into ~/.themes and you should be able to pick it from the normal theme chooser under "Settings"

---

### Post by hikujk123 on 2008-04-23
I get the following output:

 /home/username/.themes: No such file or directory

---

### Post by mbadawi23 on 2008-04-23
I think you can install the theme by selecting the package file you downloaded under System->preferences->Appearance and select to add the theme.

---

### Post by hikujk123 on 2008-04-23
That is only in ubuntu not xubuntu!

---

### Post by Paqman on 2008-04-23
> **hikujk123 said:**
> I get the following output:

 /home/username/.themes: No such file or directory

```

mkdir ~/.themes

```
...will solve that. 

Since this theme is lurking in your /home directory, it won't be available to other users.

---

### Post by mbadawi23 on 2008-04-23
> **hikujk123 said:**
> That is only in ubuntu not xubuntu!

Oh, sorry about the confusion. Then I have no clue. Good luck though.

---

### Post by hikujk123 on 2008-04-24
Thank you paqman.  It worked.

---

### Post by Modnar1 on 2008-06-01
Hi i have the .themes directory however after putting the theme in the folder it still doesn't show up in the user interace options menu (i also use xubuntu). i am trying to install the darkerice theme but haven't be able to use it so far! any help would be appreciated

---

### Post by linux phreak on 2008-06-02
Open the compressed file and place the theme file inside the .themes folder in your home directory.You must not put the file you downloaded directly into the .themes folder.

---

### Post by Modnar1 on 2008-06-03
i had already tried that, am i supposed to put the files gtk-2.0 and metacity-1 as seperate files or leave them inside the folder darkerice, as there seems to be repeat files and i have tried putting the files inside the .themes directory in about every possible way and i still am unable to select the theme from the user interface list

---

