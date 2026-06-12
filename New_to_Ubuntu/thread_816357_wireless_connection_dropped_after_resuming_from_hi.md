---
title: "wireless connection dropped after resuming from hibernate"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Stefanie on 2008-06-02
My wireless connection is dropped when I resume from hibernate. The icon in de notification area is gone, killall gnome-panel doesn't help and I really can't find a way to get things working again, except for ctrl-alt-backspace.
Is there a fix for this? I'm using ubunu hardy.

---

### Post by Inxsible on 2008-06-02
> **Stefanie said:**
> My wireless connection is dropped when I resume from hibernate. The icon in de notification area is gone, killall gnome-panel doesn't help and I really can't find a way to get things working again, except for ctrl-alt-backspace.
Is there a fix for this? I'm using ubunu hardy.
Nope...no fixes that I know of. I have seen that bug since Gutsy (Hibernate just didn't work for me in Feisty)

---

### Post by Stefanie on 2008-06-02
Do you know if ```
sudo /etc/init.d/networking restart 
```

works ? I've never tried it (i always forget the command, and the problem is that you can't look it up on the internet if your connection isn't working :-) but i wrote it on a post-it now.)

---

### Post by Stefanie on 2008-06-02
or is there another command which restarts the network manager? (sorry for the double post)

---

### Post by cenwesi on 2008-06-19
I too am having this problem and just did a google search and come up with this link. 

[http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/](http://lilserenity.wordpress.com/2007/10/31/fix-ubuntu-dropping-wireless-on-suspendhibernate-resume/)

---

### Post by sdennie on 2008-06-19
You can restart network manager with:

```

sudo /etc/dbus-1/event.d/25NetworkManager restart
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher restart

```

I don't know if it will help, but, that's the way to do it.

If that doesn't work, you could also try:

```

pkill nm-applet

```

If it doesn't restart:

```

nm-applet

```

---

### Post by Stefanie on 2008-06-20
thanks, i'll try this.

---

