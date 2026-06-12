---
title: "messenger"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by phanipalagummi on 2008-05-31
How do i chat with my friends in yahoo using gaim ,is it i can do voice chat,
how do i add the buddy list,please give me a detail explanation

---

### Post by phanipalagummi on 2008-05-31
i typed this command after installing ymessenger_1.0.4_1.........

phani@phani-desktop:~$ sudo dpkg -i/phani/Desktop/ymessenger_1.0.4_1_i386.deb

and  i got error saying


dpkg: unknown option -/

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

---

### Post by shifty_powers on 2008-05-31
sudo dpkg -i/phani/Desktop/ymessenger_1.0.4_1_i386.deb

should be

sudo dpkg -i /phani/Desktop/ymessenger_1.0.4_1_i386.deb

and do you mean pidgin? gaim got renamed a while ago...

---

### Post by shifty_powers on 2008-05-31
or, you could just go to the *.deb in nautlius, right click and install with gdebi...

---

### Post by 505 on 2008-05-31
In the command above you forgot a space after -i, it is:
```
sudo dpkg -i /phani/Desktop/ymessenger_1.0.4_1_i386.deb
```
In Pidgin you can add Yahoo by going to Accounts->Manage->New and select Yahoo as protocol. Add your login name (under "screen name"), your password and your friendly name under "alias". Click save and you should be able to get online. However, Pidgin does not support voice chat, only text chat.

---

### Post by Troll_the_Great on 2008-05-31
Try Kopete, is better then pidgin and is almost as yahoo.It supports web-cam so and I thing the voice chat works also.Just install it from synaptic and give it a go;) 
Btw, if you want voice chat why don't you use Skype?It runs natively on Linux and it works excellent.

---

### Post by Xerp on 2008-05-31
I'd second using Pidgin. Whilst it is pretty easy to use, they do also have help available:

[http://developer.pidgin.im/wiki/FAQ](http://developer.pidgin.im/wiki/FAQ)

---

### Post by Sef on 2008-05-31
Also there is Gyachi.  It is a yahoo clone that has voice.

I'll post the link, if i can find it.

---

