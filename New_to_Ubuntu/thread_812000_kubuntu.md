---
title: "kubuntu"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-05-29
Hi all
I use Ubuntu and I wanted to try the K Desktop Environment.Decided that I don't like it so I wanted to remove it.So I went in Synaptic and removed kubuntu-kde4-desktop (the same package I installed) but...no use.Now it says "Kubuntu" when the computer starts or stops, the login screen is from kubuntu, I can still choose kubuntu sesion, and if I log in into Gnome when I press the shut down button I can choose only "Log Out" "Switch User" "Lock Screen" "Suspend" and "Hibernate".The "shut down" and "restart" option are not present any more.What happened?How can I get rid of Kubuntu for good?

---

### Post by sayakb on 2008-05-29
You may change the usplash theme by:
```
sudo apt-get install startupmanager
```Open startup-manager from System->Administration->StartUp Manager
Click Appearance tab and under Usplash themes drop menu, select usplash-theme-ubuntu.

Change the login/logout screen (GDM) from System->Administration->Login Window, click on Local tab and select the Ubuntu theme from there.

For shutdown, try:
```
sudo shutdown -p now
```For reboot:
```
sudo reboot
```

---

### Post by Troll_the_Great on 2008-05-29
You still haven't answer my question.Why can't I remove KDE?Why did the "shutdown" and "restart" buttons disappeared?And I don't have a StartUp Manager in System-Administration.When I try to open Login Window I get "You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead".I have no idea what that is.Help pls!

---

### Post by sayakb on 2008-05-29
The package kubuntu-kde4-desktop installs numerous KDE libs and packages. Get rid of them manually (search n remove). But I don't recommending removing KDM unless you set Ubuntu to look for GDM as it starts.. No idea why the buttons disappeared. I never removed KDE4, though I installed it twice. Dunno why, but each time I end up having a crash with something else and had do a clean install ;) 
Honestly, I didn't face such a situation yet..

---

### Post by ChompTheMan on 2008-05-29
To change your default display manager open up a terminal and type in

```
sudo nano /etc/X11/default-display-manager
```

and you should see

```
/usr/bin/kdm-kde4
```

change it to

```
/usr/bin/gdm
```

then hit Crtl+o then enter to save, then Crtl+x to exit.  You should now get the ubuntu spash screen and login screen and should be using the Gnome Display Manager on startup.

To completely remove KDE4 you will have to remove the dependancies that came with it.  To view the list of dependancies look here: [http://packages.ubuntu.com/hardy/kubuntu-kde4-desktop]("http://packages.ubuntu.com/hardy/kubuntu-kde4-desktop").

**Only remove the dependancies that have 'kde4' or 'kubuntu' in their name**.  If you try to remove any of the other dependancies without knowing what you're doing you will mess up your system.

---

### Post by Troll_the_Great on 2008-05-31
Thx alot all, I manage to work it out the hard way. I removed KDM and the Ubuntu booted without the GUI.Then I removed the gnome desktop as well because I didn't know what commands to type to make it the default display manager (sudo apt-get remove gdm).After that I installed again (sudo apt-get install gdm) and when I rebooted everything was back to normal.:) Maybe is wasn't the right way, but I'm glad it worked.:guitar::guitar::guitar:

---

