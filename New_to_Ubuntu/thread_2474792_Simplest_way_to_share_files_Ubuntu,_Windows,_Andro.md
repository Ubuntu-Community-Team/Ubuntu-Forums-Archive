---
title: "Simplest way to share files Ubuntu, Windows, Android?"
date: 2022-05-08
forum: New to Ubuntu
---

### Post by yc2 on 2022-05-08
Which is the simplest way to share files between Ubuntu, Windows and Android phone, please?

Any detailed instructions would naturally be helpful but mostly I would like to know that I start installing the right stuff. Will e.g. SMB server be the easiest way to connent the three systems for file sharing?

Thank you.

---

### Post by yc2 on 2022-05-08
SMB installation seems OK. Ports 137 &#8211; 139 and 445 forwarded.

On the same Ubuntu computer:
```
smb://192.168.0.XYZ/sambashare
```
opens a panel for username and password
but entering credentials leads to
```
"failed to mount Windows share, no such file or directory"
```
From Windows computer I get the following after entering credentials (after server restart, not even the panel for credentials opens before the error message appears)
```
Windows can not access \\192.168.0.XYZ\sambashare
```

What am I doing wrong?

edit

```
computer-name:~$ smbclient -L usr@computer-name
do_connect: Connection to usr@computer-name failed (Error NT_STATUS_UNSUCCESSFUL)
```

more tests, server is ready
```
Status: "smbd: ready to serve connections..."
```

```
sudo pdbedit -L -v
```
will list my user

```
tree connect failed: NT_STATUS_BAD_NETWORK_NAME
```

```
drwxrwxr-x 10 usr usr     4096 maj  8 17:23 sambashare
```

```
[2022/05/08 19:01:54.327628,  0] ../../source3/param/loadparm.c:3428(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/sambashare failed. Permission denied
[2022/05/08 19:05:09.004400,  0] ../../source3/param/loadparm.c:3403(process_usershare_file)
  process_usershare_file: share name home/testuser/sambashare contains invalid characters (any of %<>*?|/\+=;:",)
[2022/05/08 19:05:15.841748,  0] ../../source3/param/loadparm.c:3428(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/home failed. Permission denied
```

---

### Post by ActionParsnip on 2022-05-08
SFTP imho, android can connect over the wifi using AndFTP and Windows can mount SFTP using extra tools or even FileZilla

---

### Post by douwe22 on 2022-11-23
Simplest way is to use zero-config feature:

Make sure Avahi service is running (should be on by default) (avahi-discover command should be able to run)
Default samba installation on latest Ubuntu 22.10  (not  sure this is needed anymore)
Install Bonjour SDK on Windows machine.
Go to installed directory and go to Control Panel. Fill out all the settings as you think is best.
Make sure the windows share/drive has 'Everyone' as its member under properties-->Security->group or members
Under advanced network sharing make sure discovery and file and printer sharing are both turned on.
Sometimes it helps to turn off password access under the network settings.
For good measure reboot bot machine

---

### Post by arieleoar on 2022-12-01
Hi!!

Other simplest way (in my opinion) could be [KDE connect]("https://kdeconnect.kde.org/download.html"). It has a windows version application, an app for android and an app preinstalled in KDE or a plugin that can be installed in GNOME ([https://extensions.gnome.org/extension/1319/gsconnect/](https://extensions.gnome.org/extension/1319/gsconnect/)).
After pairing the devices it'll allow you to transfer files, use your phone as mouse, control multimedia remotely, etc. Also it has the possibility to mount a folder from the other device into yout file system (like a disk).
Hope this helps.

Regards!

---

### Post by gileswalburn on 2022-12-01
I have several computers running, on several operating systems as I several apps and websites to test. I have always used [https://syncthing.net](https://syncthing.net), works great on a local network, along with a NAS like TrueNAS if you want too.

---

