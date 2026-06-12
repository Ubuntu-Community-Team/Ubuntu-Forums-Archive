---
title: "Mapping an network drive"
date: 2013-02-16
forum: New to Ubuntu
---

### Post by SadiesPoppa on 2013-02-16
):P So far, I am quite pleased with Xubuntu. Actually VERY pleased and thinking losing the Windows restore disks for my HP Mini was a good thing. I'm gradually getting things set up (printers, email, WiFi etc). Right now, I need to be able to map the wireless external hard & drive the family shares. I read another post about doing it with a URL & nautilus file manager but somehow I'm not getting it.

---

### Post by MoebusNet on 2013-02-16
I don't use remote drives, but I did find this if you haven't looked at it yet:

[http://askubuntu.com/questions/200753/how-to-mount-a-network-drive](http://askubuntu.com/questions/200753/how-to-mount-a-network-drive)

I've seen 'Gigolo' mentioned favorably a couple of different times (bottom of the linked page) and 'Gigolo' is supposed to be in the Software Center so it might be worth a look.

---

### Post by DuckHook on 2013-02-17
Welcome to the forums.

Need more info before we can help you. Are your family shares Windows shares? Why are you using Nautilus? The default file manager in Xubuntu is Thunar. Did you try Gigolo?

By installing Nautilus, you dragged down a ton of gnome dependencies and are likely halfway to having a gnome or Unity desktop by now. If you are okay with this, then no harm done, but Gigolo should have been quite sufficient (and easy) for connection.

---

### Post by Merrattic on 2013-02-17
Sounds like you need to install samba and setup the shares from your HP mini to be available over the network. I presume that your external HDD and the partitions/folders on it are already appearing on your HP mini? Maybe some work required in /etc/fstab as well.

---

### Post by SeijiSensei on 2013-02-17
Some file managers allow you to use smb:// URLs in the address bar to mount Windows shares.  I'm pretty sure Nautilus supports this; I know KDE dolphin does.  I haven't used thunar in a very long time, so I can't say about that one.

Try entering smb://winservername/sharename/ in the address bar and see if you get prompted for login credentials.  If it complains that it can't find "winservername" edit the file /etc/hosts with "sudo nano /etc/hosts" and add a line to the file like this:

```
10.10.10.10    winservername
```

replacing 10.10.10.10 and "winservername" with the actual IP address and name of the machine that shares the external drive.

You can tell Ubuntu to mount a remote Windows share permanently when the network comes up by adding an entry in /etc/fstab.  See [this document]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") for details.

---

### Post by SadiesPoppa on 2013-02-17
> **MoebusNet said:**
> I don't use remote drives, but I did find this if you haven't looked at it yet:

[http://askubuntu.com/questions/200753/how-to-mount-a-network-drive](http://askubuntu.com/questions/200753/how-to-mount-a-network-drive)

I've seen 'Gigolo' mentioned favorably a couple of different times (bottom of the linked page) and 'Gigolo' is supposed to be in the Software Center so it might be worth a look.

Well, I can see it on the network now.Just need to figure out how to access it so I can use it for back up. There are 3 other PC's in the house and all are running Windows 7.Getting there with all the help. THANK YOU ALL ):P ! Sad how lazy Windows has made me.

---

### Post by SadiesPoppa on 2013-02-17
I used this tutorial and apparently it worked and I just didn't realize it. Almost there. This experience has been awesome so far. I'm learning again and everyone has been most helpful. Now to figure out what else I don't know bwahahahaha!

---

