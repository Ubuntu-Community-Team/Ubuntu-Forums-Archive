---
title: "IP Changing Program wireless"
date: 2006-03-19
forum: Programming Talk
---

### Post by ninocass on 2006-03-19
HI all

At university we play some networked games via AD-HOC, i found setting the IP etc up via the gnome-network-manager was hit and miss and toook really long (3 minutes in some cases!!!)  So i went about developing a small program to help me out.  Ive never done any programing in linux (gambas) but im quite good with java/VB so i have an idea what im at.

Basically the program edit's the values in the /etc/networking/interfaces file allowing the user to set IP, netmask and gateway as well as showing information on networks in the area.

As i mentioned this was mainly a small program to help with the uni "ad-hoc-ing" and to see what linux programming is like

My question is should i further advance the program to inculde WEP encryption and release it to the public?

are there any features you would like to see in such a program?

Thanks

Nino

---

### Post by FryerFox on 2006-03-20
I would hold off on that for now. 

I myself had began writing something in Python to save WEP keys and autoassociate when particular wireless networks come into range and execute whatever scripts were chosen (e.g. change the desktop background, play a sound).

I started to add polish by creating a GUI (with glade), and exploring the debian packaging format (.deb) for redistribution. Unfortunately, it was at this point that I discovered two other projects that were doing the same thing (to a large part)

[http://gtkwifi.sourceforge.net/]("http://gtkwifi.sourceforge.net/")
[http://www.gnome.org/projects/NetworkManager/]("http://www.gnome.org/projects/NetworkManager/")

If I do anything in that regard now, I might just try to help out one of these projects.

Keep learning the in's and out's of programming in Linux, though, since there are many projects out there that need programmer help, or it might be the next project you write that suddenly gets popular.

P.S. I'm wondering why you chose Gambas - I know it's got that familiar VB feel, but why didn't you try something sleeker and sexier like Python?

---

### Post by ninocass on 2006-03-20
hi

I updated the program a bit to include an integrated terminal and the program refreshes every 30 seconds finding new networks

[img]http://nino.fruitvalestudios.com/gallery/albums/userpics/10001/normal_prog3.png[/img]

i use the GTKwifi program to find my networks but it lacks the ability to assign IP :( i tried network manager but it dosent like fluxbox and getting it installed was a pain lol

I used gambas as it seemd the most "friendly" lol plus it reminds me of VB as you say :D  ill have to habe a look into Python etc, we've just started an advanced programming module at uni that covers GUI's so i might have a look into java as well

Nino

---

