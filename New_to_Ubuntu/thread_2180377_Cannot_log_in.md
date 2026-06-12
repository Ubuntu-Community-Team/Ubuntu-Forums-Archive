---
title: "Cannot log in"
date: 2013-10-12
forum: New to Ubuntu
---

### Post by andrew-whitcomb on 2013-10-12
Hello,

When I installed Ubuntu 13.04, I selected the option to automatically log me in without password when the computer boots.  However, I now get a prompt to log in via either my user password, guest login, or remote login.  When I type my password in, the screen flashes and I get the "drumroll" sound and am returned to the same login page.  When I type my password incorrectly, I am notified that the password is incorrect.  I am currently using my computer via guest session.

The only thing I can think of that changed recently was me installing xrdp.

Can anyone help me log in?

---

### Post by andrew-whitcomb on 2013-10-12
Update:  I can log into the console via Ctrl+Alt+F1 but "startx" from there does not fully launch things like the bar.

---

### Post by andrew-whitcomb on 2013-10-12
This was resolved with "sudo apt-get install --reinstall ubuntu-desktop"

---

