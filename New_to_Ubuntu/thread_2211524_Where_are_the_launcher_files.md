---
title: "Where are the launcher files?"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by robert48 on 2014-03-16
Hi

I am running Qcad Pro and I can start it from the dash and make the icon persist in the laucher when i close down Qcad. However, when I reboot the icon disappears. I'm all for the launcher but would like better control. Where can I find the directory(s) that hold the icon files and scripts for start up?

---

### Post by deadflowr on 2014-03-16
Launcher files sit in one of two places, generally.

the system folder
/usr/share/applications.

and the user folder
/home/user/.local/share/applications

the user folder .local is hidden by default, so you need to enable show hidden to view it in the file manager.

---

### Post by robert48 on 2014-03-16
Thank you!

Qcad was in /home/user/opt/qcad-3.4.6-pro-linux-x86_64
Everything else that appears in the launcher is in /usr/share/applications

I put the 'launcher' file into /user/share/applications and now i have icon in launcher and it persists between boots.

Many thanks again
Bob

---

