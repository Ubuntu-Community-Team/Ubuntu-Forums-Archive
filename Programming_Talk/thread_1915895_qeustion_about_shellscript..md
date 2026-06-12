---
title: "qeustion about shellscript."
date: 2012-01-27
forum: Programming Talk
---

### Post by WolfgangNL on 2012-01-27
well i need help about /dev/null 

i want just if people have choose number line of files. 
if people type number 3 line send to /dev/null/


but i tried.. i dont know how works

i did make number of line like

" ```
nl /home/user/mail > /home/user/mail2
``` "


```
cat /home/user/mail2;
read -p "Please choose number send to trash | Choose Number:" choosenr;
cat /home/user/mail | egrep -1 "\<^$choosenr\>" > /dev/null
```

maybe any someone idea about those script ? or i need some add in shellscript?


btw i use ubuntu 


Wolfgang

---

