---
title: "No restart or ON/OFF button in Unity"
date: 2011-06-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2011-06-24
Hello,

I am running Natty 11.04 i386 on a desktop PC.  After today's update, I notice that in Unity2d, the title bar on top only has 3 icons: NetworkManager, Printer Status and Sound settings.  I cannot find the icon representing ON/OFF or restart/shutdown switch anywhere. The login page has a humanity icon and the ON/OFF switch though.

Any suggestions for fixing this problem?

Thanks a lot for your help.

---

### Post by iClouseau88 on 2011-06-24
Hi again,

I found that indicator-session but not indicator-session-gtk2 was installed. After installing the latter, I got the ON/OFF icon back.

Now, the NetworkManager icon is still a red X on a white button.  How do I fix this? Otherwise, NM is still functioning.

Thanks in advance for your help.

---

### Post by fjgaude on 2011-06-24
You mean 11.10, eh?

I lost my keyboard and mouse with 24 June daily... it's Alpha.

---

### Post by terry_gardener on 2011-06-24
> **iClouseau88 said:**
> Hi again,

I found that indicator-session but not indicator-session-gtk2 was installed. After installing the latter, I got the ON/OFF icon back.

Now, the NetworkManager icon is still a red X on a white button.  How do I fix this? Otherwise, NM is still functioning.

Thanks in advance for your help.

in synaptic do a search for indicator and then install.
indicator-applications-gtk2 
indicator-messages-gtk2
indicator-session-gtk2 

to get back all the default icons

---

### Post by iClouseau88 on 2011-06-24
Hello,

In addition to indicator-messages-gtk2,I also installed indicator-datetime-gtk2, indicator-appmenu-gtk2 and appmenu-gtk.  Now everything is back to normal.

Thanks for your suggestions.

---

### Post by jerrylamos on 2011-06-25
24 June Daily Build Oneiric Ocelot has the indicators back including restart, shutdown, etc.

Jerry

---

