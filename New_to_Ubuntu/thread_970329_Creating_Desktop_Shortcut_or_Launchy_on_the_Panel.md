---
title: "Creating Desktop Shortcut or Launchy on the Panel"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by Opera Rocks! on 2008-11-04
Hello,

With help from people on this forum :p  I have successfully installed the latest Xubuntu on an old desktop.

Everything is now done except for the following:

I want to create a shortcut on the desktop or the panel for a program called tsclient.  I use this program to connect to another computer.

In XP I would just right click the program on the start menu and 'send to desktop' but I cannot do this in Xubuntu.

I have tried dragging the program onto the desktop (including while holding CTRL and Shift at the same time) to no avail.  

I tried to go to the panel and 'add new program launcher' but this required me to know where the program is located.

Ok and I hate using this terminal thing almost as much as I hated using msdos.  Is there a graphical program I can use in Xubuntu that will let me easily create shortcuts on the desktop or panel?

Does anyone have any other simple way of doing this?

Cheers,

Paul.

---

### Post by mikewhatever on 2008-11-04
> **Opera Rocks! said:**
> 

I have tried dragging the program onto the desktop (including while holding CTRL and Shift at the same time) to no avail.

Do you mean the executable? I thought you didn't know where it was. In Ubuntu/Gnome you can drag the menu launcher while holding Ctrl, but I'm not sure it works that way in Xubuntu.

> I tried to go to the panel and 'add new program launcher' but this required me to know where the program is located.

You can find out by typing <which tsclient>, I don't know of a gui way.

---

### Post by Opera Rocks! on 2008-11-04
> **mikewhatever said:**
> Do you mean the executable? I thought you didn't know where it was. In Ubuntu/Gnome you can drag the menu launcher while holding Ctrl, but I'm not sure it works that way in Xubuntu.



You can find out by typing <which tsclient>, I don't know of a gui way.

Thanks Mike,

What I tried to drag to the desktop was the tsclient link in the Network folder.

With regards to typing <which tsclient> do I just open a terminal and type this in?

Sorry for being stupid :p

Paul.

---

### Post by mikewhatever on 2008-11-04
Yes, if there is an executable, it should return the path to it.

example:
 which totem
/usr/bin/totem

or
which tsclient
/usr/bin/tsclient

:)

---

### Post by randcoop on 2008-11-04
If you're using Thunar (the default file manager for Xubuntu), then you can in fact emulate Windows:

Open a file manager window and navigate to the program (it's almost always in the /usr/bin folder).  Then right-click on the program and select Send To.  It will create a desktop launcher link to the program.

---

### Post by Opera Rocks! on 2008-11-05
Hello randcoop and mikewhatever,

Thank you both - I used both your suggestions and have successfully created a desktop launch and a panel launcy - Woo Hoo!

Now the next question :p  What I would like to happen when I start tsclient is for it to automatically go to the login screen of the terminal server I connect to.  For example the IP address 10.10.5.4 (this isn't a real address).

This would be preferable to having our users have to hit the 'connect' button etc.  You can probably guess this is a bit of a different situation.  I am trying to get our workplace give up on the Win 98 machines and instead turn all the desktops into clients.

So I tried first on my home desktop to make sure it works properly - it does!

I hope this makes sense?


Thanks again,

Paul

---

### Post by randcoop on 2008-11-06
I'm sorry to say that I cannot help on this one, since I don't use (and have never used) tsclient.  

You might want to try starting another thread with a different title in order to get your questions answered.

---

### Post by GepettoBR on 2008-11-06
I agree with randcoop, but I can forward a bit of general advice:

You can channge the shortcut's command to make the program start in a special way. For example, if I want to have a shortcut that makes Firefox open and go to Google, I can change the launcher from "firefox" to "firefox www.google.com"

In order to know what parameters tsclient accepts, you can read the man page by typing "man tsclient" in a terminal.

---

### Post by GepettoBR on 2008-11-06
I agree with randcoop, but I can forward a bit of general advice:

You can channge the shortcut's command to make the program start in a special way. For example, if I want to have a shortcut that makes Firefox open and go to Google, I can change the launcher from "firefox" to "firefox www.google.com"

In order to know what parameters tsclient accepts, you can read the man page by typing "man tsclient" in a terminal.

---

### Post by powel212 on 2009-06-27
I have been using Xubuntu on an old machine for a while too and it runs very well. 

I just figured out a pretty easy way to add icons to the desktop.

Right click the desktop and select add launcher then in the "name" box start typing the name of an application, for example "firefox" at this point a list of available applications with that name should appear and then just select the app and hit enter.

Done

Powel

---

