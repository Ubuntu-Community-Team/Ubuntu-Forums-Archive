---
title: "Deluge Permission denied"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by jaminben on 2014-02-16
[SIZE=2]Hi,

I'm trying to get Deluge running with Flexget and almost have it working except that Deluge doesn't download anything. When looking at Deluge Web-UI > Details > Status it reports: [COLOR=#000000][FONT=arial]Permission denied: /media/sdc1/Torrents/TorrentFilesNew/{torrentName}

I followed this guide: [http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=arial]

When I run:
[/FONT][/COLOR][/SIZE]```
ls -l /media/sdc1/Torrents/TorrentFilesNew
```[SIZE=2][COLOR=#000000][FONT=arial]
It returns:
[/FONT][/COLOR][/SIZE]```
-rwxrwxrwx 1 deluge deluge  5691 Feb 15 09:45
```[COLOR=#000000][FONT=arial]
Can anyone offer any help please.

Thanks

Ben

[/FONT][/COLOR]

---

### Post by sandyd on 2014-02-16
> **jaminben said:**
> [SIZE=2]Hi,

I'm trying to get Deluge running with Flexget and almost have it working except that Deluge doesn't download anything. When looking at Deluge Web-UI > Details > Status it reports: [COLOR=#000000][FONT=arial]Permission denied: /media/sdc1/Torrents/TorrentFilesNew/{torrentName}

I followed this guide: [http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html](http://www.havetheknowhow.com/Install-the-software/Install-Deluge-Headless.html)[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=#000000][FONT=arial]

When I run:
[/FONT][/COLOR][/SIZE]```
ls -l /media/sdc1/Torrents/TorrentFilesNew
```[SIZE=2][COLOR=#000000][FONT=arial]
It returns:
[/FONT][/COLOR][/SIZE]```
-rwxrwxrwx 1 deluge deluge  5691 Feb 15 09:45
```[COLOR=#000000][FONT=arial]
Can anyone offer any help please.

Thanks

Ben

[/FONT][/COLOR]

does deluge have +x permissions for the folders that TorrentFilesNew is contained in
Deluge must have permissions to read all the folders it is contained in (i.e. /media, /media/sdc1, /media/sdc1/Torrents)

---

### Post by jaminben on 2014-02-16
Ah, no it does not... how would I do that without removing the original owners permissions?

Thanks

[B]Edit:
[/B]

For instance if I do: ls -l /media 

The Deluge user doesn't have permissions.

[B]Edit 2:
[/B]
I added the Deluge user to the owners group and its now working... not sure if that was the correct thing to do but it works for now.

Thanks Again :P

---

