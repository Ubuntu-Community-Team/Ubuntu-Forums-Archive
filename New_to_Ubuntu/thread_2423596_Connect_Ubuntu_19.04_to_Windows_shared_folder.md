---
title: "Connect Ubuntu 19.04 to Windows shared folder"
date: 2019-07-26
forum: New to Ubuntu
---

### Post by gates25 on 2019-07-26
I recently installed Ubuntu 19.04 and I cannot seem to connect to windows. Is there a tutorail for Ubuntu 19.04 connecting to Windows 10?

Thanks in advance.

---

### Post by Morbius1 on 2019-07-26
I don't know what "cannot seem to connect" means. Are you getting an error message when you try to connect? Need more information.

[There is a bug in how Ubuntu tried to fix smb host discovery]("https://bugs.launchpad.net/gvfs/+bug/1828107") that makes it pretty much impossible to discover then connect to a fully updated Win10 box so you will have to connect to the Win10 box using **Connect to Server** in Nautilus. THen you can specify the host in 3 different ways.

Let's say your WIn10 box is called vwin1064 and the share name is shared. You can call it:

By its mDNS name: [B]smb://vwin1064.local/shared
[ATTACH=CONFIG]283681[/ATTACH]

[/B]By ip address:[B] smb://192.168.0.100/shared

[/B]And as a last resort by it's netbios name:[B] smb://vwin1064/shared
[/B]

---

### Post by gates25 on 2019-07-27
I can see my computer in the network section of file explorer. But when i click on it to connect I get "Unable to access location. Failed to retrieve share list from server: connection refused". I'm not sure what I am doing wrong. Thank you for the response.

Thanks in advance.

---

### Post by Morbius1 on 2019-07-27
The connection is being refused because you are connecting to the Windows machine with  dialect of smb that Windows turned off. All of that is explained in the bug report I listed in my original response as well as the workaround.

---

### Post by srslol2 on 2019-07-29
Hello!  Did you try using an SMB path?  For example, if the server IP is 10.0.0.100 and the shared folder is named "coolstuff", then I would open the file explorer and click "Other Locations" at the bottom left of the screen (scroll down left column) and find "Connect to Server."  Then type this:

smb://10.0.0.100/coolstuff

A new path will open up to that folder.  As long as read rights are set at minimum, you'll see it.

---

### Post by gates25 on 2019-07-31
I tried that. I got "Unable to access location. Failed to mount windows share: connection timed out".

Not sure what I am doing wrong.

Thanks for the response.

---

