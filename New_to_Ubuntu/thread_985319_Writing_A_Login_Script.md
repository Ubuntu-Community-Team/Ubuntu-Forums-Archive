---
title: "Writing A Login Script"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by Qsl1pknotp on 2008-11-17
So I'm a newbie to Ubuntu. I noticed that the login screen, you can edit the picture.  So I was wondering if I could get rid of the picture, and just have terminal/grub pop up that says.  
Login:
Password:

Thanks for any help.

---

### Post by walkerk on 2008-11-17
nm

---

### Post by markjensen on 2008-11-17
You want to login through a terminal?

If I understand your wishes correctly, then you want to boot into runlevel 3 (text mode), not runlevel 5 (X11 GUI).

Edit your /etc/inittab file, and change the line that says```
id:5:initdefault:
```to```
id:3:initdefault:
```

---

### Post by Qsl1pknotp on 2008-11-17
> **markjensen said:**
> You want to login through a terminal?

If I understand your wishes correctly, then you want to boot into runlevel 3 (text mode), not runlevel 5 (X11 GUI).

Edit your /etc/inittab file, and change the line that says```
id:5:initdefault:
```to```
id:3:initdefault:
```


Yes that's what I would like to do.  But when I open /etc/inittab, all I get is a blank page.  Is this how it's supposed to be? 

I'm using the command

gsku gedit /etc/inittab.

Thanks again.

---

### Post by NullHead on 2008-11-17
What I would do is, remove GDM (gnome display manager) or kdm (kde display manager) and install XDM. 

It's more simplistic, but it won't drop to a terminal after you login. I'm not really sure what you want to do here. 

You can perform those actions through synaptic.

---

### Post by Qsl1pknotp on 2008-11-17
> **NullHead said:**
> What I would do is, remove GDM (gnome display manager) or kdm (kde display manager) and install XDM. 

It's more simplistic, but it won't drop to a terminal after you login. I'm not really sure what you want to do here. 

You can perform those actions through synaptic.

I think what I'm trying to say is that I want a terminal login. I'd like to keep GDM for now, because i'm just trying to get used to everything.  Thanks Though :D

---

### Post by sisco311 on 2008-11-17
you can disable gdm:
```
sudo update-rc.d gdm remove
```

to set gdm to start automatically again:
```
sudo update-rc.d gdm defaults 13 01
```

---

### Post by Qsl1pknotp on 2008-11-17
> **sisco311 said:**
> you can disable gdm:
```
sudo update-rc.d gdm remove
```

to set gdm to start automatically again:
```
sudo update-rc.d gdm defaults 13 01
```


Thanks.  This worked lol. Least I think it did.  Idk how to make it say resolved, but it is.  Thanks again :D

---

