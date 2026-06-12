---
title: "Accessing a file server"
date: 2012-01-19
forum: New to Ubuntu
---

### Post by waxcan on 2012-01-19
Hi all.
Just installed the latest Ubuntu. I've got a file server [set up exactly like this]("http://myhelp.westnet.com.au/pages/releaseview.action?pageId=17563886"):

On Win7 I accessed it via Run, explorer, or in a browser using \\10.1.1.1\anonymous.

I tried using Terminal,  but didn't work it out.

I'm trying to stream music from it to Banshee.

Appreciate any help.

-EDIT
I also used the interface for connecting to a server. I entered 10.1.1.1 under server and folder \anonymous port left default at 21.

It came up with a no reply error.

The harddrive and network are fine, still accessible through  Windows.

I'm reading Cortman's awesome terminal guide now.

Cheers

---

### Post by papibe on 2012-01-19
Hi waxcan. Welcome to the forums!

I would try to access the share first using Nautilus (file manager) by looking for it on Go -> Network.

Once you see your files on Nautilus, it may be possible to import the folder from Banshee.

Another option would be to open Banshee and go to Media -> Open Location and then use this format:
```
smb://10.1.1.1/anonymous
```
Hope it helps.
Regards.

---

### Post by M!K3_$ on 2012-01-19
If you want to access it from terminal you can use the following commands:

To view smb shares on the network
```
smbtree
```

To connect to a share
```
smbclient //servername/sharename
```



If you want to connect in the file browser, like papibe said,  simply use ctrl-l to get the address bar and type in
```
smb://servername/share
```

---

### Post by partloer on 2012-01-20
This forum post has a lot of information that might help you out.  [http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

It kinda all depends on what you want to do.  Permanent mount when you start your computer or manually mount after you are logged in or maybe other options.

---

### Post by waxcan on 2012-01-22
Thanks guys! Worked like a charm.

---

