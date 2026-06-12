---
title: "[SOLVED] Moblock is blocking all connections!"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-30
I tried installing Moblock, an application that blocks blacklisted IPs similar to peer guardian, and for some reason its now blocking all connections. I can't access the internet on my linux box. Here is how I installed it:

```
write this in the terminal:
gksu gedit /etc/apt/sources.list
enter your password
this will open a file
copy and paste this lines at the end of the file:
deb http://moblock-deb.sourceforge.net/debian unstable main
deb-src http://moblock-deb.sourceforge.net/debian unstable main
save the file and exit from the text editor(Ctrl+s, Alt+F4)
repeat the last step(write this in the terminal):
sudo apt-get update
sudo apt-get install moblock-nf
```

I would like to uninstall it so I can get back online! It doesn't appear in add/remove and, as a Linux newb, I don't know how to get rid of it and revert back to my old connection.

Any help is greatly appreciated thanks

---

### Post by rabidninjawombat on 2008-05-30
im a little bit of a noob myself, but you should be able to unstill it via synaptic. or 

```

sudo apt-get remove moblock-nf

```

please someone correct me if im wrong on the apt-get commands :)

---

### Post by iaculallad on 2008-05-30
Stop moblock first:

```
sudo moblock-control stop
```

Remove moblock application:

```
sudo apt-get remove --purge moblock
```

Try removing undeleted config file manually (either in /etc or /etc/moblock):

```
sudo rm -rf /etc/moblock
```

---

### Post by JimmyJim on 2008-05-30
> **iaculallad said:**
> Stop moblock first:

```
sudo moblock-control stop
```

Remove moblock application:

```
sudo apt-get remove --purge moblock
```

Try removing undeleted config file manually (either in /etc or /etc/moblock):

```
sudo rm -rf /etc/moblock
```

It worked :) Thanks a lot

---

### Post by rabidninjawombat on 2008-05-30
> **JimmyJim said:**
> It worked :) Thanks a lot

Good! make sure to mark your thread solved via the thread tools :) 

And thanks for the backup iaculallad,  this noob here is learning slowly but surely. :)

---

### Post by iaculallad on 2008-05-30
You're welcome. Always stop the moblock first (If its running) before trying to uninstall it. Go Ubuntu

---

### Post by jre on 2008-05-31
> **iaculallad said:**
> You're welcome. Always stop the moblock first (If its running) before trying to uninstall it. Go Ubuntu
That is done automatically. So it's not necessary, but of course it also doesn't do any harm.
If it did not stop automatically then please tell me, so that I can fix that.

But still thanks for providing support!
jre

BTW in post #1 there's a typo, it is moblock-nf**q**.

---

