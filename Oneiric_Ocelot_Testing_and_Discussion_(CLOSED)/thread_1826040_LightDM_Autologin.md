---
title: "LightDM Autologin?"
date: 2011-08-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ojdon on 2011-08-16
Hi there, I'm just wondering if the method of getting LightDM to autologin has changed? If anybody is successfully automatically logging in could you post how you achieved it?

Thanks!

---

### Post by pjnsmb on 2011-08-16
> **ojdon said:**
> Hi there, I'm just wondering if the method of getting LightDM to autologin has changed? If anybody is successfully automatically logging in could you post how you achieved it?

Thanks!

[http://ubuntuforums.org/showthread.php?t=1815410&highlight=autologin](http://ubuntuforums.org/showthread.php?t=1815410&highlight=autologin)

point #2 has started working for me

---

### Post by Ichtyandr on 2011-08-16
according to [[COLOR="DarkOrange"]this bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/819624") /etc/lightdm/lightdm.conf is empty and cannot be relied upon

---

### Post by Ichtyandr on 2011-08-24
> **ojdon said:**
> Hi there, I'm just wondering if the method of getting LightDM to autologin has changed? If anybody is successfully automatically logging in could you post how you achieved it?

Thanks!

OK so when I checked lately autologin could be set from "power cog" >system settings> user accounts > your username > automatic login

Then I remembered this post and just in case decided to post it, better late than never

---

### Post by cariboo on 2011-08-24
Does going to System Settings -> Users, then setting Autologin to On work?

---

### Post by Ichtyandr on 2011-08-24
> **cariboo907 said:**
> Does going to System Settings -> Users, then setting Autologin to On work?

In my case its been working for several days already. It shows that autologin is "off" but still works after you "unlock" with password and set to "on" and then reboot.

---

### Post by Quackers on 2011-08-24
I just changed that setting and rebooted. It auto logged me in, but to fallback mode. I logged out and back in to gnome-shell. The auto login had reset itself to OFF again.
Maybe it's not working with gnome-shell.

---

### Post by meborc on 2011-08-24
> **Quackers said:**
> I just changed that setting and rebooted. It auto logged me in, but to fallback mode. I logged out and back in to gnome-shell. The auto login had reset itself to OFF again.
Maybe it's not working with gnome-shell.

I don't have GS installed and autologin works just as expected - loading the normal 3D Unity interface

---

