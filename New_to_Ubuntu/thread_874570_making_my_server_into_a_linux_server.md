---
title: "making my server into a linux server"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by mancrow on 2008-07-30
i am looking into making my server run on linux!!! 

its my 2 tb file server and its shared so that it can stream media and also access files. system specs :
celearon 2.8 ghz  (i kno weak processor but the computer was free!!!)
512 mb ram
4 x 500 gig sata 2 drive
dell dimension E520 


so i was wondering if its a good idea? i was going to use the latest release of ubuntu cause i like to remote connect to it to download files using torrents and is it possible to download newsgroups with ubuntu. and i want to be able to access my files like windows so i go \\server2 and then i get the list of all the folders i can access. 

just wondering if that is at all possible i am sure it is that is why i asked here cause there is a lot of smart people that love to lend a helping hand

---

### Post by ladr0n on 2008-07-30
If you like linux on desktops, you'll love it on servers.  
Just so you know, though: the basic ubuntu server install does not include a GUI, so if you want to be able to work on your server graphically, you'll need to install one yourself.  
Once you get the server set up, though, you'll never need to sit in front of it at all.  You can do any administration you need through SSH from your other computer(s).  Conceptually setting up filesharing on linux isn't much different than on windows, and you can find plenty of informative tutorials online.

---

### Post by hyper_ch on 2008-07-30
it should be fairly simple.

(1) install the server (it has no gui)

(2) install ssh server (and also some auto-blocker)
```

sudo apt-get install openssh-server denyhosts

```

(3) give your server a static ip (by editing /etc/network/interfaces) and give it a nameserver entry (by adding your router's IP to /etc/resolv.conf --> nameserver WW.XX.YY.ZZ)

(4) if the static IP works fine, power off the server, put it in a place where you want it to be, power it up again ;)

(5) connect from your computer to the server (on windows get Putty to access the server through SSH)
```

ssh SERVER_IP

```

(6) install now the stuff you want. For torrents I can recommend "rtorrent" (maybe even compile it from svn as there are some nice added features meanwhile). Install samba server so that you can just browse it from windows machines.

(7) for music streaming you may want to have a look at gnump3d

....

---

### Post by Archmage on 2008-07-30
> **mancrow said:**
> celearon 2.8 ghz  (i kno weak processor but the computer was free!!!)

If you want to make this only a file server, than the CPU is more than fast enough.

---

### Post by mancrow on 2008-07-31
another question is that i have file NTFS format and now how can i share them with out formatting the drives there is a lot data on there that cannot be lost.

---

