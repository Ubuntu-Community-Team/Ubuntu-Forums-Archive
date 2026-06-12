---
title: "[SOLVED] Making them see each other"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Cuttysark on 2008-08-28
I wasn't sure whether to post in the networking section or this one, but I am, above all else, an absolute beginner, so here goes.

I've now gone totally Ubuntu on both my laptop and desktop, and am loving every minute. Enjoying it even more than when I started learning DOS from scratch way back when, and I being genuine here.

Anyhow, when I still used XP on both machines, I bought a program called Network Magic, and this allowed them to see each other via my router. It was really handy for transferring files and sharing my printer. I'd like to be able to do the same thing now with Ubuntu (Hardy Heron).

Is there an easy way, a dummy's guide or is it more involved?

---

### Post by nicedude on 2008-08-28
You shouldn't have to buy a networking program for even Windows and you can't for linux since they are all free. If you want to have a solution that works with XP & Ubuntu I would suggest you look at filezilla as it works on both and is a FTP software where you setup shares and can access them from other PC's or via the Internet. I am sure if you google "filezilla ubuntu setup" you can find a guide for how to use it.


hope that helps

---

### Post by halitech on 2008-08-28
Look at samba (if you are thinking about sharing with windows down the road) and NFS if only using linux.

---

### Post by tuxulin on 2008-08-28
in terminal type
sudo apt-get install openssh-server openssh-client and install on both machines
then goto Places -> Connect to Server

when the dialog box apear fill it in 
in service type box select --- ssh
in the server box put the ip of the target machine
port 22 is safe since (i think) you will be using it for internal use

the rest is simple or leave empty
then lastly click connect

then login with target machine user account

Tuxulin

******* EDIT ****************
for the printer then see

[http://blog.mypapit.net/2008/05/enable-printer-sharing-with-ubuntu-computers.html](http://blog.mypapit.net/2008/05/enable-printer-sharing-with-ubuntu-computers.html)

---

### Post by halitech on 2008-08-28
lets go back to basics here for a minute and ask an important question, is the OP well versed in linux commands or do they want a file manager window top pop up so they can point and click to where the files are they want to access?

---

### Post by drs305 on 2008-08-28
Just in case you need a bit of elaboration on tuxulin's post:

> **tuxulin said:**
> 
in the server box put the ip of the target machine
On the other machine, run:
```

ifconfig

```
What you want is whatever the value in bold is:
```

eth0      Link encap:Ethernet  HWaddr 00:18:f3:b1:28:a7  
[COLOR="Red"]inet addr:[/COLOR]**192.168.0.9**  Bcast:192.168.0.255  Mask:255.255.255.0

```

> 
then login with target machine user account


Enter the username used on the other computer.

---

### Post by Cuttysark on 2008-08-28
Thanks guys, that went smoothly and painlessly, both machines can see each other now and thanks also for the printer info, that also went without a hitch.

---

