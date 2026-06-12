---
title: "Samba streaming on OS X... but Not Ubuntu"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by spit334 on 2008-06-26
I have a headless Ubuntu 8.04 Server Machine using samba. 

When connecting to the server from my 10.5 Mac, I can stream my .avi files perfectly with VLC.

However, when I connect to the server from my Ubuntu 8.04 laptop (regular distro), VLC gives me this error:
Unable to open 'smb://SERVER/movies/Indiana%20Jones/Indiana%20Jones%20-%20The%20Last%20Crusade.avi'

I know that there has been some trouble with samba streaming... but it seems to be on the user side, not the server side.

I would post the smb.conf file, but it doesn't seem necessary because it is working fine on my Mac. My goal was to be able to stream movies to all of the Macs in the house (4)... but I found it odd that my Ubuntu laptop wouldn't work.

Also, if it makes any difference (which I doubt)... the smb share is located on a mounted external HD.

---

### Post by billgoldberg on 2008-06-26
I have the same problem with samba.

I just use Openssh now, haven't had a problem since.

---

### Post by spit334 on 2008-06-26
Im not sure how openSSH would solve that problem... that also could be because I am relatively new to Ubuntu.

I am running openSSH right now, which allows me to run terminal commands on the server on my laptop.

However, I am still not convinced that VLC streaming won't work over samba.

---

