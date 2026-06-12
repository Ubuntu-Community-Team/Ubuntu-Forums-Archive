---
title: "Ubuntu server with GUI?"
date: 2015-01-30
forum: New to Ubuntu
---

### Post by Dave.B on 2015-01-30
Hello 
i am being given a server that a friend had and am wondering if there is a ubuntu server that comes with a GUI?

i an somewhat comfortable with ubuntu desktop and am wanting to try server.

The specs on the server are:
Supermicro Server 
2x 3.33GHz Xeon 5260 Dual Core
4GB 
160GB 
DVD 
2xGIGABIT  

thank you for the input

---

### Post by grahammechanical on 2015-01-30
As I understand things, the Ubuntu desktop edition and the Ubuntu server edition have the same software repositories. That means that I can install server application on my Ubuntu desktop machine. So, I see no reason why you should not be able to install desktop applications, even Ubuntu desktop, on a server machine.

The machine will need a graphic adapter. They are not always required for servers. Especially if the machine is accessed over a network.

Regards.

---

### Post by Bucky Ball on 2015-01-30
DO NOT install ubuntu-desktop. You may as well install Ubuntu. You only want a desktop _environment_. For a server, you are after something lightweight. Try xfce or lxde. You can install either with:

```
sudo apt-get install xfce4 
```

Replace 'xfce4' with 'lxde' if you want to go for that one. There are others. Have a look about, but they're two of the lightest. Installing *buntu-desktop anything will install ALL default packages, apps, dependencies, the lot, most of which you don't, and will never, need on a server.

> **grahammechanical said:**
> 
The machine will need a graphic adapter. They are not always required for servers. Especially if the machine is accessed over a network.

Something to be mindful of. ;)

---

### Post by Dave.B on 2015-01-30
The machine will need a graphic adapter. They are not always required for servers. Especially if the machine is accessed over a network.



the server has 
Integrated XGI Z9S Video Card with 32MB
built in so i am covered there

---

### Post by steeldriver on 2015-01-30
If the server does have physical display capabilities, then about the most minimal setup I have found is lxde-**core **without any of the recommended packages

```

[FONT=courier new]sudo apt-get install **--no-install-recommends** lxde-core
[/FONT]
```[FONT=courier new]
[/FONT] If it doesn't, then you could either use one of the web-based server management tools, or install a minimal GUI plus a vncserver that you would then be able to access via a remote vncviewer

---

### Post by oldos2er on 2015-01-30
You don't even need a desktop environment. Running a server with X (the graphics subsystem software) and a window manager e.g. i3 would suffice.

---

### Post by HermanAB on 2015-01-30
Howdy,

The trick with managing a server is to do it remotely over SSH from another machine.  SSH provides an X client.  Therefore, you can run graphical programs on a server remotely on your own desktop, without actually having X running on the server.

Ferinstance:
$ ssh -X -C -c arcfour user@server 'gedit filename'

---

### Post by nerdtron on 2015-01-31
My question would be why need a GUI? Do you have a program that need to run on a GUI server?

I'd like to ask since even if you install a GUI, you wouldn't accomplish much. Almost all settings will still need to be text files edited by hand. SSH and the command line interface can give you all you need plus uses low resources and lower bandwidth.

---

### Post by HermanAB on 2015-01-31
"low resources and lower bandwidth"
...and much reduced attack surface.

---

### Post by Dave.B on 2015-01-31
i am new to server and would feel better running gui at first

---

### Post by mörgæs on 2015-02-01
> **Dave.B said:**
> 

the server has 
Integrated XGI Z9S Video Card with 32MB
built in so i am covered there

I wouldn't say so. These cards are very weak and might be difficult to get to work.

Don't hesitate to post if something goes wrong.

---

