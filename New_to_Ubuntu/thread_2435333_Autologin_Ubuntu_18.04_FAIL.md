---
title: "Autologin Ubuntu 18.04 FAIL"
date: 2020-01-19
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2020-01-19
At this point I have tried LightDM and GDM3 as provided. I've followed a few guides. All guides auto login. However nothing I do makes them go to Openbox. They always go to Ubuntu session. I've tried the .dmrc, I've tried lightdm.conf.d/config.conf user-session. It just doesn't work. I have tried the /etc/gdm3/custom.conf and it doesn't respect the timed wait before auto login, nor does it go to Openbox. Instead preferring Ubuntu default.. I'm quite frustrated and this is a big problem at the moment.  I'm hoping someone has an answer.

---

### Post by guiverc on 2020-01-19
Have you tried logging out of *Ubuntu default*, then logging in to your wanted Openbox?   Your box maybe auto-logging into the last session used..

---

### Post by Tadaen_Sylvermane on 2020-01-19
I have. Just now I changed /var/lib/AccountService/users/kodimain to openbox. Changed .dmrc to openbox, and added user-session=openbox to my lightdm.conf file. I powered down and turned it back on.
All but the lightdm file say Ubuntu now. It's getting this from somewhere but I cannot figure it out. And of course it's back in Ubuntu.

---

### Post by Tadaen_Sylvermane on 2020-01-20
I found another way to accomplish my goal. I was trying to make a solution for pxe bootable clients work on a full bare metal install, and got nowhere. Instead of having multiple users I just autologin a single user with GDM and just have a script to autostart my media center. This allows us to exit and use as normal, or load media center back up with no trouble. actually better solution than previous when it was a pxe booted machine.

---

