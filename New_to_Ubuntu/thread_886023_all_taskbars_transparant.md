---
title: "all taskbars transparant"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Falc7 on 2008-08-10
Hi
I was playing around with the transparancy settings in the compiz manager thing. And i seem to have made the top and bottom bars completely transparant. Thus rendering me completely unable to do anything, as i can't see. Is there some way to reverse this using the ctrl + F6 terminal? Or any other way?

---

### Post by gerben1 on 2008-08-10
Try this:
Hover your mouse over the task bar, press and hold down <alt> and roll your mouse-wheel.

---

### Post by Falc7 on 2008-08-10
Ah yes, that sort of worked, now i have the top and bottom tool bars, but the right click menu, and the applications and places drop down menu, are all still transparant.

---

### Post by ThrobbingBrain66 on 2008-08-10
Hit Alt+F2 and type 'metacity --replace' (without the tick marks)

This will revert back to Metacity and let you fix any configuration mistakes you made.

---

### Post by Falc7 on 2008-08-10
Thanks very much, it worked great, i have another small question, how would i restart the computer using only the terminal?

---

### Post by SunnyRabbiera on 2008-08-10
> **Falc7 said:**
> Thanks very much, it worked great, i have another small question, how would i restart the computer using only the terminal?

sudo reboot
that will mainly shut it down, but its a start.

---

### Post by Falc7 on 2008-08-10
Thanks, i will try that.
I am trying to install an icon pack, how do i do it? 
I tried extracting the icons to .icons folder, but they didn't show up in system-> appearence-> theme->customise->icons



And also, my brother has customised his ubuntu abit, in his applications, places, system and right click menu, when he clicks them, there is a picture of a red plant or something behind the writing, how could i get this?

---

### Post by mcduck on 2008-08-11
> **SunnyRabbiera said:**
> sudo reboot
that will mainly shut it down, but its a start.

..Actually that will reboot. "sudo halt" would shut down.. ;)

(or "sudo shutdown -h now" to power off and "sudo shutdown -r now" for reboot. )

---

### Post by Falc7 on 2008-08-11
Any idea then on change the icons other visual element?

---

### Post by ThrobbingBrain66 on 2008-08-11
> **Falc7 said:**
> Any idea then on change the icons other visual element?

I'm not too sure on what you mean by the red plant...could you get a screenshot perhaps?

The icons are easy however.  You don't extract the archive at all.  Open the Appearance dialog is System > Preferences > Appearance and drag 'n drop the package.

---

### Post by Falc7 on 2008-08-11
I get the message: Icons does appear to be a valid theme
from this file
[http://gnome-look.org/content/show.php/BWS_Icons?content=83610](http://gnome-look.org/content/show.php/BWS_Icons?content=83610)
and also this one:
[http://kde-look.org/content/show.php/yellow+crystal+clear+icons+by+8siem?content=81095](http://kde-look.org/content/show.php/yellow+crystal+clear+icons+by+8siem?content=81095)

---

### Post by appi2012 on 2008-08-11
That is done through gtk themes. Try downloading them here:
[http://gnome-look.org/](http://gnome-look.org/)
Choose which ever one you like. You install them the same way you install icons. 

Some themes need certain engines to work properly. To install these engines, search for the engine name in gnome-look, click on it and then follow the instructions written in the description.

---

### Post by ThrobbingBrain66 on 2008-08-11
> **Falc7 said:**
> I get the message: Icons does appear to be a valid theme
from this file
[http://gnome-look.org/content/show.php/BWS_Icons?content=83610](http://gnome-look.org/content/show.php/BWS_Icons?content=83610)
and also this one:
[http://kde-look.org/content/show.php/yellow+crystal+clear+icons+by+8siem?content=81095](http://kde-look.org/content/show.php/yellow+crystal+clear+icons+by+8siem?content=81095)

The contents of the archive aren't in a valid format.  If you were to download any other icon set, you'd see that they should be in a variety of folders based on the icon size/type.

---

