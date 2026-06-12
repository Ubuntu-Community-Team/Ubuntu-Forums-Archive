---
title: "opening ports for p2p"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by gorgon on 2008-08-30
hi,

i've been reading about a bit on opening up ports to use torrent clients bu tthey mostly talk about port forwarding. im connected to the net without having access to the router and i can download torrents just fine but uploading is at 1kb/s. how can i make sure that nothing is keeping me from proper p2p action within ubuntu?

if it makes any difference im using azureus.

---

### Post by nicedude on 2008-08-30
You still need to open a port in your linux firewall whether you have a router or not if you want the best performance. Like try the tools -> firewall nat test and see if it doesn't fail.

If it does then install firestarteer or guarddog as a GUI frontend to IP table so you can configure you IP tables linux firewall in a GUI

I like guarddog best by the way, just make a custom rule and pick some high port like 34000 and enable it then set the same port in azureus and you will be set. To make sure just do the firewall test in azureus and it should say OK now.

Hope that helps.

---

### Post by gorgon on 2008-08-31
hi nicedude,

installing firestarter actually crashed my machine and im now left with commandline after doing a manual fsck and gnome only appearing as a frozen light brown fullscreen with a grey square in the upper right corner. Exiting trying to start x only gives me a grey fullscreen with a black X for mouse.

Any ideas?

---

### Post by gorgon on 2008-08-31
ok, sorry about the fuss. got to log into gnome again at the next try. strange.

---

