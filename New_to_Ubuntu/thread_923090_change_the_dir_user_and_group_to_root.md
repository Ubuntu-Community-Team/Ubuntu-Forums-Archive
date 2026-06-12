---
title: "change the dir user and group to root"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by 007casper on 2008-09-18
Hiya

I have been using sudo chown root:root palm*

I need to change the user, and the group to root for a directory... 

however, the files in the directory, and its subdirectories dont change 

I have been doing it one at a time... and it will be eternity before I finish the whole subdirectories and its associated files

please, advise how I can change it in one shot????

Thank you so much!

---

### Post by tuxxy on 2008-09-18
Try -R
```

chown -R
```

[http://www.computerhope.com/unix/uchown.htm](http://www.computerhope.com/unix/uchown.htm)

---

### Post by iaculallad on 2008-09-18
Use the -R/-r switch to recursively do the job for you:

```
sudo chown -R root:root palm
```

---

