---
title: "Server Edition GUI query"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by hungryOrb on 2008-05-26
Hihi :]
Installed the server edition earlier, and when loaded, I got a CLI, with no hint of GUI. Was wondering if someone could set me straight to install the rest of a 'standard' install to give me the (much needed!) gui? 
Thanks for considering!
Orb

---

### Post by cwgatling on 2008-05-26
It depends on whether you need just X server or a full desktop environment. If it's a server, you won't want to waste resources with a Gnome/KDE/XFCE.
Just X:

```
sudo apt-get install xserver-xorg
```

Gnome:

```
sudo apt-get install ubuntu-desktop
```

If you wanted a light version with some GUI features (e.g. text editor, browser), you'd install X, then Gedit, firefox etc.

---

### Post by iaculallad on 2008-05-26
Or you could just use:

Code:

> sudo apt-get install kdebase kdm x-window-system-core

to get away with extra packages.

---

### Post by hungryOrb on 2008-05-26
Thankyou cwgatling!
I think both of those are a great solution. I was kindof hoping that someone would suggest the normal GUI for ubuntu server edition. The server can handle any GUI I'm sure, it's pretty overpowered for its impending task of serving a page.
Does ubuntu server normally come with GUI? I'm pretty sure I didn't skip anything.. ;D and when given the option to select install options, I selected everything, but don't remember seeing any desktop available.. :]
Thanks for help ;]

---

### Post by cwgatling on 2008-05-26
The server edition doesn't come with a GUI. To make it into a normal desktop install, it would be the second command (ubuntu-desktop), but this installs far more than you'd need on a server (games, IM, email client etc).

---

### Post by hungryOrb on 2008-05-26
> **cwgatling said:**
> The server edition doesn't come with a GUI. To make it into a normal desktop install, it would be the second command (ubuntu-desktop), but this installs far more than you'd need on a server (games, IM, email client etc).

Thanks cwgatling!
I'll go for the ubuntu-desktop. The space isn't an issue, and I don't think that would install many daemons right? So resources should be still minimal. If I find myself with an increasingly slow server, I can always uninstall some things to lighten it.
:]
Thankyou again

---

### Post by cwgatling on 2008-05-26
No, no daemons will be installed. You can remove anything you don't need through Synaptic. Good Luck! :)

---

### Post by hyper_ch on 2008-05-26
why do you want to a have a gui anyway on a server?

---

### Post by hungryOrb on 2008-05-27
> **hyper_ch said:**
> why do you want to a have a gui anyway on a server?

Partly psychological. I feel safer ;D
Also, I don't know many commands for the CLI alone, so will find navigating through visual folders and setting shares etc, and more straightforward thing. Even if it's potentially slower.. :]
What I'm wondering, is can daemons be viewed in GUI? Can all the services that I need to run be assessed in a list?

---

### Post by iaculallad on 2008-05-27
> **hungryOrb said:**
> Partly psychological. I feel safer ;D
Also, I don't know many commands for the CLI alone, so will find navigating through visual folders and setting shares etc, and more straightforward thing. Even if it's potentially slower.. :]
What I'm wondering, is can daemons be viewed in GUI? Can all the services that I need to run be assessed in a list?

Yes you can, from using the GUI. Go to System->Administration->Services. You could view all your services in here, enable it or disable it as you like.

---

### Post by hungryOrb on 2008-05-27
> **iaculallad said:**
> Yes you can, from using the GUI. Go to System->Administration->Services. You could view all your services in here, enable it or disable it as you like.

Thankyou!

---

