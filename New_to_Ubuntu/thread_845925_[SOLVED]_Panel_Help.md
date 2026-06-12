---
title: "[SOLVED] Panel Help"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by bonedragon on 2008-07-01
hi 
I'm really in a pickle.
i have no idea what i did but when i start up ubuntu now i dont have the top panel. The one with *applications,places,system*
can some one please help me get it back. 
I did delete the bottom panel because i downloaded a dock.
i can access my home folder and thats it i think. unless there is some shortcuts i don't know about.
HELP

---

### Post by Elfy on 2008-07-01
Right click the panel - add to panel - main menu or menu bar

CLick bottom panle and do Add Panel  will give you a second panel which you can move, you will probably want notification area as well

---

### Post by tsger on 2008-07-01
I agree with the above post but would suggest you do them in reverse order.

1. Right click bottom panel, choose "new panel."
2. Right click the new panel, choose "properties."  Choose orientation: "Top."
3. Right click the new panel, choose "add to panel," then add "menu bar" and "notification area."

Hope it helps.

---

### Post by Elfy on 2008-07-01
In a hurry to get kids to school - did second line second and no time to change it so it was first  :D

---

### Post by iaculallad on 2008-07-01
If the post above still does not work. Try pressing Alt+F2, a window will pop-up and enter "gnome-terminal" (w/o double quote) and press Enter Key. This will launch your terminal:

On your terminal, issue the commands below, one command at a time.

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel

```

---

### Post by jmaque on 2008-07-01
I have a slightly similar dilemma, I accidently removed my top panel.  Is there a way to "restore" it back to all the defaults.

If not, then I will have another question, I will open a new topic to ask how to add all the panel items back.  The main one that I am having trouble getting back is the network one ( the one that allows you to switch between NIC and wifi settings).

thanks in advance

---

### Post by Elfy on 2008-07-01
Notification panel will have the network applet in it.

But this apparently works to restore the default - not done it myself as I diy it.

[http://ubuntuforums.org/showpost.php?p=4663517&postcount=9](http://ubuntuforums.org/showpost.php?p=4663517&postcount=9)

---

### Post by jmaque on 2008-07-01
> **forestpixie said:**
> Notification panel will have the network applet in it.

But this apparently works to restore the default - not done it myself as I diy it.

[http://ubuntuforums.org/showpost.php?p=4663517&postcount=9](http://ubuntuforums.org/showpost.php?p=4663517&postcount=9)

The notification panel did it.  I had actually already added it, but the network thing was not showing, TILL i rebooted.

Thanks for the help

---

### Post by bonedragon on 2008-07-02
hi 
first of all thanks to everybody who replied.
maby i wasent clear enough i have no panels on the desktop at all, so i cant do the whole right click add pane thing :(.
thanks iaculallad but the alt+f2 thing is not working i dont get the pop up:(.
when i right click anywhere on the screen the only options i get is create new folder, create new launcher, create new document etc. nothing on panels.
thaks again for any and all help

---

### Post by tjwoosta on 2008-07-02
i think if you press alt-f2 
you can just type 
```
gnome-panel
``` 
in the box and it should pop up a new panel

then just right click and add all the stuff



> 
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel


i dont mean to sound hostile but what the hell do thees commands do?

shutdown gconftool?
remove recursively /.gconf/apps/panel?
kill gnome-panel?

wouldn't this cause more damage?

---

### Post by bonedragon on 2008-07-03
hi guys thanks oncemore for the help
i got the terminal working by finding it in the filesystem.
the comands..

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel

```[/QUOTE]

didnt do anything i tried it twice to make sure still no luck.
any help or do i just have to reinstall ubunut?
:(

---

### Post by appi2012 on 2008-07-03
go to the terminal and run:
```
gnome-panel
```

That should get you a panel.

If not, run:
```
gnome-system-monitor
```

and tell me whether gnome panel is on the list of processes.

---

### Post by bonedragon on 2008-07-05
thank you
appi2012 and iaculallad
it worked. i dident have gnome-panel installed by default but it told me how to install it when i typed "gnome-panel"
thanks again.

---

