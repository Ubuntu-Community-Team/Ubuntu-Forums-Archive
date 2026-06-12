---
title: "how to set up a network?"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-05-25
Installed Ubuntu 8.04 on an old desktop (new July 2004).  Was running XP, now dual boot.  I can get on the internet just fine, but I can't see the other PC's on the network.

Have an Intel 10/100 built in LAN on my motherboard, cable to a wireless router.  Other PC's have wireless built in.

When I'm running XP everything works fine.

I must have omitted a big chunk of the installation procedure.

Is there an easy way in Ubuntu to set up the network capabilities so that I can see the other PC's, and they can see the Linux machine?  It seems odd that I can easily connect to the internet, but am not visible on the network.  If I click on "Places", then "computer", then "network servers" an icon appears with the title "Windows Network" but nothing else.

Thanks in advance

---

### Post by sayakb on 2008-05-25
```
sudo apt-get install samba
```
And try again

---

### Post by Jerry N on 2008-05-25
Ubuntu 8.04 and LinuxMint 5 are missing the capability to see Windows machines on a network automatically.  You need to open "Computer" and type "smb://*name*" (don't type the quotes) where *name*is the name of the Windows computer you want Ubuntu to see.  You don't need to install Samba for this but you will need Samba if you want to share files on your Ubuntu machine with your Windows machines.  

Jerry

---

### Post by raymondvillain on 2008-05-26
If I go to "system" > "administration" > "synaptics" and select the samba package, the machine goes through some gyrations and installs Samba (I think).  What else does one need to do to get it running?

I am green as gourd guts on this matter, thanks for the help.

---

