---
title: "How to find out where Unity launcher launches from?"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by newgiin on 2013-06-14
I'm used to being able to just right-click on shortcuts and figure out where they point to. Can you do this in Unity? For example, for the life of me, I can't figure out where Transmission is installed, the only way I can launch it is by searching for it in the launcher, but right-clicking just shows me the app. description...

---

### Post by Cheesemill on 2013-06-14
***Short Answer***

Nearly all applications are installed into the /usr/bin directory. The command for Transmission is /usr/bin/transmission-gtk.

***Long Answer***

To find this out first take a look in /usr/share/applications for all of the .desktop files. This is where all of the information comes from for applications in the dash (and in the main menu of other DE's). It's pretty obvious by looking that the .desktop file for Transmission is called transmission-gtk.desktop. Now open this file in a text editor and look for the line that begins with 'Exec=' to find out the command that is run when the application is launched, in this case it's transmission-gtk.

To check where this application lives you can use the which command...
```
rob@arch:~$ which transmission-gtk
/usr/bin/transmission-gtk
```

Anyway, that's the long explanation but 99% of the time the answer is /usr/bin/<application name>.

---

### Post by newb85 on 2013-06-14
Your question concerns me a little.  Why exactly do you want to know where the application is installed?

---

### Post by 3rdalbum on 2013-06-14
I'm with newb85, but if you want to see the exact command being run, look in the Main Menu program.

---

### Post by newgiin on 2013-06-14
> **newb85 said:**
> Your question concerns me a little.  Why exactly do you want to know where the application is installed?

Mostly curiosity. I was just wondering if there was a way to quickly determine the executable without a terminal since obviously the launcher already knows where it is.

---

### Post by chinainch on 2013-06-14
I would like to know as well, just got a new machine with ubuntu 12.4 installed, and it is driving me crazy. I can't shrink the launcher panel, I can't shrink open windows, have no 'force quit', can't get proper monitor resolution, and yes, there is more.  I would have had Linux installed had I known how brain dead this is.  Please if anybody can help it would be appreciated.

---

### Post by newb85 on 2013-06-14
> **chinainch said:**
> I would like to know as well, just got a new machine with ubuntu 12.4 installed, and it is driving me crazy. I can't shrink the launcher panel, I can't shrink open windows, have no 'force quit', can't get proper monitor resolution, and yes, there is more.  I would have had Linux installed had I known how brain dead this is.  Please if anybody can help it would be appreciated.

In System Settings, under Appearance, there should be a slider for Launcher Icon Size on the Look tab.  On the Behavior tab, there's an option to Auto-Hide the Launcher.

In the top-left corner of the screen should be three buttons.  (They will appear if you take your mouse to the top of the screen, as will the menus for the foreground window.)  Those are the classic Close, Restore, and Minimize buttons.

Monitor resolution is in System Settings as well, under Displays.

Usually if you try closing an unresponsive window a couple times, Ubuntu will ask if you want to force quit.  Barring that, you can open System Monitor and kill processes.

---

### Post by 3rdalbum on 2013-06-14
> **newb85 said:**
> 
Usually if you try closing an unresponsive window a couple times, Ubuntu will ask if you want to force quit.  Barring that, you can open System Monitor and kill processes.

There's also xkill - hit Control-Alt-T and type "xkill" and press Enter, then click on the window of the program you want to force-quit.

@Chinainch: Linux is very different to Windows. It's not meant to be like Windows at all. It's not "brain dead", you're just still in the process of learning a completely different system. I had similar problems when I first tried to use Windows, after having used Mac OS and Linux all my life. Stick with it and you'll probably find it rewarding, and afterwards you'll say to yourself "Wow, that was actually really easy".

---

