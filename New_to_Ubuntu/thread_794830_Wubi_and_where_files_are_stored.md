---
title: "Wubi and where files are stored"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-05-15
I've installed Ubuntu 8.04 through Wubi. Now, I know where to go to access all my files that are held on my Windows side. But...where are all the files installed to when I install something on the Linux side?

For example. I've installed Wine and uTorrent. Now, when I use Opera and just click on a torrent link, Opera can't open it directly into uTorrent. I get an error message.

When I right click on the uTorrent icon that is on my desktop, and hit Properties, the menu tells me that uTorrents location is in home/my name/desktop.

So, when I've put this location into Opera(and just to let you know I've disabled Opera's bittorrent client, so it's not that that's causing the problem), so it will open torrents directly in uTorrent, I still get this error message. Which the error message is: 

'/home/my name/Desktop/µTorrent.desktop' No such file or directory

So, what directory was uTorrent installed in? I've been browsing around, and I can't find it. And keep in my mind that I'm totally new to Linux. I'm so used to Windows. Just clicking on Program Files, and all my programs are displayed. So the more detailed you can be on where my programs are installed in Linux the better. I need to find out what directory uTorrent was installed in, so I can input this directory into Opera.

Thank you for any help.

---

### Post by EXCiD3 on 2008-05-15
utorrent.desktop is just a file containing information for the shortcut. It is not actually uTorrent itself. I'm assuming you installed uTorrent in wine. I don't know how you would setup utorrent to load the files. Wine is located at ~/.wine/drive_c/windows/  You should be able to find uTorrent there could rig up a link to it that Opera could send the torrents to. I would recommend you use a native linux torrent client. Deluge is a very nice one and has the same sort of look and feel of uTorrent. You should give it a shot first.

---

### Post by h8uthemost on 2008-05-15
Nah...it still doesn't work. I guess there's no way to make this happen since uTorrent is on a virtual harddrive.

And I would use Deluge, I like better than uTorrent actually. But some of a the private torrent sites that I belong to don't allow it. And every one of them allow uTorrent. So for right now it's just easier for me to use uTorrent.

Thanks for the help.

EDIT: Ok, actually I'm going to try transmission. Now that was already installed. So what directory would that be in?

Thank you.

---

### Post by EXCiD3 on 2008-05-15
If you open terminal you can do```
locate transmission
``` to have it find the directory where it is installed. Not everything has the same install location so you can use the locate command to find them. Most applications users install are stored in the /usr/bin folder.

---

