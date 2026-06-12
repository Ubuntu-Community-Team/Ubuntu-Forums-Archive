---
title: "Autostarting a program as sudo in KDE"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by gizmobay on 2008-07-03
I have my fax hooked to my computer and for some reason the modem device always changes to root so I just setup my sudoers file to allow me to run the command as root while being a user. The program is efax-gtk and the command I use is sudo /usr/bin/efax-gtk -rs. I created a link to the application and entered the above command; I then moved this to KDE Auto Start. This works but the only problem is that on login the efax-gtk application bounces in the tray for about a minute after login. I was wondering if there's a way to fix this.

---

### Post by hakko on 2008-07-03
Guessing....Check the permissions on the efax-gtk?

Also:
> 
To Autostart a program in KDE you simply need to put a symbolic link to the executable file in the Autostart directory. In most cases this is located at:

   ~/.kde/Autostart/

If wanted to have xbindkeys start automatically when KDE started then I would locate the the executable file for xbindkeys. In my installization it is located at:

   /usr/bin/xbindkeys

All you have to do is place a symbolic link in the Autostart directory:

   ln -s /usr/bin/xbindkeys ~/.kde/Autostart/xbindlink
[http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)


---

### Post by txcrackers on 2008-07-03
Instead of trying to work *around* the permissions problem, I'd suggest try to work *with* them - it turns out much simpler.

Firstly, what are the permissions for the modem device? */dev/modem* will most likely be a link to another device and that's the one we're interested in. I'm guessing it looks like my serial port:
```
crw-rw---- 1 root dialout 4, 64 2008-07-03 08:45 /dev/ttyS0
```

So, pull up the User manager (through system settings) and click on the "Groups" tab, then select the checkbox "Show system groups." Select the [b]dialout[b/] group and add your user to that group. Log out, log in and you should be good to go (and remove the "sudo" from your auto-start - you shouldn't need it anymore).

---

### Post by gizmobay on 2008-07-03
Thanks for the help. I'm using martian_modem. After reading your post further, I see I can set a username when starting martian_modem so I set this to dialout and then just added my username to the group and efax-gtk works without having to do an end around with sudo.

---

### Post by txcrackers on 2008-07-03
Not a problem... please mark the thread as "solved" if you're happy with the solution... ;)

---

