---
title: "Fluxbuntu questions, User and menu"
date: 2008-01-15
forum: Other OS Talk
---

### Post by jesrani on 2008-01-15
I have installed Fluxbuntu 7.10 on a P2, 800MHz machine with 128Mb RAM. It feels good. But I have some questions :
1) I made a user name during setup. Now I can use Sudo command and use the password to do administrative tasks. Can I create another user who can only Do browsing, check mail, print to a samba server and use applications. No adding or updating software and no sudo command usage to be allowed. How do I do this. Please give detailed instructions or links as I am a newbie
2) can I assign a password to the root user and then log in as root? in this case I can convert the user created earlier as the limited user. If not, what is the use of the root user?
3) All installed applications are not showing up in the Fluxbox menu even after using the "update-menus" command. I installed "Gnome CUPS manager" and can see that but I cant see "Gnome user manager" which I installed. I thought there was no spreadsheet, but it seems there is a spreadsheet "Gnumeric" installed but it does not show in menu. Can I have an "Add/remove" button like in Ubuntu?
4) How to change wallpaper and are there wall papers available??

---

### Post by K.Mandla on 2008-01-15
[LIST=1]
[*]I don't recall if Fluxbuntu has a user management panel, so you might have to do it manually -- but yes, you can add a restricted user account for just those things. The *useradd* command is useful for you there; try the [man pages for useradd]("http://linux.die.net/man/8/useradd") on how to use it from the command line.
[*]Yes. [It's never recommended]("https://help.ubuntu.com/community/RootSudo"), but that's for you to decide. *sudo -i* to get a root-access environment, then change the password with *passwd*. After that you should be able to log in as root.
[*]Some of them might have not have menu entries, which means you need to start them from the command line or manually add them to the menu. I've forgotten where the Fluxbox menus are, but I'm sure someone else will be able to help with that.
[*]And again it's been a while since I used Fluxbuntu so I don't recall if the wallpaper is handled by rox-filer or feh. Better wait for someone else to answer that one too.
[/LIST]

I'm also moving your post to Other OS Talk, since technically it's about another OS. ... :roll:

---

### Post by p_quarles on 2008-01-16
The Fluxbox root menu is located in /etc/X11/fluxbox/fluxbox-menu, but that's not the one you want to edit. The user menu (which by default calls the root menu) is located in ~/.fluxbox/menu. At first, this file might look scarier than it actually is. The entry syntax is simple. For Firefox:
```
[exec] (Firefox) {/usr/bin/firefox} </usr/share/icons/foo/bar/firefox.png>
```
The first entry defines the type of menu item, the second is the text displayed in the menu, the third is the path to the executable, and last is the icon, if you want one. 

Wallpapers in Fluxbox are pretty easy. Regardless of which wallpaper handler Fluxbuntu comes with, it can be invoked with the "fbsetbg" command, like so:
```
fbsetbg -f /path/to/wallpaper.png
```

---

### Post by K.Mandla on 2008-01-17
Thanks, p_quarles. I need to brush up on my Fluxbox. :-k

---

### Post by jesrani on 2008-01-20
Thanks will try out the options

---

