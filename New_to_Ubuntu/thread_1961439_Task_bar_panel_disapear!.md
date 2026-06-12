---
title: "Task bar panel disapear!"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by vagelism on 2012-04-19
Hello to all!
I have a problem when (rarely) my pc crashes , the task bar with my shortcuts on it desapear and I have to rebuild it. I have this problem since in my new installation of ubuntu I choosed my home directory to be encrypted.
Any idea on how to do make somekind of shortcut or where this file is stored with the preferences of the bar in order to backup it and restore it any time I face this small problem?
Thank you!

---

### Post by Frogs Hair on 2012-04-19
The answer depends on what version of Ubuntu you use . If you use 11.04 or earlier you can use the following command restore defaults .```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

The application at the link will save panel settings to be restored on older versions of Ubuntu. I have never used it though.
[http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/](http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/)

---

### Post by vagelism on 2012-04-19
> **Frogs Hair said:**
> The answer depends on what version of Ubuntu you use . If you use 11.04 or earlier you can use the following command restore defaults .```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

The application at the link will save panel settings to be restored on older versions of Ubuntu. I have never used it though.
[http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/](http://www.omgubuntu.co.uk/2010/09/how-to-restore-default-gnome-panels-in-ubuntu/)

I dont want to restore the defaults but to restore my customized panel that is dissapeared every time a crash happent.
When I have this problem the tast bar is totally empty after restart and I have to rebuild it!

---

### Post by Frogs Hair on 2012-04-19
That is why I posted the link . With older versions of Ubuntu Tweak you could also back up your desktop configuration . The command will restore the the default indicators such as menu , date/time , user menu , and notification area without having to rebuild the panel from the add to panel menu on versions 11.04 or earlier .

---

### Post by vagelism on 2012-04-19
> **Frogs Hair said:**
> That is why I posted the link . With older versions of Ubuntu Tweak you could also back up your desktop configuration . The command will restore the the default indicators such as menu , date/time , user menu , and notification area without having to rebuild the panel from the add to panel menu on versions 11.04 or earlier .

Then...is what I wanted! 
Can you please explain me what exactly does ? To copy and paste it is nice and works great , but I would like to learn also if is possible. 
Thank you!

---

### Post by Frogs Hair on 2012-04-19
The command bypasses the gui and resets the default configuration. It saves the trouble of having to open the configuration editor or add to panel menu to restore the items manually.

Recursive: of, relating to, or involving recursion <a recursive function in a computer program> 

The following portion of the command restarts the the panel but will not restart  applications that are not intended to run continuously , it simply closes the application .  

```
killall gnome-panel 
```

---

### Post by vagelism on 2012-04-19
Thank you once more!

---

