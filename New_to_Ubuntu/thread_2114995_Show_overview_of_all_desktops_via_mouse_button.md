---
title: "Show overview of all desktops via mouse button"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by soundpwns909 on 2013-02-11
I just recently decided to make the switch to ubuntu, so to make it as easy as possible for me I'm trying to get a lot of the same feel of osx mountain lion from ubuntu.  

I am trying to see an overview of all my virtual desktops via a mouse button. Similar to what you can do with mission control in osx. I've been trying to find information on it but I really don't know where to start.  

Currently I am using Cairo Dock as my desktop environment. 

Any help is appreciated.

System Specs
Intel i5 3570K
Gigabyte GA-Z77X-UD5H
8 Gb Ram
Ubuntu 12.04 LTS

---

### Post by TheFu on 2013-02-11
You will need to override the mouse settings for the window manager or choose a window manager that provides the function you want.  I'm almost positive that **fvwm** supports what you want, but you'll definitely be editing a text config file to make it happen.

Trying to make Linux feel like OSX will leave you disappointed.  I know, last year, I tried to make OSX feel list Linux and was extremely disappointed. That doesn't mean that OSX or Linux are inferior, just that they have very different design philosophies.  After a week, I returned the Mac - couldn't stand it.  It felt like I didn't have any control when I'm used to having complete control.

---

### Post by soundpwns909 on 2013-02-11
Thanks I will look into that.  Ya, I guess I'm not going completely for the osx feel, I'm trying to switch up how I work, but there are a few things about osx that I have gotten use to and would like to do in linux.

---

### Post by grahammechanical on 2013-02-11
I do not know what version of Ubuntu you are using but I get this with Ubuntu Unity.

> I am trying to see an overview of all my virtual desktops via a mouse button. 

There is a workplace switcher icon in the Launcher. One click and the screen changes to a representation of four workplaces. And I can drag applications from one workspace to another or change workspaces by clicking on the workspace.

In 12.10 you may have to put this icon on the Launcher by going to System Settings>Appearance>behaviour tab and ticking Enable Workspaces.

Regards.

---

### Post by soundpwns909 on 2013-02-11
> **grahammechanical said:**
> I do not know what version of Ubuntu you are using but I get this with Ubuntu Unity.



There is a workplace switcher icon in the Launcher. One click and the screen changes to a representation of four workplaces. And I can drag applications from one workspace to another or change workspaces by clicking on the workspace.

In 12.10 you may have to put this icon on the Launcher by going to System Settings>Appearance>behaviour tab and ticking Enable Workspaces.

Regards.


I'm not running the gnome desktop, I'm running cairo dock

---

### Post by stinkeye on 2013-02-12
I'm assuming your still using compiz as the window manager.

Use compizconfig-settings-manager
Install via terminal...
```
sudo apt-get install compizconfig-settings-manager
```
ccsm > Desktop > Expo > Expo button

---

### Post by coldcritter64 on 2013-02-12
> **soundpwns909 said:**
> I just recently decided to make the switch to ubuntu, so to make it as easy as possible for me I'm trying to get a lot of the same feel of osx mountain lion from ubuntu.  

I am trying to see an overview of all my virtual desktops via a mouse button. Similar to what you can do with mission control in osx. I've been trying to find information on it but I really don't know where to start.  

Currently I am using Cairo Dock as my desktop environment. 

Any help is appreciated.

System Specs
Intel i5 3570K
Gigabyte GA-Z77X-UD5H
8 Gb Ram
Ubuntu 12.04 LTSI achieved similar by installing easystroke and by holding down the right mouse button and scrawling two letters S and W in my hand writing, easystroke passes the keyboard combination "Super + W" to the OS. I set that combination in compiz for the main overview switcher, not sure if that is the default combination. Using easystroke may possibly work for you, I'm totally unfamiliar with cairo dock.

---

