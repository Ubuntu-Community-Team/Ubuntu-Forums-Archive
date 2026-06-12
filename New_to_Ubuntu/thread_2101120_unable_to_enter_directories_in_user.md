---
title: "unable to enter directories in user"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by linux spartan on 2013-01-03
hi am a newbie to ubuntu and using 12.04 and trying to access a folder in my desktop via terminal but i have tried the following commands but cant get into desktop directory,suggestions please?
xxx@xxx-pressario-CQ56-Notebook-PC:~$ pwd
/home/xxx
xxx@xxx-Presario-CQ56-Notebook-PC:~$ ls

Desktop                
Documents             
Downloads  

xxx@xxx-Presario-CQ56-Notebook-PC:~$ cd /desktop/
bash: cd: /desktop/: No such file or directory
xxx@xxx-Presario-CQ56-Notebook-PC:~$

---

### Post by arpanaut on 2013-01-03
Linux is case sensitive.
You would need to enter such as ```
johnmac@PP-lts:~$ cd Desktop
johnmac@PP-lts:~/Desktop$ 
```

Edit: need to check my syntax before I post!

---

### Post by oldos2er on 2013-01-03
```
cd De[Tab]
``` should complete the command for you.

cd /Desktop won't work, there's no Desktop directory (at least by default) in /

---

### Post by slickymaster on 2013-01-03
> **linux spartan said:**
> xxx@xxx-Presario-CQ56-Notebook-PC:~$ cd /desktop/
bash: cd: /desktop/: No such file or directory
xxx@xxx-Presario-CQ56-Notebook-PC:~$

Your code is wrong, you should type:
```
cd Desktop
```

---

### Post by linux spartan on 2013-01-03
thankyou,this command actually worked.really apreciate

---

