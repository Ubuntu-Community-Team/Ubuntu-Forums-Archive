---
title: "shortcut cd"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-18
hi ubuntuforums,

if i have a folder structure like this: home/user/pics/animals/downloaded/google_images/mammals/ ,
is there a way to quicky cd into the mammals folder without typing the long directory?

---

### Post by zombifier25 on 2012-03-18
Well, place this at the end of your .bash_rc
```
export IMG=/home/user/pics/animals/downloaded/google_images/mammals/
```After you're done, type this in your terminal to apply the changes:
```
source .bashrc
```Done! Now, whenever you want to enter that directory, you only need to enter this:
```
cd $IMG
```

Of course, you can always replace IMG and the directory with whatever you like.

---

### Post by mferarri on 2012-03-18
> **zombifier25 said:**
> Well, place this at the end of your .bash_rc
```
export IMG=/home/user/pics/animals/downloaded/google_images/mammals/
```After you're done, type this in your terminal to apply the changes:
```
source .bashrc
```Done! Now, whenever you want to enter that directory, you only need to enter this:
```
cd $IMG
```

Of course, you can always replace IMG and the directory with whatever you like.

thanks dude, but kinda was wishing i could type the folder name and it would search for it and go to it.oh well.

---

### Post by oldos2er on 2012-03-18
Create an alias in ~/.bashrc, something like ```
alias mam='cd home/user/pics/animals/downloaded/google_images/mammals/'
``` Restart the shell, type *mam*.

---

