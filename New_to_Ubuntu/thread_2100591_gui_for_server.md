---
title: "gui for server"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by anonu on 2013-01-02
hello,
 
i am absolutely new. i just installed ubuntu server i386. i reasilse it is command based. i was wondering if there is a gui which i could use to access web via browser to look up commands to use in terminal?
 
ideally i'd like to be able to launch it when necessary, till i get my bearings. right now i don't know how to navigate folders, so detailed answer would be highly appreciated. for eg.
 
my back ground is been on win since end dos era so i do understand some stuff.
 
thanks,
anon

---

### Post by mastablasta on 2013-01-02
have a look here: [https://help.ubuntu.com/community/ServerGUI](https://help.ubuntu.com/community/ServerGUI)
 
don't know what you want to do or accomplish but many users use **webmin** to manage server via web based gui. [http://www.webmin.com/index.html](http://www.webmin.com/index.html) not sure why the ubuntu site talks about lack of development of webmin since if you check the webmins changelog it is still being developed.
 
there is also zentyal.
 
zentyal also has community based OS with server GUI

---

### Post by Gone fishing on 2013-01-02
[http://webmin.com/](http://webmin.com/) The last version Webmin 1.610 was released in November. I find it very useful, somethings are so easy using Webmin. I would also suggest if you need to copy commands etc don't work on the server but on another box and ssh into the server then you can have a web browser open and copy commands etc.

You can of course add any GUI just from apt-get sudo install ubuntu-desktop to get Unity although if you did go that route I'd try something lighter say sudo apt-get install xubuntu-desktop.

---

### Post by anonu on 2013-01-02
thanks for your reply.
 
i want to set up a simple file server to centrally locate files and be able to access it and map drives from win machines. i want to set up users and groups etc.
 
i see all the answers, but i want to be able to see it on the same machine. i don't mind using the terminal, but right now i dont have a clue of any commands...

---

### Post by Gone fishing on 2013-01-02
If you sudo apt-get install xubuntu-desktop you will get the Xubuntu Desktop and you can install the server from there. I would think about Webmin it just makes life easier.

You might like to look at this too [http://www.server-world.info/en/note?os=Ubuntu_12.04&p=samba&f=2](http://www.server-world.info/en/note?os=Ubuntu_12.04&p=samba&f=2) (I would substitute vi command for nano or even gedit if you use the GUI)

---

### Post by Paqman on 2013-01-02
> **Gone fishing said:**
> 
You can of course add any GUI just from apt-get sudo install ubuntu-desktop to get Unity although if you did go that route I'd try something lighter say sudo apt-get install xubuntu-desktop.

+1 for Webmin, but if you wanted to install an actual desktop envrionment on a server I wouldn't use any of the *-desktop metapackages. They depend on all the desktop applications so will pull all those in too. Instead try to install just the core of those DEs, such as [xfce4]("apt:xfce4").

---

### Post by 3rdalbum on 2013-01-02
Ubuntu used to come with a small text-mode browser called w3m, that would work for looking at web pages of instructions on the same computer.

It's not preinstalled anymore but you can install it on your server with one command, and run it just by typing its name:

```
sudo apt-get install w3m
w3m
```

There's also another really good browser called Links2. It has a kind of GUI that can run in the terminal. With Links2 you can see images on pages even if you're using it from the terminal:

```
sudo apt-get install links2
links2 -g
```

---

### Post by lykwydchykyn on 2013-01-02
If you just want a simple desktop:
```

sudo apt-get install xorg lxde firefox

```

After that, type "startx" whenever you want to go into a GUI.  You can replace lxde with "xfce" or whatever desktop you like; same with the browser.

If you want a graphical login, install the "lightdm" package as well, otherwise you'll start in text mode until you type "startx".

---

### Post by irv on 2013-01-02
I remember when I setup my first server, I didn't know a lot of commands so I just installed a desktop (Ubuntu 10.04) and then installed [LAMP]("http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/") and [WEBMIN]("http://blog.johnso.org/2010/06/how-to-install-webmin-for-ubuntu-1004.html").
[ATTACH]229489[/ATTACH]
Then I maintain my server from my laptop via Remote Desktop.

---

### Post by mastablasta on 2013-01-04
> **anonu said:**
> thanks for your reply.
 
i want to set up a simple file server to centrally locate files and be able to access it and map drives from win machines. i want to set up users and groups etc.
 
i see all the answers, but i want to be able to see it on the same machine. i don't mind using the terminal, but right now i dont have a clue of any commands...
 
 
if you are only after a file server have a look at Open Media Vault: [http://www.openmediavault.org/](http://www.openmediavault.org/)
 
debian based... it's primary function is to do what you want to do.

---

