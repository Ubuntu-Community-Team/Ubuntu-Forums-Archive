---
title: "Install gnome on Ubuntu Server"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Jensss on 2008-10-10
Hi,

I want to install gnome on Ubuntu Server.
What I found on the forum is that I should install ubuntu-desktop.
But I have no Internet connection on the server for the next days.
Can I install ubuntu-desktop by using for example a normal Ubuntu 8.04 disk?

Or is the only way to get an GUI to wait for my Internet connection?

Thanks 
Jens

---

### Post by Nepherte on 2008-10-10
It should work with the desktop ubuntu cd. Just add the cdrom as a software repository to your repository list.

---

### Post by hyper_ch on 2008-10-10
you should be able to install it with the alternate disk BUT why do you want to do that?

---

### Post by Nepherte on 2008-10-10
> **hyper_ch said:**
> you should be able to install it with the alternate disk BUT why do you want to do that?
hyper_ch does make a valid point. Typically, you don't need a gui for a server.

---

### Post by Jensss on 2008-10-10
I don't have any experience with Ubuntu Server.
But I do have with Windows Server. So if I have a GUI, I can better understand everything and learn how to work in terminal.

One last question: which command do I use to edit my sources.list?
gedit doesn't work on server...

---

### Post by Nepherte on 2008-10-10
You could use either nano or vi. I'd suggest nano since it's a little easier to use, certainly if you have no experience with a terminal.
```
sudo nano /etc/apt/sources.list
```

---

### Post by hyper_ch on 2008-10-10
a gui won't help you understand how the server works... editing config files and reading logs/error messages is not gui-dependant ;)

---

