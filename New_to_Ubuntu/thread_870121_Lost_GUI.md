---
title: "Lost GUI"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-07-25
After trying to get DVD PLAYER TO WORK AND DOWNLOADING ati DRIVERS when I boot up I only get command line.
How do i GET BACK TO GNOME DESKTOP

PS this is my backup machine to connect on

---

### Post by /usr/bin/hacked? on 2008-07-25
try ```
startx
```

---

### Post by jamesrfla on 2008-07-25
> **/usr/bin/hacked? said:**
> try ```
startx
```

How do you put that code in that box like that when you reply?

---

### Post by Titan8990 on 2008-07-25
Did you alter your xorg.conf file? If so did you back it up first?

it is code is [] and then /code in brackets again []. 

It is simple BBCode used in forums everywhere: [http://en.wikipedia.org/wiki/BBC_code](http://en.wikipedia.org/wiki/BBC_code)

---

### Post by jamesrfla on 2008-07-25
Okay let me see if this works. 
```
startx
```

---

### Post by Titan8990 on 2008-07-25
If you get to know BBCcode then you will know basic HTML formatting. The main difference is html uses <> and BBCcode uses []. There is however much more html tags than BBCcode tags.

---

### Post by Midgetprawn on 2008-07-25
Ta I will try Xstart
The xorg file may have been altered by Stchman's sh script
Is there a defualt setting?

---

### Post by jamesrfla on 2008-07-25
> **Midgetprawn said:**
> Ta I will try Xstart
The xorg file may have been altered by Stchman's sh script
Is there a defualt setting?

It is startx not xstart.

---

### Post by Midgetprawn on 2008-07-25
Yeah but i'm dyslexic around compurets
Ta

---

### Post by steveneddy on 2008-07-25
What did you install?

---

### Post by loboc on 2008-07-25
```
startx
``` will read .xsession in your home directory
```

sudo /etc/init.d/gdm restart 

```
relaucnhes the gnome dipslay monitor which will load the login prompt and restore the gnome-session

---

