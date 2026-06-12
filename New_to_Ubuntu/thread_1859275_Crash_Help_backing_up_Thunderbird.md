---
title: "Crash Help backing up Thunderbird"
date: 2011-10-13
forum: New to Ubuntu
---

### Post by xsabrewulf on 2011-10-13
I recently "upgraded" to 11.10

and now when I boot I get the ubuntu loading screen (the dots) then it just goes to a black screen.

i updated from 10.10

anyways, I figure I need to reinstall the only issue I have is I REALLY need all my thunderbird emails and everything.

I downloaded 11.10 and I am currently on the LIVE disc

i went to EDIT and show hidden files/folders

I searched mozilla webpage, and I did what it says but there is no .thunderbird folder

I really need ubuntu repaired or find the profile folder.

---

### Post by wolfen69 on 2011-10-13
Just open your home folder and do Ctrl-H. Then you will see a .thunderbird folder. You can save that folder. You might need to open home folder with
```
sudo nautilus
```

---

### Post by xsabrewulf on 2011-10-13
I found the .thunderbird

but when I click on it, it says I don't have permissions

---

### Post by kolinab on 2011-10-13
not sure why it says you don't have permissions, since you ought to have permissions to things in your /home . . . I would try:

```
gksudo nautilus
```



Be careful using a root nautilus window . . .

---

