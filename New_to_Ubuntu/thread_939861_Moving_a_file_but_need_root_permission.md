---
title: "Moving a file but need root permission"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by coubury on 2008-10-06
Hello

I have a file i downloaded it's to get my usb wireless device to work

I need to movie it to /lib/firmware


THe file is on my desktop and is called

bcmwl5.sys


Its located /home/me/Desktop


I tried copying it over as you would in windows but it said i dont have permission

---

### Post by houbysoft.xf.cz on 2008-10-06
Open a terminal and type
```

sudo mv /home/me/Desktop/bcmwl5.sys /lib/firmware

```
It will ask you for your password, just enter it and press enter.

---

### Post by CLomax on 2008-10-06
For clarification I feel that I should add that the sudo command means you want administrator permission. Think of it as 'pseudo' root.

EDIT: After saying that, I looked at your bean count and felt silly.

---

### Post by jerome1232 on 2008-10-06
If you are an admin user on the system then you can escalate your permissions using gksu or sudo.

to open a filebrowser as root to accomplish this task
```
 hit alt+f2, type gksu nautilus hit enter
``` You will now have a file browser opened as the root user, be careful you can delete ANYTHING on the system

using the command line you could simply copy it as root
```
sudo mv ~/Desktop/bcmwl5.sys /lib/firmware
```

---

### Post by coubury on 2008-10-06
Thanks.

---

### Post by houbysoft.xf.cz on 2008-10-07
Btw, please mark your thread as "solved" ;) thanx

---

