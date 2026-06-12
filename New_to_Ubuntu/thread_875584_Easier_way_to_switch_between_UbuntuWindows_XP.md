---
title: "Easier way to switch between Ubuntu/Windows XP"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by misswham on 2008-07-31
Is there an easier way to swtich between Ubuntu and XP without rebooting and if so how?

---

### Post by overdrank on 2008-07-31
> **misswham said:**
> Is there an easier way to swtich between Ubuntu and XP without rebooting and if so how?

You can use XP in a virtual machine. Virtual Box or VMware

---

### Post by tuxxy on 2008-07-31
[http://www.virtualbox.org/](http://www.virtualbox.org/)

Heres how to install,

[http://ubuntuforums.org/showthread.php?t=770745](http://ubuntuforums.org/showthread.php?t=770745)

---

### Post by aktiwers on 2008-07-31
Remember 3d games won't run on Windows installed on a virtual machine (VirtualBox or Vmware)

---

### Post by dhughes on 2008-07-31
I second the virtual machine, although it can be slow and some stuff like USB, CD-ROM drives may not work without some effort.

 Or if you have a second computer install XP on it and use a KVM (keyboard video mouse) switch to switch between the two systems using just one keyboard, mouse and monitor.

 You could also, instead of a KVM switch, use VNC to view another system (also pretty slow).

---

### Post by Locutus_of_Borg on 2008-07-31
two computers, lol


srsly, vmware is nice

virtualbox has some cooler features, but i found vmware easier to set up internet access through my wireless card, plus i couldnt get os x to install in virtualbox

---

### Post by Atomic Dog on 2008-07-31
I like vmware myself, but both prooducts are quite nice.

A virtual XP machine will run those win apps you can't live without. ...of course wine may run your windows apps too, so you may want to explore wine also.

---

### Post by speeddemon8803 on 2008-07-31
without rebooting? no

---

### Post by norwizzle on 2008-07-31
> **Locutus_of_Borg said:**
> two computers, lol



I was waiting for that :)

---

### Post by rossjman1 on 2008-07-31
I actually set up a XP virtual machine (with virtualbox) and added a new session to the GDM session menu that allows me to Run XP without rebooting or being slowed down by a desktop environment and window manager. It works great! I did it for the 'cool' factor and the only app I use in it is Absolute Poker (which doesn't work with wine). I was going to try to install SimCity 4, but reading the posts here, I don't think I will be able to...

---

### Post by raptor2552 on 2008-07-31
> I actually set up a XP virtual machine (with virtualbox) and added a new session to the GDM session menu that allows me to Run XP without rebooting or being slowed down by a desktop environment and window manager. It works great! I did it for the 'cool' factor and the only app I use in it is Absolute Poker (which doesn't work with wine). I was going to try to install SimCity 4, but reading the posts here, I don't think I will be able to...

How did you do that?

---

### Post by dhughes on 2008-07-31
> **norwizzle said:**
> I was waiting for that :)


 I missed the joke.

 What geek doesn't own more than one computer?

---

### Post by misswham on 2008-07-31
Is vmware pretty easy to install and do I have to reinstall both xp and ubuntu to install vmware?  I just hate to have to do that because I have done a lot of upgrades on both and I hate to have to start over.  Is vm ware free and will it slow down my computer like virtualbox?

---

### Post by rossjman1 on 2008-07-31
> **raptor2552 said:**
> How did you do that?

I actually created a thread in the tips & tutorials forum yesterday, but it has yet to be posted.

First you need to set up VirtualBox and whatever OS you want to use (there are several tutorials about this). Then you open a terminal and navigate to /usr/share/xsessions and then do ```
sudo gedit windows.desktop
```. You can name this file whatever you want (but keep the .desktop). I used windows.desktop in this example.
Paste this code into the new file:
```
[Desktop Entry]
Encoding=UTF-8
Name=Windows XP Pro
Comment=This session will run Windows XP
Exec=VirtualBox -startvm "Windows XP Pro"
Icon=
Type=Application
```
The **Name** entry is the title that will be displayed in the GDM sessions menu. the **Exec** entry is what will be executed when you try to log in under that session. The part that's in the quotes is the name of your virtual machine (screenshot).
[IMG]http://[IMG]http://http://jeffantosh.googlepages.com/Screenshot-VirtualBoxOSE.png[/IMG]Apparently I can't show images here. [http://jeffantosh.googlepages.com/Screenshot-VirtualBoxOSE.png](http://jeffantosh.googlepages.com/Screenshot-VirtualBoxOSE.png)
Restart X and you're done! You can make the VM fullscreen by pressing right control and f at the same time.

---

