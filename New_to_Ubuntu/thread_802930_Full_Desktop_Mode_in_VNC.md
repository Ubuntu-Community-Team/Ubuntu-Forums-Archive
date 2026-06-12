---
title: "Full Desktop Mode in VNC?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by hankbeblazin on 2008-05-21
i'm totally new to linux (i have ubuntu 8.04)and im learning as i go and it's pretty difficult but i figured i'd ask this question. i was able to log on to my linux machine using tightvncviewer on windows xp. 

maybe this is typical but i know when i logged on to my windows machine from linux i got the full desktop, everything. 

when i logged into my linux machine from windows i didnt have any taskbar or anything other than a blank grey screen that i can open the terminal in.

my question is...can i get the full desktop when remote connected to linux? thanks inadvance

---

### Post by civic_si on 2008-05-21
I get the full desktop of mine when I log into it. The Ubuntu machine needs to be loggid into the desktop in order to work. Not sure if that will fix your problem but I thought I would share.

---

### Post by hankbeblazin on 2008-05-21
yeah i am logged into the desktop when i do remote connect

i don't know if this matters but i used xvnc4viewer for the vnc viewer on the linux machine. if so should i use a different vnc to view the full desktop?

thanks for the reply

---

### Post by jrusso2 on 2008-05-21
> **hankbeblazin said:**
> yeah i am logged into the desktop when i do remote connect

i don't know if this matters but i used xvnc4viewer for the vnc viewer on the linux machine. if so should i use a different vnc to view the full desktop?

thanks for the reply

There is a full desktop option in the configuration settings.  When you launch VNC it brings up a box configuration settings you put in the IP address there is a button on the bar on the bottom that has options. On the misc tab is the full screen mode check box

---

### Post by ryanhaigh on 2008-05-21
Sounds as though you have installed a separate vnc server on your linux machine. Generally these servers don't connect to your currently running session but start another one. 

Ubuntu does however have a vnc server application that will allow you to connect to the current sessiom, its called vino and is installed by default. To configure vino just go to system>preferences>remote desktop. There is a lot of useful information on using VNC in ubuntu here: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

In that document the default vnc servers section refers to vino and the integrated vnc server, if this is not the way you want to go the document also has configuration information for the other vnc servers.

---

### Post by hankbeblazin on 2008-05-22
> **ryanhaigh said:**
> Sounds as though you have installed a separate vnc server on your linux machine. Generally these servers don't connect to your currently running session but start another one. 

Ubuntu does however have a vnc server application that will allow you to connect to the current sessiom, its called vino and is installed by default. To configure vino just go to system>preferences>remote desktop. There is a lot of useful information on using VNC in ubuntu here: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

In that document the default vnc servers section refers to vino and the integrated vnc server, if this is not the way you want to go the document also has configuration information for the other vnc servers.

ok i went to system>preferences>remotedesktop 

it says "users can view your desktop using vncviewer localhost:0"

does that mean i put vncviewer localhost:0(then my port) into the tightvnc to view it. i tried that and it said it couldnt connect. 

i feel so retarded that i don't know this stuff lol sorry for the idiotic questions. i appreciate all the help thought

---

### Post by ryanhaigh on 2008-05-22
Localhost is how the machine refers to itself. You will need to use the ip address of the ubuntu machine, you wont need to input a port number. Eg. 10.1.1.1:0

---

### Post by hankbeblazin on 2008-05-22
> **ryanhaigh said:**
> Localhost is how the machine refers to itself. You will need to use the ip address of the ubuntu machine, you wont need to input a port number. Eg. 10.1.1.1:0

ok so here's what i did. i deleted tightvnc because that says it opens a second session instead of the current one. i installed vnc viewer on the windows machine

it still wont connect using my ip address and :0 like it says in the remote desktop preferences

it will connect using henry-desktop:2 but only shows the grey box with the Terminal only. no taskbar or menus

i'm really lost here this whole linux thing is crazy haha. help please

---

### Post by ryanhaigh on 2008-05-22
Did you install a vnc server on your ubuntu machine? You may have to uninstall that and possibly even restart before you can access the built-in vino server at adddress:0.

---

### Post by hankbeblazin on 2008-05-22
yeah my machine will access :1 and :2 but not :0

i know thats the problem. i deleted the other files for :1 :2 but it seems to want to go back to that. 

i don't get why it won't do :0 i've been at this for 3-4 hours and its driving me nuts.

whenever i run tightvnc (in the terminal. it'd be nice if it had a GUI like in windows it would make this 100x easier) on the linux box it says bad command and then assigns me :1 or :2  which seems odd to me.

---

### Post by ryanhaigh on 2008-05-22
The problem is that you are running multiple VNC servers. I don't know what you mean by deleting the files but that is not the way to uninstall the vnc server. From the sounds of it you have installed tighvncserver so to remove it just open the terminal and do:```
sudo apt-get remove tightvncserver
```. After doing that restart your system and login. If you have enabled remote connections in system>prefs>remote desktop (which is a different server to the tightvnc server) you should then be able to connect to ip:0 or hostname:0.

---

### Post by hankbeblazin on 2008-05-22
i figured it out. i had to run x11vnc to get the full desktop. wow that took a long time to figure out. at least i'll know for next time. Thanks alot Ray you were awesome.

---

