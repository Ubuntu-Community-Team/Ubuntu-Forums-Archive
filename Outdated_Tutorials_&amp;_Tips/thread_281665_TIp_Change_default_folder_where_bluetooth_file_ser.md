---
title: "TIp: Change default folder where bluetooth file server saves the files"
date: 2006-10-21
forum: Outdated Tutorials &amp; Tips
---

### Post by Nailor on 2006-10-21
In Dapper, Gnome Bluetooth File Server works fine, except that you can't control where it saves the files sent via bluetooth. As default, the files go to user's home folder.

This can be changed, and here's a small howto:

Create a new gconf folder:
```

mkdir ~/.gconf/apps/gnome-obex-server

```
And make inside that folder file named %gconf.xml (remember the %).
Insert to that file
```

<?xml version="1.0"?>
<gconf>
        <entry name="receive_notification" mtime="1161434653" type="bool" value="true">
        </entry>
        <entry name="savedir" mtime="1144755883" type="string">
                <stringvalue>/home/USERNAME/bluetooth</stringvalue>
        </entry>
</gconf>

```

This file tells the Bluetooth File Server that files should be saved in directory /home/USERNAME/bluetooth and that it should show a notification when a file is received.

Now, restart Gdm (or logout and login again) and the program should work. Later on, you can change the directory and the receive_notification value via gconf by starting gconf-editor and going to /apps/gnome-obex-server/

---

