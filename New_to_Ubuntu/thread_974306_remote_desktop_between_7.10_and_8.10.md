---
title: "remote desktop between 7.10 and 8.10"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by jeromey on 2008-11-07
i have an older computer that is still running ubuntu 7.10.

i setup the remote desktop. (system-preferences-remote desktop)

now, how can i view this remote desktop from my laptop with 8.10?

---

### Post by jeromey on 2008-11-07
??
> 
The Following User Says Thank You to jeromey For This Useful Post:
chazn85 (52 Minutes Ago)
why do you thank me?

i have already tried simply using the remote desktop viewer (applications-internet-remote desktop viewer)  but it will not connect

it doesnt even see the the sever on my local domain, but it is

i tried installing tightvncviewer on 8.10 but that didnt work either

if i run xtightvncviewer from a terminal it will open a little box that says "sever", so i enter the severs ip and nothing happens 
(the box doesnt even close if i try, unless i force quit the app)

so now i removed xtightvncviewer and im stumped on how to connect

please help

---

### Post by tjwoosta on 2008-11-08
i think it should work with the standard remote desktop viewer that is pre-installed


have you opened your firewall and router ports?

---

### Post by mapes12 on 2008-11-09
An easier way to connect your 2 machines is to use openssh. See the post from SpaceTeddy here: [http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308)

You may need to have both machines using the same version of Ubuntu otherwise the connection may be slow.

---

