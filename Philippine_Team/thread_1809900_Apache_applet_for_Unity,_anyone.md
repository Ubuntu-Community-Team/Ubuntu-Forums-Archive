---
title: "Apache applet for Unity, anyone?"
date: 2011-07-22
forum: Philippine Team
---

### Post by arscariosus on 2011-07-22
I've been playing with Apache yesterday, and I'm still a noob, but I managed to do what I'm planning to do by reading the config files.

I noticed that Apache runs at boot, and I cannot find it at the startup applications. And besides, I find it a bit lengthy to invoke commands like this  

```

/etc/init.d/apache stop/start/restart

```

Are there any applets for Unity or a sort of a lightweight app where I could quickly turn Apache on/off? I could add an alias at the bashrc but what I really prefer is an applet for the Unity panel :)

Thanks.

---

### Post by Samhain13 on 2011-07-24
A shorter, more intuitive version would be:
```
apache2ctl start|stop|restart
```

Removing apache2 from start-up apps:
[http://ubuntuforums.org/showpost.php?p=8630438&postcount=2](http://ubuntuforums.org/showpost.php?p=8630438&postcount=2)

A GUI would be helpful, too, I guess.

---

### Post by arscariosus on 2011-07-24
Thanks!

```

sudo chkconfig apache2 off

```

doesn't seem to work though :(

---

### Post by daison3 on 2011-07-24
Im using Xampp for almost 3years to develop websites and to design, and just a 2weeks here in Ubuntu, better to use xampp than to manually configure the apache if you're developing just for websites. If you have a server, that might do to manually secure the website ^_^



use xampp, and chmod the /opt/[COLOR=Green]XAMPPdir to 777

[COLOR=Black]go to its folder and start the .sh file[/COLOR]



[/COLOR]

---

### Post by Samhain13 on 2011-07-31
> **arscariosus said:**
> doesn't seem to work though :(

Bummer. I tried it and it did here. Sorry, I can't help more. :(

---

