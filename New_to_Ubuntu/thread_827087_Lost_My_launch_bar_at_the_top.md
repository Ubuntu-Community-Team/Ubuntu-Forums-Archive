---
title: "Lost My launch bar at the top?"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by DarkSaga70 on 2008-06-12
I rebooted last night and now when gnome starts up I have no way to launch apps or anything because the bar at the top I normaly use has decided to vanish. Please help me get this back.

---

### Post by wolfen69 on 2008-06-12
right click the existing taskbar and add new panel. move it, then click add to panel to add what features you want.

---

### Post by DarkSaga70 on 2008-06-12
> **DarkSaga70 said:**
> I rebooted last night and now when gnome starts up I have no way to launch apps or anything because the bar at the top I normaly use has decided to vanish. Please help me get this back.

I don't have ANY bar to right click on. I have seen this before on a friends machine but he is not home to ask how he fixed it. On my desktop I have no bars what so ever just icons.

---

### Post by issih on 2008-06-12
Hit alt F2, and use the dialog to run "gnome-panel".

That will give you at least a bare panel back from which you can follow the previous advice, it might even bring back everything if your config is still ok

Hope thats useful :)

---

### Post by drs305 on 2008-06-12
Once you get the panels back and set up to your liking, you can save the settings with the following command. It will save most, but not all, of your panel settings.

Use whatever /location/name you wish. This example saves the panel settings to ~/Desktop/panel.settings:
```
gconftool-2 --dump /apps/panel > ~/Desktop/panel.settings
```

To restore the panel settings and then refresh the desktop:
```
gconftool-2 --load ~/Desktop/panel.settings && killall gnome-panel
```

---

### Post by DarkSaga70 on 2008-06-12
> **issih said:**
> Hit alt F2, and use the dialog to run "gnome-panel".

That will give you at least a bare panel back from which you can follow the previous advice, it might even bring back everything if your config is still ok

Hope thats useful :)

when i hit alt-F2 nothing happens :(

---

### Post by issih on 2008-06-12
Immediate response.

1) Did you change the run command keyboard shortcut? if so use that obv..
2) Are you sure you hit alt+f2? is it a keyboard where the function keys are dual use, did you use the appropriate modifier? The system needs to see the keys alt and F2 simultaneously.
3) Do you drop into a terminal if you hit ctrl+alt+F1? if so then your function keys are ok and things are a bit trickier hit ctrl+alt+F7 to get back to the graphical shell.

Let us know if any of that helps and give me a moment to check something

---

### Post by DarkSaga70 on 2008-06-12
> **issih said:**
> Immediate response.

1) Did you change the run command keyboard shortcut? if so use that obv..
2) Are you sure you hit alt+f2? is it a keyboard where the function keys are dual use, did you use the appropriate modifier? The system needs to see the keys alt and F2 simultaneously.
3) Do you drop into a terminal if you hit ctrl+alt+F1? if so then your function keys are ok and things are a bit trickier hit ctrl+alt+F7 to get back to the graphical shell.

Let us know if any of that helps and give me a moment to check something

 ctrl+alt+F1 takes me to a terminal yes I guess that is a plus.

---

### Post by issih on 2008-06-12
Ok, goto the terminal (ctrl+alt+f1), and login, enter your username and password as prompted (exactly as you would at the graphical log in)

Now type:

```
DISPLAY=:0 gnome-panel
```

and go back to the graphical shell, hopefully that will mean you now have a panel back :s. From there add your other panels as before. Once you have a main menu applet added, go into "System->Preferences->Keyboard Shortcuts" and ensure you have a keyboard command set to launch the run command(alt+F2 is the default) and also one to launch a terminal (I use ctrl+alt+t) so you can get out of this kind of mess more easily.

Hope that works.

---

### Post by DarkSaga70 on 2008-06-12
> **issih said:**
> Ok, goto the terminal (ctrl+alt+f1), and login, enter your username and password as prompted (exactly as you would at the graphical log in)

Now type:

```
DISPLAY=:0 gnome-panel
```

and go back to the graphical shell, hopefully that will mean you now have a panel back :s. From there add your other panels as before. Once you have a main menu applet added, go into "System->Preferences->Keyboard Shortcuts" and ensure you have a keyboard command set to launch the run command(alt+F2 is the default) and also one to launch a terminal (I use ctrl+alt+t) so you can get out of this kind of mess more easily.

Hope that works.

OK!!!! I guess I un-installed somthing wrong when I tried to take out evolution and it screwed things up so I followed your commands and then the commands that the term told me and now I am once agian good to go :) Thank you for all the help :)

---

### Post by issih on 2008-06-12
Excellent, glad to have been of service :D

---

