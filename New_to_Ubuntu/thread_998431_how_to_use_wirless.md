---
title: "how to use wirless??"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by nevercroft on 2008-11-30
I have installed ndiswrapper and it recognizes my wifi adapter. In the thing at the top right of the screen it has a tick for "enable wireless". But when I click the connection manager and click the wireless tab it doesn't find any networks. Are they supposed to show up there? 
Help!

---

### Post by jgoguen on 2008-11-30
The wireless tab in the Connection Editor only displays networks you've configured or already connected to.  If you wait a while (should only be a minute) all wireless networks in range will appear when you left-click the NetworkManager icon.  To force NetworkManager to rescan for networks, right-click NetworkManager icon, uncheck "Enable Networking", then right-click again and check it again.  Wait a minute or two and your networks should appear.  If there's nothing there after a couple minutes, please post the output of this command to make sure your network is being seen:
```
sudo iwlist wlan0 scan | grep "your network name"
```
Replace "your network name" with the name of your wireless network, but leave the quotes in place.

---

