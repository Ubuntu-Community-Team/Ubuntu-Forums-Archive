---
title: "network connection icon dissappeared"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Matrix1 on 2008-10-22
I must have done something really wrong but for some reason the network connection icon disappeared from the panel.  How would I get the icon back on the panel?  I have tried to add icons to the panel but the list does not contain this icon, it does have network activities but that's different.
Now that the network connection icon disappeared, I cannot even see the available wireless networks.

---

### Post by cl0ckwork on 2008-10-22
try pressing alt+F2 and launch **nm-applet**

that should solve your worries

---

### Post by Nxion on 2008-10-22
To add it back to my panel, You right-click on the panel, select 'Add to Panel', and then select 'Notification Area' under Utilities. Try that.

OR>>

```
sudo apt-get install network-manager-gnome
```

and of that does not work try ALT+f2 and type in the run dialog box 

```
nm-applet
```

---

### Post by Matrix1 on 2008-10-22
I tried launching the nm-applet but it does not do anything.
I also tried sudo apt-get install network-manager-gnome in the terminal.  The icon is still not on the panel.  Please help.

---

### Post by OrangeCrate on 2008-10-22
> **Matrix1 said:**
> I tried launching the nm-applet but it does not do anything.
I also tried sudo apt-get install network-manager-gnome in the terminal.  The icon is still not on the panel.  Please help.

It happened to me once too. I simply rebooted the computer, and it was back. Sorry to sound too simple here, but have you tried that?

---

### Post by Matrix1 on 2008-10-22
I tried rebooting few times already but does not bring back the icon.

---

### Post by rideburton56 on 2008-10-22
Not to hijack..... but how to you remove a duplicate nm-applet if say you did this to see what happens and have multiple nm-applets on your panel :)

---

### Post by Matrix1 on 2008-10-22
> **Nxion said:**
> To add it back to my panel, You right-click on the panel, select 'Add to Panel', and then select 'Notification Area' under Utilities. Try that.

OR>>

```
sudo apt-get install network-manager-gnome
```

and of that does not work try ALT+f2 and type in the run dialog box 

```
nm-applet
```

Thanks Nxion, it works now.

---

### Post by OrangeCrate on 2008-10-22
> **rideburton56 said:**
> Not to hijack..... but how to you remove a duplicate nm-applet if say you did this to see what happens and have multiple nm-applets on your panel :)

That's funny.

Well, you could move it to the other side of your panel, and then you wouldn't notice it as much. :)

Or, you could try to simply delete it - right click on the applet, and hit "remove from panel". By manually adding one, that worked for me.

If that doesn't work for you, I don't have a clue.

---

### Post by Matrix1 on 2008-10-22
i am seeing the same thing--duplicate wireless strength icon.  I tried to remove one by right clicking but there is no such option to remove.
Any ideas how to remove the duplicate?

---

### Post by OrangeCrate on 2008-10-22
> **Matrix1 said:**
> i am seeing the same thing--duplicate wireless strength icon.  I tried to remove one by right clicking but there is no such option to remove.
Any ideas how to remove the duplicate?

Not right on top of the icon, that just gets networking dialog, and there is no option to remove there.

Try just left of the icon. That's were the applet handle is. (Where there's three little lines, spots, or whatever your theme uses.)

---

### Post by rideburton56 on 2008-10-22
I just tried that, and it removed the whole bar of programs that im running (battery power, sound, pidgin,deluge,firestarter)

when I right clicked to add to panel, there is an applet called notification area that needs to be added back in again.  And what do you need to do after you add back in notification area?

alt+f2 and run nm-applet (ONLY ONCE!!)

---

### Post by OrangeCrate on 2008-10-23
> **rideburton56 said:**
> I just tried that, and it removed the whole bar of programs that im running (battery power, sound, pidgin,deluge,firestarter)

Sorry, but I'm not sure what you did that caused that?

> when I right clicked to add to panel, there is an applet called notification area that needs to be added back in again.  And what do you need to do after you add back in notification area?

Nothing. After adding it to the panel, it should work as intended.

---

