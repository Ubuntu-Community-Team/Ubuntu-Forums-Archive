---
title: "Shell command to open a window?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by ant2ne on 2008-05-03
What is the bash command to open a nautilus window at a given location?

Thanks

---

### Post by ddrichardson on 2008-05-03
Do you mean: nautilus pathname

---

### Post by MrWES on 2008-05-03
right click on the desktop and choose create launcher | then in the command portion of the new launcher type nautilus /home/USERNAME/Documents

this will create an icon/launcher that will bring you directly to your Documents directory via nautilus.

Adjust accordingly.


Bill

---

### Post by ant2ne on 2008-05-04
I would like to add a line to a shell script that opens a window in a given path location. 

I don't want to enter the path each time.

---

### Post by Joeb454 on 2008-05-04
Then add the path location to the shell script, say you wanted to open /var/www/mysite/ then you would enter ```
nautilus /var/www/mysite/
```

Unless you want to ask for what path to open each time of course :)

---

