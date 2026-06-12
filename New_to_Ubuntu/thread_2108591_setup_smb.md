---
title: "setup smb"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by twopeak on 2013-01-25
Hello
I have a xbmc-buntu; that I use as my primary media center.
In the past I have succeeded in sharing files with my Win7 machine.

After a re-install I can't figure out what I'm doing wrong.
Eventually I've managed to get one of both shares working, though not as I'd like:
* one share should point to the user file and be read only without password
* one share should point to the whole system and be read/write with a password.

Furthermore; it seems it's now impossible to go to the shares using \\hostname. I must use the IP adress. 

Any help on how to get this right? I've tried a lot of different configurations (first manually and then using SWAT) but none really worked.
I've read what I could but I don't intend to be an expert on the field (I'm trying to just get it to work).

smb.conf > [http://pastebin.com/Y2jKweDF](http://pastebin.com/Y2jKweDF)

---

### Post by furything on 2013-01-25
I use mythbuntu and find it is something to do with windows.

I had to clean up my windows 7 network stuff and the connection to both my myth boxes disappeared from network media devices (av extenders).

I removed all information from my windows box in the registry by hand (for both myth boxes).

It has found one of them so I can play recorded tv from that box in windows media player but the main backend still just shows up as a network computer. It took several days for the first box to show up so I am hoping the second one will shortly be correctly shown. 

There is no configuration difference between my 2 myth boxes so it has to be the windows box that is the issue. This maybe the same for you.

---

### Post by twopeak on 2013-01-25
the first part is just me being clueless.

the second part must be my config:
it worked in the past, but i reinstalled xbmcbuntu; android, ios, windows all can connect on hostname to eachother; except the xbmc-box. and I've been mucking with it quite much (generally, the more I touch it, the harder it gets to fix).

---

### Post by twopeak on 2013-01-28
If someone still reads my thread, is it badly asked, or is the question difficult to answer?

---

