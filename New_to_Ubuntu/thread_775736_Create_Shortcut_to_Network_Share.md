---
title: "Create Shortcut to Network Share"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by dover19 on 2008-04-30
I can't figure out a way to do this. I was happy when I found how to get access to the Windows Network share on the server at work, but it mounts it on the desktop and it mounts the root address.

I'd like to do something like creating shortcuts to a specific folders inside that network share because there's only certain sections of the network share that concern me, I don't want to be constantly navigate through it to get to where I need to be.

---

### Post by bluefrog on 2008-04-30
same as you do your other shortcuts/bookmarks.

once you are in the folder you want, add a bookmark to nautilus (your file explorer).

---

### Post by njt on 2008-04-30
I am not quite sure how you are creating that mount but I assume Places->Connect to Server.

I don't really use that feature but there are loads of solutions, just using nautilis is probaly easiest (or Dolphin if you KDE), if you place smb://<ip address>/<shared folder name>/<sub folder name> would allow you to browse that folder.  If you don't have samba installed then the connect to might be needed but the same principal applies just tack on the exact path (remember that spaces need to be ecsaped and it
s case sensitive). 

In theory the Places->connect to option should be the same just add a '/' and start listing directories and it will mount to that point.  That said I just tried that and my "connect to" system is not working but I don't really use it so thats fine with me.

Hope some of this helps

---

### Post by jasonlevis on 2008-11-08
> **dover19 said:**
> I can't figure out a way to do this. I was happy when I found how to get access to the Windows Network share on the server at work, but it mounts it on the desktop and it mounts the root address.

I'd like to do something like creating shortcuts to a specific folders inside that network share because there's only certain sections of the network share that concern me, I don't want to be constantly navigate through it to get to where I need to be.

I found this thread trying to figure out the same problem and subsequently figured out a solution, so I thought I would come back and post it for other user's in the same situation (even though it's a half a year late).

I wanted a shortcut that I could click on to mount a connection to a web server I was doing work on. I didn't want to clutter up my Nautilus bookmarks.  

> 
[LIST]
[*]use "Connect to Server" to connect to the location and subfolder you want
[*]copy the text in the location field (ie. sftp://username@yourserver.com/home/user )
[*]Right-click on the desktop and select "Create Launcher"
[*]Change "Type:" dropdown to select "Location"
[*]Enter a name for the shortcut in the "Name:" field
[*]Paste the path you copied earlier into the "Location:" field
[*]Click OK
[*]Move the Launcher file anywhere you want it
[/LIST]

---

