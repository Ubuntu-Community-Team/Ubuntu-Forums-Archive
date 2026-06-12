---
title: "Transition from Lubuntu to Ubuntu"
date: 2019-12-19
forum: New to Ubuntu
---

### Post by wjbmd48 on 2019-12-19
Hi:

I'm experienced with Lubuntu, but inexperienced at Ubuntu 18.04, and there are 3 things I just can't figure out:

1) I know that to be able to create desktop links I have to get into "properties|behavior" in nautilus, and enable create links. I just can't see how I get into "properties|behavior in the nautilus screen: I've tried left/right clicking everywhere. What's the secret to this?

2) I'm used, in Lubuntu, setting my panel applets (battery/resource/temperature/CPU use) by right clicking on the panel. How does one set these things up in the Ubuntu dock?

3) Where is the menu showing system tools/preferences/internet/office/graphics/sound-video, etc? I can see it when I set up new items in alacarte, but otherwise can't locate it.


Thanks!!

Bill

---

### Post by coffeecat on 2019-12-19
So that forum members can advise you appropriately, please state which supported release of Ubuntu you are using. If you are still using 16.04 you will have the Unity desktop. If 18.04 or later, it will be gnome. There are differences.

---

### Post by wjbmd48 on 2019-12-19
Ooh, sorry, it's Ubuntu 18.04, edited in original post.

Thanks!

I'm always confused by what is meant by "gnome." Is there an editing package I'll need to download to do 1)-3) above?

Bill

---

### Post by CatKiller on 2019-12-19
The kinds of things you want to do - launchers on the desktop, widgets on the panel, a traditional menu - are things that the Gnome devs specifically dislike and don't want users to be able to do. Some functionality is barricaded behind secret keyboard modifier keys, but most has been shunted to external extensions.

If you're after something less barebones than lubuntu, while still being allowed to make it do what you want, I'd suggest you should go with KDE rather than Gnome.

---

### Post by Redalien0304 on 2019-12-19
The Cinnamon DE Does all that already. take a look at it

---

### Post by wjbmd48 on 2019-12-19
Sorry to be so hopeless, but I'm not sure I know what the difference is between KDE and gnome; I downloaded cinnamon via synaptic, but how do I fire it up? I see nothing in the apps list, and when i fire up cinnamon in terminal, all I see is: 
Cinnamon warning: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.

In addition, I still have no idea about how to access properties|behavior in either nautilus or the file manager so's I can make links.

Thanks!

Bill

---

### Post by CatKiller on 2019-12-19
> **wjbmd48 said:**
> Sorry to be so hopeless, but I'm not sure I know what the difference is between KDE and gnome. 

Gnome and KDE are both modern desktop environments with a bunch of integrated niceties. Gnome is developed by control freaks who dislike their users being able to customise their computing experience in any way or otherwise do things that they don't approve of. KDE is not.

It's trivially easy to do those things you wanted to do in KDE, rather than being an uphill struggle against the efforts of the developers like it is in Gnome.

If you aren't sure what a desktop environment is at all, rather than simply what the differences between them are, [this article](https://www.forbes.com/sites/jasonevangelho/2018/09/17/linux-for-beginners-whats-a-desktop-environment/) may help.

---

### Post by wjbmd48 on 2019-12-19
OK, the fog is lifting. So if I'm using Ubuntu, I'm stuck with gnome and can't use the more versatile KDE, correct? Can cinnamon do this, and how do I fire it up? I've downloaded it, but don't know how to start it.

But the major thing I'd still like to do is to put up desktop links. Can someone please tell me what to click on or enter in terminal to allow link creation in nautilus/file manager to access properties|behavior? For the life of me I can't figure out how to do this.

Thanks!!

Bill

---

### Post by CatKiller on 2019-12-19
> **wjbmd48 said:**
> OK, the fog is lifting. So if I'm using Ubuntu, I'm stuck with gnome and can't use the more versatile KDE, correct? Can cinnamon do this, and how do I fire it up? I've downloaded it, but don't know how to start it.

Technically, no, you're not stuck. The desktop environments are all packages like any other. You can have Gnome, KDE and Cinnamon all installed at the same time and pick whichever one you want to use for a given session from the login screen.

