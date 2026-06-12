---
title: "Password"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by Cowbobob on 2012-01-19
When I enter my password to go into Ubuntu 11.10 I get a black screen that shows bob@bob-desktop and can go no further. Any ideas how to fix?
     thanks

---

### Post by M!K3_$ on 2012-01-19
Is this a default vanilla installation?
Or have you been modifying things? If you have been modifying things, what was the last thing you did?

---

### Post by Cowbobob on 2012-01-20
> **M!K3_$ said:**
> Is this a default vanilla installation?
Or have you been modifying things? If you have been modifying things, what was the last thing you did?

The only thing I did was to change my password.

---

### Post by snowpine on 2012-01-20
Type:

```
startx
```

to launch the X windows manager (the GUI interface).

If it doesn't work then it will at least give you some detailed error messages to troubleshoot.

---

### Post by Cowbobob on 2012-01-20
I typed startx in and got the following response
X user not authorized to run the X server, aborting
XIO fatal IO error 11 (resource temporally unavailable) on X server ":0"
After 7 requests (7 known processed) with 0 events remaining.

---

### Post by snowpine on 2012-01-20
I'm not familiar with that error message, I'm sorry. :(

---

### Post by /bin/sh on 2012-01-20
try this:
```

sudo startx

```

---

### Post by CoffeeRain on 2012-01-20
It sounds like for some reason your user doesn't have permission to use X.

---

### Post by grahammechanical on 2012-01-20
As a wild guess I would say that you do not have a desktop environment installed. Did you install Ubuntu server edition?

You are at the command line. It is Linux without a desktop environment. At the least you need someone to give you the commands to download and install Ubuntu-desktop and possibly also Compiz.

I am not sure of the commands, so you might want to wait until someone more experienced advises you but I think that the command is

```
sudo apt-get install ubuntu-desktop
```

Someone correct me if I am wrong.

Regards.

---

### Post by /bin/sh on 2012-01-20
or you can try:
```

sudo apt-get install unity

```

---

