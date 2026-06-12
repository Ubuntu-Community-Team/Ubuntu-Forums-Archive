---
title: "Where is &quot;Remote Desktop&quot; settings icon in Xubuntu"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by swarup on 2008-05-15
I use both Ubuntu and Xubuntu Hardy. In Ubuntu, under "Preferences", there is a tab for "Remote Desktop" which when clicked on, gives options for whether one opts to have this computer available for use by others as a remote desktop, whether a password is needed for access, and whether they have only access to see the screen or can also control the mouse. 

Where is that "Remote Desktop" tab located on the Xubuntu desktop? I looked under "Settings" as well as in the "Settings Manager" and could not find it. When in Xubuntu I go to Applications->Settings->Main Menu, I can see under System->Preferences that this "Remote Desktop" tab is selected to be showing. And according to my understanding, on the Xubuntu desktop it should show under Applications->Settings. But it is not there. In Ubuntu of course, there is a System->Preferences icon right on the upper panel, whereas in Xubuntu that Preferences menu seems to be located under Applications->Settings. But the "Remote Desktop" tab is not included there. So how can I bring up "Remote Desktop" options in Xubuntu?

---

### Post by Monicker on 2008-05-15
afaik, xubuntu does not have an integrated Remote Desktop feature.  That is a gnome implementation of a vnc server.  You can manually set one up though.

[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html")

---

### Post by swarup on 2008-05-15
> **Monicker said:**
> afaik, xubuntu does not have an integrated Remote Desktop feature.  That is a gnome implementation of a vnc server.  You can manually set one up though.

[http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html")

Hey, thanks. I've just read through the link you gave and it is extremely informative. 

One question: My original install on this laptop is actually Ubuntu Hardy. I then added Xubuntu and it runs when I opt to go into it as a session. My question is, that all the software as well as settings from Ubuntu have transferred automatically over to Xubuntu-- such as wireless setup, email, etc etc. So wouldn't the settings of the Remote Desktop feature have ported over as well? Someone tried to connect with me, and they didn't see my computer as being available until I rebooted into an Ubuntu session and then it worked fine. 

So does it sound then, like I'll to go ahead and follow the fairly extensive procedure listed on that blog? Or should there be an easy way to do it since it is already set up on this computer through Ubuntu?

---

### Post by Monicker on 2008-05-15
Since its integrated into the gnome desktop environment, I don't think you can run it from directly from the xfce environment which xubuntu uses.

You might try running vino from a terminal and seeing what happens, as I believe that is the actual application name for what they label as Remote Desktop.

---

