---
title: "[SOLVED] System command"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by phil66 on 2008-05-26
I am wanting to run the command "/sbin/shutdown now -h" from the run command menu

When I run it from Konsole I have to add sudo for root and then add my password before it will work

What do I need to add before /sbin in the run command so this will run as root

Thanks for the help
Ray

---

### Post by Joeb454 on 2008-05-26
I'm not sure exactly what you want to do, but to shutdown you could run ```
sudo shutdown -h now
```

---

### Post by phil66 on 2008-05-26
> **Joeb454 said:**
> I'm not sure exactly what you want to do, but to shutdown you could run ```
sudo shutdown -h now
```

I have cairo-dock and I am trying to add a launcher which will shutdown computer with the command /sbin/shutdown now -h or some other command

sudo /sbin/shutdown now -h works from the Konsole but not from the run command line or the dock launcher but requires a password in konsole

This has to be a command from root

If I use sudo /shutdown now -h I get  /shutdown command not found. The shutdown exe is found in file system..sbin

What I need is to be able to tell the command I am root before it executes. ~ ahead of sbin does not work

Thanks
Ray

---

### Post by NikoC on 2008-05-26
no need to add the '/', just
sudo shutdown -h now

however, in a graphic environment such as kde use
gksudo shutdown -h now

This way you will get a popup window asking for a pass...

Edit: just ignore my post, sorry, it doesn't to the trick!

---

### Post by Joeb454 on 2008-05-26
That's because in KDE you have to use ```
kdesu
``` ;) I think you can edit the sudoers file to tell it you don't need to enter the password for shutdown commands, though it's easy to mess this up and end up with a broken sudo, and I don't know how to edit it :p

---

### Post by phil66 on 2008-05-27
Thanks for the replies

Only partially successful using the commands

The sudoers file has a commented entry for password but says to use visudo to edit

New to this editor will have to research before trying

Thanks again for the help

---

### Post by sayakb on 2008-05-27
Ah well, is there a way to shutdown without using sudo? I've been using OpenBox and I need a panel launcher that would shutdown/reboot.

---

### Post by Joeb454 on 2008-05-27
Not that I know of. Editing ```
sudo visudo
``` is the only way to work around this - because then you can use sudo, but it will not require a password to work.

As I mentioned previously - this can completely break sudo if you're not careful :)

---

### Post by urukrama on 2008-05-27
See [this section]("http://urukrama.wordpress.com/openbox-guide/#shutdown") of my Openbox guide. That should answer your question. It tells you how to shutdown or reboot without administrative priviges.

---