Since all your data is backed up and you're starting fresh anyway, I'd suggest reinstalling from a Kubuntu or Ubuntu Mate image so that you don't have any of Gnome's weirdness, but otherwise it's ```
sudo apt install kubuntu-desktop
``` or ```
sudo apt install cinnamon
``` There should be a thing to click on near your name on the login screen for which session you want to use.

> But the major thing I'd still like to do is to put up desktop links. Can someone please tell me what to click on or enter in terminal to allow link creation in nautilus/file manager to access properties|behavior? For the life of me I can't figure out how to do this.

For obvious reasons I haven't used Gnome in a while, but I think you're asking a few things here. Nautilus' settings are hidden behind a thing that I remember looking like three vertical dots. To have icons on the desktop I believe you need to install an extension in Gnome. If you're trying to make symbolic links rather than create desktop launchers you can use ```
ln -s <old thing> <new thing>
```

---

### Post by Dennis N on 2019-12-19
> But the major thing I'd still like to do is to put up desktop links. Can someone please tell me what to click on or enter in terminal to allow link creation in nautilus/file manager

To enable the create symbolic link option of Files:
```
Nautilus (Files) > Preferences > Behavior > Link Creation > check the box: "Show action to create symbolic links"
```
Then, right click on a file and select "Create link". You can then move created link to the Desktop folder to show the link on the Desktop.

---

### Post by wjbmd48 on 2019-12-20
Many thanks all; it's been an education. After fooling around with Ubuntu, I think I've decided that, at least for my purposes, it offers no improvement over Lubuntu, which seems more versatile, and for which I've done most of the learning curve climbing. 

I do appreciate all your help!

Bill

---

### Post by TheFu on 2019-12-20
> **wjbmd48 said:**
> Many thanks all; it's been an education. After fooling around with Ubuntu, I think I've decided that, at least for my purposes, it offers no improvement over Lubuntu, which seems more versatile, and for which I've done most of the learning curve climbing. 

I do appreciate all your help!

Bill

The DE is NOT the OS!!!
The DE is just a coat of paint, window shutters, fancy porch, on a house. The house is still the house, with "ubuntu" being the house.

It is unfortunate that Canonical doesn't actually use "Ubuntu w/Gnome3 Desktop" as the name for the Ubuntu release they push most.  A few other options are:
[LIST]
[*]Ubuntu w/KDE Desktop
[*]Ubuntu w/LXQt Desktop
[*]Ubuntu w/XFCE4 Desktop
[*]Ubuntu w/Mate Desktop
[*]Ubuntu w/Cinnamon Desktop
[*] ...  and a few others.
[/LIST]

There are also ways do NOT change all the default applications preinstalled.  We can just change the DE - Desktop Environment and keep the default applications for Kubuntu, Lubuntu, Xubuntu, Ubuntu-Mate .... 

And if you want a less fancy GUI, you don't actually need a DE at all.  GUIs are layers.  X11, Xt, Xm, Window Manager, DE, DE-Addons.  If we use X11 -->  WM layers, we have a less bloaty GUI.  There used to be over 50 different WMs. Today, there are at least 20 still used that can be installed with a simple **sudo apt install {some-wm-pkg-name}**. Any that are installed will show up under the "Gear" on the login page.  Click the gear, pick the session type you want, then login.  There are some dangers when the DEs share underlying libraries because they will also share config files and those settings.  XFCE, Mate, Cinnamon are all based on Gnome2.

I'm not a fan of Gnome3, but mainly because it doesn't work well on low-end systems or inside virtual machines.  About a year ago, I got fed up with all the bloat and GUI changes for the sake of change only. Decided to go back to the WM I used in the mid-1990s, fvwm.  fvwm is basically the same now as it was then.  The config files are all self-contained, outside what any DE would touch.  The settings don't require that I keep up with text files AND a dconf editor AND a few different GUI "settings" tools. Too frustrating for me. 

What's the point of this?  You can pick any GUI you want, but picking closely related GUIs can cause problems.  The solution to avoid those issues is to use a different userid+login for each different GUI.  They can be added and removed just like changing a shirt and suit.

---

### Post by wjbmd48 on 2019-12-20
I appreciate all that, it's been an education.

Ultimately, I gave up on Ubuntu in favor of Lubuntu because the WINE/Microsoft Office seemed much buggier in Ubuntu, to the point of mangling Word files, which is a deal breaker for me. Better a simpler and less advanced OS than having to worry about corrupted files. (And, no, libreoffice is not an option when dealing with publishers, which is my line of biz.)

---

### Post by cpt-ankitsharma on 2019-12-23
> **wjbmd48 said:**
> Sorry to be so hopeless, but I'm not sure I know what the difference is between KDE and gnome; I downloaded cinnamon via synaptic, but how do I fire it up? I see nothing in the apps list, and when i fire up cinnamon in terminal, all I see is: 
Cinnamon warning: Screen 0 on display ":0" already has a window manager; try using the --replace option to replace the current window manager.

In addition, I still have no idea about how to access properties|behavior in either nautilus or the file manager so's I can make links.

Thanks!

Bill

GNOME, KDE XFCE, UNITY etc. these are all desktop environments. 

Here is some more info:

[https://en.wikipedia.org/wiki/Desktop_environment](https://en.wikipedia.org/wiki/Desktop_environment)

Depending on the needs you would install a certain desktop environment on top of your OS. Which is just a different GUI to interact with your OS. 

Beofre you login to ubuntu there is a option to select the environment to login. Just install the environment as the above post describes and login to your preferred environment.

---

