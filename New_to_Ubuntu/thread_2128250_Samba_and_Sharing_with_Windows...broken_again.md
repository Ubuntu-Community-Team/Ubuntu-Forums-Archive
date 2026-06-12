---
title: "Samba and Sharing with Windows...broken *again*?"
date: 2013-03-22
forum: New to Ubuntu
---

### Post by pablolie on 2013-03-22
OK, so after yet another kernel and samba update in 12.04 now my ability to share between Ubuntu and Windows is broken again, for no apparent reason. I go into Samba and it tells me the server is in WORKGROUP and description "%h server (Samba, Ubuntu)" - same as always, worked before. Only Ubuntu sees absolutely nothing in the Windows network. The "Personal File Sharing" thing continues to be a bad joke because the right packages are never installed - what's the point of even having it there? But that is a different matter. 

I uninstalled and re-installed Samba in case some sub-package was broken... still no luck.

Honestly this stuff seemed to work more reliably back in 10.04 and even 8.04. 

Any guides on how to troubleshoot Samba?

---

### Post by prodigy_ on 2013-03-22
Are you sure you didn't overwrite your your smb.conf during the update?

---

### Post by pablolie on 2013-03-23
Positively sure - it is still there.

---

### Post by pablolie on 2013-03-23
This issue may make me give up on using Ubuntu in my home network. It is getting too frustrating to synch media files.

I hope the Ubuntu community finds a way to make this more inituitive - the "Personal File Sharing" setup shoould be made to work. And Samba should be as easy as entering the Windows Workgroup name and be done. 

Based on every Samba guide I see (and there are many, and they are inconsistent) my setup should be working.

---

### Post by Morbius1 on 2013-03-23
From what information you posted it doesn't sound like a Samba issue but a Networking or a name resolution issue. There's an easy way to find out. Run the following command:
```
nautilus smb://192.168.0.100
```
[COLOR=#0000cd]*Change 192.168.0.100 to the ip address of the Windows machine. *[/COLOR]

If you can get through then Samba is working just fine.

As far a seeing your Windows machine by name in Nautilus there's really only a number of things that can get in the way:

** Can't browse by name unless all the machines are in the same subnet so check your ip addresses and see if they are in the same subnet.

** Some or all of the samba dependent services aren't running so check them and if they are not started start them:
```
sudo service smbd start
sudo service nmbd start
```
** Firewall is in the way so temporarily stop it:
```
sudo ufw disable
```
** The default mechanism to convert netbios names to ip addresses is being foiled by "wins".

Linux and Windows will both default to broadcasting their names to one another but on Linux it gets messed up but Samba allows you to prioritize this by adding an option - right under the workgroup line in /etc/samba/smb.conf:```

name resolve order = bcast host lmhosts wins
```
Then restart smbd and nmbd again.

But I tell you life is short so if you keep having issues with Samba / Networking then why not set the Windows machine to have a static ip address and access it that way. You can bookmark it in Nautilus when you get access so you don't have to remember it's address. 

I just set up a home network for someone with Win / Lin / OSX / iOS  components and the easiest thing is to add the following utility to the Windows machine: [http://support.apple.com/kb/DL999](http://support.apple.com/kb/DL999) . And make sure port [COLOR=#000000]5353/udp is open.[/COLOR]

Despite it's name what it does is install the Windows equivalent of Avahi ( Bonjour in Apple products ). From that point on you access it by it's host-name.local regardless of it's ip address at that moment and then bookmark that if you want:
```
nautlus smb://host-name.local
```
Linux and OSX respond to *.local queries by default and with the added package so will Windows.

---

### Post by Morbius1 on 2013-03-23
ERROR - for the life of me I can't figure out how to delete this extra post.

---

