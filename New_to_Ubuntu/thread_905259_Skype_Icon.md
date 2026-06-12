---
title: "Skype Icon"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by avanrens on 2008-08-30
When you close Skype it runs in the background and leaves an icon on the gnome panel, but I for some reason went and deleted the icon. Now I can't access Skype without the icon. I've removed it using Synaptic and re-installed it but still no icon on the panel.
Yes I know I won't do it again!

---

### Post by nothingspecial on 2008-08-30
I don`t use skype but try,

```
skype
```

---

### Post by vishzilla on 2008-08-30
Create a new launcher. Right click on the menu, and select Edit Menu. Go to Internet, on the right of the window you will find New Item. Select it and enter the details, with the command 'Skype'

---

### Post by L Campbell on 2008-08-30
> **avanrens said:**
> When you close Skype it runs in the background and leaves an icon on the gnome panel, but I for some reason went and deleted the icon. Now I can't access Skype without the icon. I've removed it using Synaptic and re-installed it but still no icon on the panel.
Yes I know I won't do it again!

Have you tried > Applications > Internet > Skype and you still don't get the icon to appear?

---

### Post by avanrens on 2008-08-30
Yes I can run skype that's not the problem its when I close Skype and it use to leave a small icon on the quick launch menu bar, that particular icon does not appear any more after I delected it, even if I completely remove Skype using Synaptic and then re-install it. There must be a way to completely remove a program, I have used locate in terminal and have found a lot of references to Skype after I uninstalled it.

---

### Post by nothingspecial on 2008-08-31
Like I said, I don`t use skype, but you may have a hidden .skype directory in your home folder.

Places > Home Folder. Press Ctrl + H and some hidden files all starting with a . will appear.
 These are just configuration files for apps on your system ie all the settings you have saved for them.
If there is a .skype folder, delete it a run skype again. You`ll probably have to set it all up again because it should run as if you`d just installed it. Hopefully whatever you`ve done to permanently delete your icon will have been reset.

---

### Post by avanrens on 2008-08-31
Hi thanks for the info, but I'm afraid it still didn't work. I suspect Skype must be hiding a config file some where and using it when I re-install.
Thank you all the same I'll just live with it at the moment as it still works fine, if I close down Skype I then and have to use System Monitor to stop Skype running and then restart it to use it.

---

### Post by olebon on 2009-07-05
Maybe this reply is too late and useless, but I've just solved this problem on my machine. You should right click an empty space on the panel,then "Add to Panel" and finally "Notification Area". If this applet is already there, try to clean up more space for it to fit all your notifications.;)

---

