---
title: "How to automatically startup a clean X-session"
date: 2009-12-02
forum: Programming Talk
---

### Post by SwedishWings on 2009-12-02
Hi folks,

been scratching my heads for a some hours, and hope someone can help. 

I'm building an information kiosk (based on Ubuntu 9.04). The idea is that when the customer plugs in the power, it will boot up and start a clean X-session and run a my application. Of course, i don't want Gnome or any other desktop apps to be run.

I've been trying to understand how to best do this. I know that gdm gives me automatic login which is nice, but i can't figure how to make it just start X and my app.

Is there a smarter way to do this, than using gdm?

Any pointers are most welcome!

/Mike

---

### Post by Zugzwang on 2009-12-02
Maybe it suffices to construct a custom .xinitrc-file for the user you automatically log in with?

[http://wiki.archlinux.org/index.php/Xinitrc](http://wiki.archlinux.org/index.php/Xinitrc)

---

### Post by SwedishWings on 2009-12-02
After some more digging i found a very easy way:

Remove gdm and usplash (usplash is not vital to remove)
```
$ sudo apt-get remove gdm usplash 
```

Install mingetty
```
$ sudo apt-get install mingetty
```

Edit /etc/event.d/tty1 and replace 
```
exec /sbin/getty 38400 tty1
```
with
```
exec /sbin/mingetty --autologin <user-name> tty1
```

Finally edit ~/.bashrc and add 

```
exec xinit <full path to application>
```

Thats it!

---

