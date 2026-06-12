---
title: "Ubuntu Server. Am I an idiot? I only see CLI..."
date: 2008-07-05
forum: New to Ubuntu
---

### Post by Roasted on 2008-07-05
I just installed Ubuntu Server (Hardy Heron) on my laptop to test it out. I only see CLI, even after logging in and such. I saw screenshots of it and I know there's a GUI to it... right? 

What did I do wrong, or forget to do?

---

### Post by Barrucadu on 2008-07-05
Ubuntu has a GUI, Ubuntu Server does not. This is because on a server, a GUI is usually useless as almost all server applications can eb entirely managed through the CLI.

---

### Post by hyper_ch on 2008-07-05
what do you want to have a gui on a server for?

---

### Post by Roasted on 2008-07-05
I'm just used to 2003 server by Windows, where I can see on the gui active directory and all of that. I just expected Ubuntu server to be similar.

Guess not. :(

---

### Post by Barrucadu on 2008-07-05
You'll find Windows Server 2003 is the odd one out; No other server operating systems have a GUI.

---

### Post by avtolle on 2008-07-05
Well, it is your computer, and if you want a GUI, take a look at [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) for some ideas of how you might proceed to get one. HTH.

---

### Post by Roasted on 2008-07-05
So... how exactly can you easily navigate to a certain user in active directory to make necessary changes on the fly?

To me, it just makes sense. :confused:

---

### Post by Troll_the_Great on 2008-07-05
You can install any GUI.For example for Gnome (my favorite):
```
sudo aptitude install ubuntu-desktop
```
For KDE:
```
sudo aptitude install kubuntu-desktop
```
For X-Face:
```
sudo aptitude install xubuntu-desktop
```
Did this helped?

---

### Post by Roasted on 2008-07-05
I installed Gnome.
Rebooted.
Logged in.
Still CLI...

---

### Post by Troll_the_Great on 2008-07-05
Type ```
gdm
``` and tell me what happens.

---

### Post by Roasted on 2008-07-05
It says not installed. You can install it by doing sudo apt-get install gdm.

I typed sudo apt-get install gdm.

gdm package not found.

lol?

(Yes I'm online)

---

### Post by Troll_the_Great on 2008-07-05
This is indeed weird...Are you sure you typed it correctly?

---

### Post by Troll_the_Great on 2008-07-05
Try this:
Type ```
gksu synaptic
``` and see if you can find gnome-desktop or gdm (or something like that) there.

---

### Post by llamakc on 2008-07-05
> **Troll_the_Great said:**
> Try this:
Type ```
gksu synaptic
``` and see if you can find gnome-desktop or gdm (or something like that) there.

Synaptic is a GUI program, which the OP doesn't have. Therefore this suggestion won't work.

OP: You have choices. You may still install gdm (the login manager) or you may just start Gnome from the command line.

If you wish to install GDM, please post the contents of your /etc/apt/sources.list file. The package "gdm" is in the main repository so you should see it just fine.

You may be mistyping something so just in case try again:

```

sudo apt-get install gdm

```

And then 

```

sudo /etc/init.d/gdm start

```

The program 'gdm' must be run with sudo or as root, and the init script in /etc/init.d/ will start it successfully for you if you have installed it.

Second: if you just want to fire up Gnome from the command line, do this:

```

cd 

```

Now you have just changed directories to your home directory /home/USERNAME.
Next we'll open an editor and edit a file.

```

nano .xinitrc

```

Place the following in the .xinitrc file.

```

exec gnome-session

```

And then from the commandline type:

```

startx

```

You will need the package "xinit" installed to use startx.

---

### Post by hyper_ch on 2008-07-06
> **Roasted said:**
> So... how exactly can you easily navigate to a certain user in active directory to make necessary changes on the fly?

To me, it just makes sense. :confused:

what do you want to do?

---

### Post by sayakb on 2008-07-06
```
startx
```
Should start X.

---

### Post by aktiwers on 2008-07-06
```
sudo apt-get install ubuntu-desktop
``````
startx
```Should be all right? :D

---

