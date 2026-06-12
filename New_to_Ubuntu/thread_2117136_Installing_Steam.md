---
title: "Installing Steam"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by fractalman on 2013-02-17
Ubuntu 12.04 (lts) 32 bit, 2.5g ram

Ok, I've been trying to install steam but it doesn't want to have any of it.  i tried through software center but it won't install.  It asks me to make an ubuntu simple sign in account, which i do then it emails me a verification code but when i enter the code nothing happens, it just stays on the same screen,  i have tried running software center from terminal as root as well but get the same glitch

I tried downloading steam as a deb package from their site.  If i use software center to install the file cannot be opened, using software center as root makes no difference

if i try gdebi package installer but it throws out the message that the file might be corrupted or i don't have the correct permisions.  i get the same as root too

if i try sudo dpkg -i steam_latest.deb from a terminal, it starts to install then throws up an error message

```

phi@No47:~/Downloads$ sudo dpkg -i steam_latest.deb
[sudo] password for phi: 
(Reading database ... 223683 files and directories currently installed.)
Unpacking steam (from steam_latest.deb) ...
dpkg-deb (subprocess): short read on buffer copy for failed to write to pipe in copy
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing steam_latest.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/steam/bootstraplinux_ubuntu12_32.tar.xz'
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 steam_latest.deb
phi@No47:~/Downloads$ 

```I have tried  downloading another copy but got the same with all attempts.

do i need to do something else that i'm missing to get this to install or is there a known bug with steam?  i have had a good google but cannot for the life of me find anything to help me out.

---

### Post by fractalman on 2013-02-19
Bump... any ideas?  still had no luck getting steam to install

---

### Post by Kopkins on 2013-02-19
I went here
[http://store.steampowered.com/about/](http://store.steampowered.com/about/)
And clicked install Steam and it downloaded the .deb and I clicked it from downloads and it opened software center and installed quickly after I entered my password. 

If you don't mind the effort try installing it on a VM to see if it is just your system or if something else is going on.

Best of luck, and sorry if I'm no help.
Kopkins

---

### Post by MrKaliman on 2013-02-19
Install it using software center... Works like a charm!

---

### Post by fractalman on 2013-02-20
Thanks for the replies,  i downloaded the deb package yet again but this time it has installed properly, i can only assume the other packages were corrupted,  weird!

---

### Post by Kopkins on 2013-02-20
Awesome. You can mark your thread solved by using the thread tools dropdown above your first post on the right.

Kopkins

---

