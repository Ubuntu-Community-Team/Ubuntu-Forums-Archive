---
title: "My PATH + unbuntu is broken"
date: 2020-02-15
forum: New to Ubuntu
---

### Post by zeus2705 on 2020-02-15
Hello,

I was stuck in a log in loop so I used alt+crtl+f3 to log in. Then the path was broken so I used "export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games" to reset the path I do not have a .Xauthority so I just ran "startx" to launch the desktop. The first thing the desktop is not exactly the same and no icon on the file explorer only name.


[https://image.noelshack.com/fichiers/2020/07/6/1581768535-capture-d-ecran-de-2020-02-15-13-03-43.png](https://image.noelshack.com/fichiers/2020/07/6/1581768535-capture-d-ecran-de-2020-02-15-13-03-43.png)

So I decide to use boot-repair and I got that [http://paste.ubuntu.com/p/gdNysYHCRb/](http://paste.ubuntu.com/p/gdNysYHCRb/)




After the reboot, I was stuck again on the log in a loop so I did the same thing to log (PATH was not modified) even after I ran (source /etc/environment)




But nothing has changed Please Help me

---

### Post by jeremy31 on 2020-02-15
Moved to New to Ubuntu, restored original font/color and removed image tags as it is a larger image

---

### Post by cmcanulty on 2020-02-15
The password loop seems to be fairly common lately. Here is a solution from the web that doesn't mess up your system at all. It says lost password but works to stop the password loop also. You can use the same password you had originally. I hope someone will fix this bug.

[https://linuxconfig.org/how-to-reset-lost-root-password-on-ubuntu-18-04-bionic-beaver-linux]("https://linuxconfig.org/how-to-reset-lost-root-password-on-ubuntu-18-04-bionic-beaver-linux")

---

### Post by zeus2705 on 2020-02-16
[https://linuxconfig.org/how-to-reset...c-beaver-linux]("https://linuxconfig.org/how-to-reset-lost-root-password-on-ubuntu-18-04-bionic-beaver-linux") :  I m stuck at the first step after editing GRUB f10 or ctr+x doesn't boot ubuntu just a purple screen with no interaction

---

### Post by cmcanulty on 2020-02-16
That threw me at first too. Basically after the edit grub just look for the entry

```
ro   quiet splash $vt_handoff
```

 then carefully delete that text and replace it with

```
rw init=/bin/bash
```

then follow the other steps

This may be an easier path to try:

[https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/]("https://websiteforstudents.com/reset-forgotten-ubuntu-user-password-on-ubuntu-16-04-17-10-18-04/")

---

