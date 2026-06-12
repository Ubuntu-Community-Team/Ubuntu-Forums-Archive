---
title: "Fresh Install Update?"
date: 2005-02-10
forum: Repositories &amp; Backports
---

### Post by Wuzzbent on 2005-02-10
Hey All,
  I just installed Ubunta and when I did,  as it's installing, it asks you if you want to do a web-update before the install is complete, well I guess the site was down and It continued without doing a system/package update, I was wondering how I can recall that update now that the update site is back up?

Thanks -

---

### Post by mendicant on 2005-02-10
Just use aptitude or synaptic and get the updated packages.  From the command line:

% sudo xterm
% # in the new xterm
% aptitude update
% aptitude dist-upgrade

Running plain aptitude will bring up a curses GUI, and synaptic is a GTK GUI.

---

### Post by lao_V on 2005-02-10
Another way would be to (from terminal):
  
   ```
sudo apt-get update (to update your current distro)
 sudo apt-get dist-upgrage (to upgrade your distro to 5.04 Hoary - you will need to change your /etc/apt/sources.list)
```

---

### Post by mendicant on 2005-02-10
I'd really suggest using aptitude instead of apt-get.  It has a similar command line interface, but is just better:

[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

I really like the automatic dependency tracking, the searching (file:///usr/share/doc/aptitude/html/en/ch02s03.html)  and the display of suggested packages (in the curses GUI).

---

### Post by lao_V on 2005-02-10
[QUOTE=mendicant]I'd really suggest using aptitude instead of apt-get.  It has a similar command line interface, but is just better:

[http://lists.debian.org/debian-user/2004/04/msg11344.html](http://lists.debian.org/debian-user/2004/04/msg11344.html)

I really like the automatic dependency tracking, the searching (file:///usr/share/doc/aptitude/html/en/ch02s03.html)  and the display of suggested packages (in the curses GUI).[/QUOTE]
 Thanks mendicant, that's quite useful to know!

---

