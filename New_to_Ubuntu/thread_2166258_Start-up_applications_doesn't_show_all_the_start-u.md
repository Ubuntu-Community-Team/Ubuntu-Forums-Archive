---
title: "Start-up applications doesn't show all the start-up apps"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-08-08
Hello all!

I used to have an Ubuntu 9.04 Jaunty installation. In the terminal I would type:

```
gnome-session-properties
```

and I could modify and/or remove system start-up applications

However, since it was an EOL, I decided to upgrade to the latest Ubuntu version. Now I type the same thing, and It just asks me to add a new Start-up application. How can I get the "old" list, that lists **_all_**&#8203; start-up applications, as I am working to make brand-new session based on the default ubuntu session?

---

### Post by deadflowr on 2013-08-08
Run this
```
sudo sed -i "s/NoDisplay=true/NoDisplay=false/g" /etc/xdg/autostart/*.desktop


```

Then open up start up applications again.
All the programs system-wide launched at start will be listed.

The reason the start-up applications is empty is that it now only lists the user's start-ups.

---

### Post by SweetAurora on 2013-08-08
In a terminal type:
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```
that will make the Start-up Applications Manager show all start-up apps.

But I warn you, be VERY **[SIZE=3]VERY!!![/SIZE] [SIZE=4]CAREFULL!!![/SIZE]** Most of the applications listed for start-up are **MANDITORY **and could cause Ubuntu to not load a desktop after login. They were hidden for a reason.

But things I found safe to turn off.
Backup Manager
Chat
Desktop Sharing
Onboard
Orca
Personal File Sharing
Ubuntu ONE

---

### Post by Werne on 2013-08-08
> **kitsuneinari78 said:**
> Most of the applications listed for start-up are **MANDITORY **and could cause Ubuntu to not load a desktop after login. They were hidden for a reason.
If I recall correctly, only the Files and some startup applications related to gnome-session would cause Ubuntu not to load the desktop, and I think there's only a few of those capable of messing up the desktop or do anything harmful. The rest is that Chat/UbuntuOne/Update Manager stuff and bluetooth, network manager, Orca, Onboard, etc.

---

### Post by righttechnology on 2014-07-25
this will reveal the hidden apps too... in (Ubuntu 14.04) 
this worked for me anyway :)

sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*

---

### Post by Jonathan Precise on 2014-08-08
Thank you all! Marked as solved.

Sorry for not replying sooner. I've been very busy.

---

