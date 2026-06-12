---
title: "[SOLVED] Missing Firefox plugin"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by unknown user on 2008-09-23
I am trying to view this page on my Ubuntu system ([http://www.coastalwatch.com/camera/cameras_large.aspx?cam=7030&state=WA](http://www.coastalwatch.com/camera/cameras_large.aspx?cam=7030&state=WA)) but my firefox is telling me that I have a plugin missing.  I click on the Install Missing Plugin button and I get a box says No Suitable Plugins Found - Unknown Plugin (Application/x-mplayer2).

Can anyone help me find the plugin that I need so I can view the surf cam.

---

### Post by mrtomcef on 2008-09-23
On the right hand side of the page I selected to view the surfcam in low quality java. Then, when the missing plugins came up I selected find plugin and it directed me to install a java plugin.

---

### Post by nowshining on 2008-09-23
look thru synaptic and find the mplayer firefox plugin install it and it should also install mplayer- restart firefox and try again..this time it should work fine..

---

### Post by unknown user on 2008-09-23
The one I want is hiWin as that is live feed.

nowshining I did what you suggested but this has not worked.

---

### Post by nowshining on 2008-09-25
> **unknown user said:**
> The one I want is hiWin as that is live feed.

nowshining I did what you suggested but this has not worked.

okay i found a way to do it, open up nautilus as root and create a symbolic link or copy all files from /usr/lib/mozilla/plugins/ (all files) to /home/username/.mozilla/plugins/ - restart the browser and all should be well. :)

---

### Post by philinux on 2008-09-25
Ive got a default install plus ubuntu-restricted-extras and I got it to work like this.

Go to home page, make sure accept cookies is on or whitelist the site. Then browse to selected cam. It loads totem embedded video player and plays. Mind you  the one I picked must be pitch black there now, time diff. But it streamed.

---

### Post by unknown user on 2008-09-26
Guys I will do this later tonight when I get home and see if they work, thanks for the help.
I have had a look on the net and found this site ([http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)) not sure if it will work, but wondered if any one has seen it or used it.
I will have a bash when I get home.

---

### Post by nowshining on 2008-09-26
> **unknown user said:**
> Guys I will do this later tonight when I get home and see if they work, thanks for the help.
I have had a look on the net and found this site ([http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)) not sure if it will work, but wondered if any one has seen it or used it.
I will have a bash when I get home.

ummm that's the same thing i suggested to install from the repos :) it didn't work for me eitehr until i told u the instructions above on my last post..

---

### Post by unknown user on 2008-09-30
I will be trying this today in the hope of getting it working as I love the live beach feeds

---

### Post by unknown user on 2008-10-01
All working guys, thanks for your help, I can not watch the sea on my Ubuntu system

---

