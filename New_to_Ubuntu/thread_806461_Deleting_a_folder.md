---
title: "Deleting a folder ?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Tubby on 2008-05-25
Hi, i transfered some files from a cd to the unbuntu desktop, there is one folder now i want to delete now but it will not let me me drag it to the bin, it has that padlock thing over it, can someone please help me out.
thanks,

---

### Post by IHATEDLINK on 2008-05-25
Go to Applications>Accessories>Terminal and type:

```
gksudo nautilus
```

Fill in your password, navigate to your desktop folder and delete the folder you wanted to.

---

### Post by HotShotDJ on 2008-05-25
I typically recommend installing Midnight Commander (sudo apt-get install mc) and then run it as root (sudo mc) to do this.  It can also be accomplished at the command line, but the command is considered dangerous and might result in my receiving an infraction for including it in a message.

---

### Post by Sinkingships7 on 2008-05-25
Reflecting off of what IHATEDLINK said, I VERY strongly recommend that you DO NOT use sudo nautilus. Instead, use
```
gksudo nautilus
```
You should always use a graphical-sudo if you're going to launch an application with super user privileges. Other than that, follow everything else he said and you'll be fine.

Also, don't get used to using nautilus as root. It's bad habit, and you should only do it if you know what you're doing.

---

### Post by Tubby on 2008-05-25
Thanks very much IHATEDLINK, and thanks to everyone else that has replied.
much appreciated.

---

