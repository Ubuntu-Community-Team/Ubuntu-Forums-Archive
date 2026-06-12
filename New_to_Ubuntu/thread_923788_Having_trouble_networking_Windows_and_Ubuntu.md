---
title: "Having trouble networking Windows and Ubuntu"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by modman27 on 2008-09-18
I cannot figure out how to network my xp box to my ubuntu box. I have samba installed. I went in the config file and changed the workgroup to be the same. They are on the same subnet, but yet my shared folders do not show on the XP box. Any thoughts???

---

### Post by Zzl1xndd on 2008-09-18
Are you able to see your Windows shares on the Linux box?

---

### Post by modman27 on 2008-09-18
Well I have xp home and I could be wrong but i dont think that it allows you to share folders. I also was thinking that I have a firewall installed, I think watchdog. Do you think that may be part of the problem?

---

### Post by Zzl1xndd on 2008-09-18
Could be Firestarter Blocks my ability to view shares, try disabling the firewall. Also Windows XP home can share files so give it a try.

---

### Post by Locutus_of_Borg on 2008-09-18
when you say your shared folders do not appear on XP...you have gone to My Computer > Tools > Map Network drive then input the ip and folder correctly?
e.g. for /home/name/windows_shared on address 127.0.0.1, you would fill in \\127.0.0.1\windows_shared


If it connects, the box will just disappear and you have to put in the drive letter you chose into the navigation bar of explorer, after that, it will appear in your network locations in My Computer

---

### Post by modman27 on 2008-09-18
I shared out a folder in xp box, cannot see it from the linux box. I tried mapping the drive and it asked for a password. Entered my su password with no results. I allowed for guest access on the linux share as well still with no results. ???

---

### Post by haydnc on 2008-09-18
Are you trying to access the shares on the Ubuntu box by IP address or by the 'name' of the Ubuntu box? If the latter you need to install Winbind (from memory) to translate IP addresses into human readable names for your machines... there might be some other things you need to do too, I can't recall but these forums should be able to help you out there.

If you're accessing data on the windows box from ubuntu don't forget you need to browse using samba: smb://windows machine name or ip/share name
If you're trying to go the other way - windows views linux - use \\linux machine name or ip\share name

If you're just using IP address as suggested by Locutus_of_Borg then it's more likely that you've got a firewall somewhere killing your data transfers. Try disabling firewalls all around to see if that's where the problem lies. If you can narrow it down to a firewall problem you can usually set up firewall rules to allow all traffic on your internal network.

It's also possible it's an authentication thing. I seem to remember needing to modify /etc/samba/smb.conf which contains a line about security, usually something like security = user.
If memory serves me well, to get windows and ubuntu playing nice together you need to change that to security = share (that's the easiest way I've found anyway).

People will probably be upset at you if you do that last one as it erodes the network security of your ubuntu machine, however since I've not discovered any truly easy way to get a windows machine and a Ubuntu machine to play nicely together without doing it, you might want to consider it as an option.

I forgot to add

---

### Post by modman27 on 2008-09-18
Figured it out...It was a firewall issue. Thanks for the help!

---

### Post by Another Monkey on 2008-09-20
What was the firewall issue?

I cannot get networking between Windows and Ubuntu going.

Network Wizard has been run on windows, all services are running, TCP-IP looks correct, NetBIOS is enabled, firewall trusts local network, shares exist.

Samba is running, shares exist, no firewall.

Both connected to the same router, on the same subnet, in the same workgroup.  They can ping each other OK and I can use //192.168.1.1/some_share and that works, but going through File Browser on Ubuntu or Explorer on Windows, nothing.  It's just empty on Ubuntu and errors on Windows.

What's strange is that if I take my Ubuntu laptop into work (which is all Windows) it works perfectly, sees all servers and shares in the File Browser.  ARGH!

It is doing my head in.

---

