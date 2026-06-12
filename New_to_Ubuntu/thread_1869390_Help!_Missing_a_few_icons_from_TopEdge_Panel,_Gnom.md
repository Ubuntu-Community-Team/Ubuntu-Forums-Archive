---
title: "Help! Missing a few icons from TopEdge Panel, Gnome2.30.2"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by RotorRick on 2011-10-25
Help! Missing a few icons from TopEdge Panel, Gnome2.30.2, Ubuntu 10.04LTS

Ok, I just did a restart half hour ago, and found that the icons in the top edge panel, on the righthand side corner, were not in my usual prefered layout (volume on far left, shutdown on far right). So I tried mucking about to change their locations, and seem to have ended up "disappearing" them better than the KGB!

 Now I know they aren't deleted, but I've no idea how to bring them back onto that top panel. 
The ones I'm missing are:

Volume control
network status

in  Gnome2.30.2,
 Ubuntu 10.04LTS

Thanks!!:popcorn:

---

### Post by LinuxFan999 on 2011-10-25
I have 2 questions.

1. Do you have the latest updates?

2. Could you please upload some screenshots of your problem?

---

### Post by RotorRick on 2011-10-25
I think all I need is to re-activate these:

[B]Notification Area applet
Volume Control applet[/B]

---

### Post by ajgreeny on 2011-10-25
> **RotorRick said:**
> I think all I need is to re-activate these:

[B]Notification Area applet
Volume Control applet[/B]
The volume control is now part of the **indicator-applet**, not a stand-alone as it used to be, the network status is in the repos as **gnome-netstatus-applet**, but I think you may mean the **network-manager-applet** is missing, which is part of the **notification area**.

More details needed.

---

### Post by RotorRick on 2011-10-25
> **ajgreeny said:**
> The volume control is now part of the **indicator-applet**, not a stand-alone as it used to be, the network status is in the repos as **gnome-netstatus-applet**, but I think you may mean the **network-manager-applet** is missing, which is part of the **notification area**.

More details needed.


So...how do I get those running again? Do I just copy/paste " **indicator-applet" **into terminal and hit enter?

Or is there some menu I'm not seeing?

---

### Post by RotorRick on 2011-10-25
Ok, so I just _**Right-clicked on the panel**_, selected 

[B]Add To Panel

[/B]and then started trying various applications. I found all the ones I've been missing for the last few hours, 

[B]Indicator Applet
NetworkManager Applet[/B]

but also found several others I prefer too. For instance:

[B]Search for Files
Force Quit
Shut Down
Sticky Notes [/B](probably won't use that one much, but never know)
[B]Tomboy Notes

[/B]Then I selected for them to "**Move**" to place them where I want them to appear, and then I right-clicked on them again and selected "**Lock to panel**". That should solve my issue, and now we know what I was doing wrong!

---

