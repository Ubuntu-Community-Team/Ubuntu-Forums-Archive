---
title: "any advice on using ubuntu for a server"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by 720iD on 2008-09-03
i am thinking of a setting up server at home i have little knowledge of running a server, except for what i have learned from managing my shared hostingn this will be my first server. i am thinking of using ubuntu as my server software. i am sure other people have done this and i am wondering if anyone can give me some pointers. i have used ubuntu in the past as a desktop os but i have not used the server version.

---

### Post by perlluver on 2008-09-03
> **720iD said:**
> i am thinking of a setting up server at home i have little knowledge of running a server, except for what i have learned from managing my shared hostingn this will be my first server. i am thinking of using ubuntu as my server software. i am sure other people have done this and i am wondering if anyone can give me some pointers. i have used ubuntu in the past as a desktop os but i have not used the server version.

The server version is just a Command Line Interface, no GUI.  So you have to know how to operate it as such.  If you are not afraid of the Command Line, you will be fine.  Otherwise, you may want to mess around with the Server, under Ubuntu with a GUI for awhile, and get up to speed on how it is run.  You can install a LAMP server with [CODE]sudo tasksel install lamp-server.  That will give you Apache, MySQL, and PHP.  You can also install NFS or Samba, depending on what you want the Server to do.

---

### Post by tuxxy on 2008-09-03
You can either install the server version or install normal Ubuntu and add/remove the required packages, which could be easier for you.

I think you would benefit reading the [server guide ]("https://help.ubuntu.com/8.04/serverguide/C/index.html")

---

### Post by iansane on 2008-09-03
I found webmin and phpmyadmin to be good web based management tools for some of the configuring of the webserver and database. You can use it whether running server or the server installed on desktop ubuntu. You'll have to access it from a remote computer if running the non gui server I think. That's what I did anyway.

You can also install gnome and desktop on the server edition but it kinda makes it the same as installing apache and mysql and php (LAMP) on the desktop edition.

---

### Post by bodhi.zazen on 2008-09-03
Install the server edition, learn to use ssh + screen :twisted:

The web tools are nice as well, but you should understand the system under the hood a little as well.

---

### Post by 720iD on 2008-09-04
thanks all for the info, this has been a big help. i never thought of using desktop ubuntu and installing the required sever packages. i think this will be the way for me. although there is a lot more that i need to investigate.

---

### Post by Ocelaris on 2008-09-17
I just installed the server version for the first time after having done the desktop tens of times... but never stuck with it. I would definetly do all the tasks required once on a gui before attempting on a CLI only machine. I would've given up long ago if I hadn't had that crutch to rely on. It's all about doing it over and over and over again until you get some of it...

---

