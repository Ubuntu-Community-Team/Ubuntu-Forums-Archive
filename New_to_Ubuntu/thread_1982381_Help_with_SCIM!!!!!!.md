---
title: "Help with SCIM!!!!!!"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by Calvin123 on 2012-05-18
I am using Moon OS, it is a great OS, but I wanted to type Korean....I am not asking for instructions I am asking for someone to exsplain the instructions lol. "Configuration

If you installed ‘im-switch’ package above, it enables X to read ~/.xinput.d/default when launching X. This is to customize X input per user account, and make it consistent with Fedora or Redhat based Linux. Create ~/.xinput.d/default as following:

 export XMODIFIERS=”@im=SCIM”
 export GTK_IM_MODULE=”xim”
 export XIM_PROGRAM=”scim -d”
 export QT_IM_MODULE=”scim” 

KDE user, create ~/.kde/Autostart/scim as:

 #!/bin/sh
 scim -d 

and then set executable permission

 $ chmod a+x ~/.kde/Autostart/scim 

GNOME Users, Add below to ~/.gnome2/session-manual

 [Default]
 num_clients=1
 0,RestartStyleHint=3
 0,Priority=50
 0,RestartCommand=scim -d
 0,Program=scim 

Now restart X and you will see SCIM on taskbar if everything went on. Right click on the icon and choose SCIM setup. On menu “IMEngine > Global Setup”, select appropriate Korean keyboard you use. I use 2bul, and I guess others don’t behave correctly." So could some one explain this?

---

### Post by rai4shu2 on 2012-05-18
To start with, Moon OS uses Gnome so you can safely ignore the KDE part of the instructions. Aside from that, it looks a lot like using Debian Squeeze (so I don't know how helpful we can be around here).

I assume you have gedit for editing text files, and to restart X you press Ctrl-Alt-Backspace.

---

