---
title: "Re-enabling hibernate"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by silverpetals on 2012-07-30
Hi, I've just installed Kubuntu on my Acer netbook and it's great so far. Sleep appears to crash it however, so I tried hibernating from the terminal and it worked fine, so I am trying to re-enable it for use in the menus to replace the sleep option. I've tried following the instructions from [here]("https://help.ubuntu.com/12.04/ubuntu-help/power-hibernate.html") but when I go to create the text file in /etc/polkit-1/localauthority/50-local.d/ with Kate, it errors and tells me to check that I have write access to the location. Being a bit of a newbie to Linux I could do with a bit of help as to how I gain write access to that location... thanks in advance :)

---

### Post by Elfy on 2012-07-30
You need to be root, try 

```
kdesudo kate /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
```

---

