---
title: "Nautilus doesn't work!"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by svenofix on 2008-04-22
I cannot even log on to my computer anymore do to problems that I am having. Two windows open displaying errors as is the following:


```
**Nautilus can't be used now, due to an unexpected error.**

Nautilus can't be used now, due to an unexpected error from Bonobo 
when attempting to register the file manager view server.
```


```
**The panel has encountered a fatal error**

The panel could not register with the bonobo-activation server 
(error code:3) and will exit. It may be automatically restarted.
```

---

### Post by billgoldberg on 2008-04-22
> **svenofix said:**
> I cannot even log on to my computer anymore do to problems that I am having. Two windows open displaying errors as is the following:


```
**Nautilus can't be used now, due to an unexpected error.**

Nautilus can't be used now, due to an unexpected error from Bonobo 
when attempting to register the file manager view server.
```


```
**The panel has encountered a fatal error**

The panel could not register with the bonobo-activation server 
(error code:3) and will exit. It may be automatically restarted.
```

Install another windows manager from the command line. Or reinstall it from the command line.

---

### Post by aktiwers on 2008-04-22
Look here howto install:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

Under "Playing Around".

You could try reinstall Gnome

---

### Post by svenofix on 2008-04-22
> **aktiwers said:**
> Look here howto install:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

Under "Playing Around".

You could try reinstall Gnome



Am I able to do that in the Ubuntu Recovery Mode? Since I'm not
able to get to a terminal, nor does Ubuntu boot into the login
screen, but directly into my account (I believe I made it that that
would happen).

---

### Post by aktiwers on 2008-04-22
Press CTRL+ALT+F2
It will take you to fullscreen Terminal.

Maybe you need to login again (remember that typing password here wont actually show what you type, just type anyways and hit ENTER).

Then start by killing GDM:
```
sudo /etc/init.d/gdm stop
```Then reinstall Gnome:
```
sudo apt-get --reinstall install ubuntu-desktop
```And try to startx again:
```
startx
```Or reboot:
```
sudo reboot
```

---

### Post by svenofix on 2008-04-22
I'm sorry, I feel dumb. Do I press ctrl-alt-f2 when I'm in Recov
Mode?

Also, when reinstalling Gnome, do I have to be connected to the internet?

---

### Post by aktiwers on 2008-04-22
Don't worry :)

Yes - or when it boots and gives you those errors, then press CTRL+ALT+F2.

Yes plug the PC into the internet, it will also update any packages in gnome, if you have any outdated.

---

### Post by svenofix on 2008-04-22
When I press ctrl-alt-f2 from Recov Mode, the whole screen goes
blank and just shows a blinking dash _ at the top-left corner. The
same thing happens when I press ctrl-alt-f3, f4, f5, and f6,
however when I press ctrl-alt-f1 the screen reverts back to Recov
Mode.

I'm thinking, couldn't I just use Recov Mode, since it already
looks like a terminal?

---

### Post by aktiwers on 2008-04-22
Yes I think you can.
Sorry I have never been in recov mode, but if it looks like the terminal, it must be it :)

Try do it from there

---

### Post by svenofix on 2008-04-22
lol, lucky! :p This is the second time I have to use Recov Mode.

Well, thanks for the help! Greatly appreciated!

---

### Post by aktiwers on 2008-04-22
I wish you luck. I have to go to bed now (its 5:43 here)..
If it does not work out, I will check back when I get up ;)

---

### Post by svenofix on 2008-04-23
Yup, nothing worked when I tried and experimented. :(

I think the problem lies in the file-server. :? Is it possible to download
a different one from the terminal.


EDIT: I had a friend who's very good with computers to check out my problem. He couldn't figure it
out, so I'm going to have to go for a complete reinstall. However is there some way I can access my 
Ubuntu Partition from Windows and backup my files?

---

### Post by Helge on 2008-09-10
I had similar problems to svenofix today. It turned out to be caused by an applet, which took all CPU. The applet was fast-user-switch-applet.

My untested theory is that this happened: the applet was installed on the user desktop by default. I then made two changes to the user account, which may confuser the applet:

1. Move the account from /home/usename to /localhome/username

2. Two changes to /etc/nsswitch.conf; 
  passwd files nis
  group files nis
instead of the default
  passwd compat
  group compat

The changes are to allow users to be authenticated by NIS (a.k.a. yellow pages), and mounted on /home, instead of /etc/passwd and /etc/group (which are used for local users)

At first, I sometimes got the bonobo-server message at login to Gnome. Always, the panes were unvisible, so it was hard to do things. When I killed the applet processes, the desktop immediately looked good, but there was a message about two applets, and wether I wanted to remove them from the panel config. I removed the fast-user-switch-applet.

No gnome-related file in my account had permission problems.

---

### Post by graben3 on 2008-09-10
> **svenofix said:**
> Yup, nothing worked when I tried and experimented. :(
 However is there some way I can access my 
Ubuntu Partition from Windows and backup my files?

To backup your files, try booting from the live CD

This CD will detect your windows and ubuntu partition so you can transfer files via the live environment to any partition you want

---

