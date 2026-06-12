---
title: "Can't Update 12.10"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Mossback on 2013-02-17
It has been awhile sincce I was in the system and ran a update. Everything seemed normal until I tried to install the updates. After a few seconds I got a message that the "Paackage System is Broken" and nothing installed. Should I get rid of the downloaded updates and start over (if so how do I do it) or is there a way to fix the downloads?

Thanks in advance for any assistance.

---

### Post by ibjsb4 on 2013-02-17
In terminal:

```
sudo apt-get update
```

Get any errors?

---

### Post by Mossback on 2013-02-17
It looks like the updates were downloaded. Should I update through the terminal or use the update manager.

I appreciate your help!!

---

### Post by ibjsb4 on 2013-02-17
Try update manager again, sometimes it just gets stuck and a terminal update will do the trick.

If it still will not work,  try installing the updates in terminal.

```
sudo apt-get upgrade
```

---

### Post by Mossback on 2013-02-17
The manager didn't work and I got the following details:

The following packages have unmet dependencies:

libqt4-dbus: Depends: libqt4-xml (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
             Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqt4-declarative: Depends: libqt4-network (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                    Depends: libqt4-script (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                    Depends: libqt4-sql (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                    Depends: libqt4-xmlpatterns (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                    Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
                    Depends: libqtgui4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
libqt4-designer: Depends: libqt4-script (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                 Depends: libqt4-xml (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
                 Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
                 Depends: libqtgui4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
libqt4-help: Depends: libqt4-network (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
             Depends: libqt4-sql (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
             Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
             Depends: libqtgui4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
libqt4-network: Depends: libqt4-dbus (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqt4-opengl: Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
               Depends: libqtgui4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
libqt4-qt3support: Depends: libqt4-designer (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                   Depends: libqt4-network (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                   Depends: libqt4-sql (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                   Depends: libqt4-xml (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
                   Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
                   Depends: libqtgui4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
libqt4-script: Depends: libqt4-dbus (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
               Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqt4-scripttools: Depends: libqt4-script (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                    Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
                    Depends: libqtgui4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
libqt4-sql: Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqt4-sql-mysql: Depends: libqt4-sql (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                  Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqt4-sql-sqlite: Depends: libqt4-sql (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                   Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqt4-svg: Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
            Depends: libqtgui4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
libqt4-test: Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqt4-xmlpatterns: Depends: libqt4-network (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
                    Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
libqtgui4: Depends: libqt4-declarative (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
           Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
qdbus: Depends: libqt4-dbus (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3.1 is installed
       Depends: libqt4-xml (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed
       Depends: libqtcore4 (= 4:4.8.3+dfsg-0ubuntu3.1) but 4:4.8.3+dfsg-0ubuntu3 is installed

Is the syntax "sudo apt-get update install" ?

---

### Post by ibjsb4 on 2013-02-17
sudo apt-get update

sudo apt-get upgrade

---

### Post by ibjsb4 on 2013-02-17
Try

```
sudo dpkg --configure -a

sudo apt-get -f install
```

---

### Post by Mossback on 2013-02-17
Good deal - it seemed to work. I ran the update manager again and got the reply that the software was up to date.

I guess I have a lot to learn before I tell Microsoft to "Shove It" :p

Thanks for your help.

---

