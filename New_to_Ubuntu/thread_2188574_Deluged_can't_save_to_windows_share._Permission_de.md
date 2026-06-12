---
title: "Deluged can't save to windows share. Permission denied. help"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by nasser4life on 2013-11-17
I created an Ubuntu Server, LAMP setup using 12.04 with VMWare 10 on Windows 8.1
Installed Deluged, Deluge-web, sabnzbd+ and CouchPotato.
This is my second go at this and first time around I was able to connect couchpotato to Deluge. 

Not anymore with this setup.
[http://dev.deluge-torrent.org/wiki/UserGuide/InitScript/Ubuntu%2011.04%2B%20(Upstart%20Job)](http://dev.deluge-torrent.org/wiki/UserGuide/InitScript/Ubuntu%2011.04%2B%20(Upstart%20Job))

Also I've setup deluged to save to this windows share I created with these permissions. That was after doing the default setup following the guide.
```
//servername/sharename /media/windowsshare cifs credentials=/home/ubuntuusername/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
The correct windows username/password is stored in the credentials file.
The Windows user has full control set under permissions on Windows.
Tested and able to save to the shared folder using WinSCP via SFTP and also from the terminal.

The Deluged setup was done using a new user and I believe is restricted to the one folder.
I wanted to know how to go about changing these settings to get pass this permission denied whenever i try downloading a torrent.
Maybe a little help on running this on as my logged on user instead of 'deluge'. Wasn't sure about the settings and the group I should use in the .conf files. Or how do I go about giving 'deluge' user access to the share I created.
Any help would be much appreciated. Sooner or later I'll figure out how to get couchpotato connect to it as well.

---

