---
title: "Remote Desktop - connection closed"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by ZootHornRollo on 2008-07-11
Hi,

i have Hardy on my main pc and am trying to remote desktop my other pc running gutsy.

I am using Remote Desktop Viewer and keep getting an message saying ```
Connection to host "graham@MusicBox" was closed.
```

i have had this running ok just yesterday but today i get that message.

I have not changed any settings on either computer but have updated the machine running Hardy.

Any ideas?

---

### Post by Dr Small on 2008-07-11
You didn't happen to install Firestarter on "MusicBox" did you?

---

### Post by ZootHornRollo on 2008-07-11
i have no idea what firestarter is.  so not knowingly!  :)

what would that have done?

---

### Post by ZootHornRollo on 2008-07-11
ahhh... its a firewall

no

---

### Post by ZootHornRollo on 2008-07-11
fixed.

dunno how.  it just works.

reinstalled vino and vinagr on hardy and vino on gutsy

restarted both machines... still the same...  could ping the other pc but connection closed

restarted into XP.  worked fine with vncviewer.

restarted into Ubuntu, tried it...  works!

go figure!!

---

### Post by ZootHornRollo on 2008-07-12
OK.    doesn't work again :(

I booted into Hardy this morning and once again the remote desktop viewer was spitting out the Connection to host "graham@MusicBox" was closed.

I booted into XP, ran VNC viewer, worked fine.  booted back into Ubuntu, works fine using remote desktop viewer.

Is there a setting that RealVNC triggers to get it working?

---

### Post by superprash2003 on 2008-07-12
which command are you using to connect?? 
For Reference: [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine_30.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine_30.html)

---

### Post by ZootHornRollo on 2008-07-12
> **superprash2003 said:**
> which command are you using to connect?? 
For Reference: [http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine_30.html](http://prash-babu.blogspot.com/2008/05/how-to-remote-control-ubuntu-machine_30.html)

i don't use a command as such.

If i use the 'find' within the remote desktop viewer it finds the server by name and tries to connect without asking for the password.  i  then get the connection closed message.

If i connect using the servers ip i get the password prompt then i get the connection closed message.

This is really annoying as it worked no prblem before and works flawlessly when i use realvnc on XP so it must be something to do with my machine running hardy

---

### Post by f37u5g0d on 2008-07-12
There is a very high possibility that hardy has upgraded packages for vino and whatever else for vnc.  I suggest having both machines using the same version of ubuntu whether that's gutsy or hardy.

---

### Post by ZootHornRollo on 2008-07-12
if i type in terminal ```
vncviewer i.p.i.p:5900
``` it says connection refused?  do i need to include the password somewhere?

---

### Post by ZootHornRollo on 2008-07-12
they are both running different versions of vino.  can't see a way n synaptic to upgrade gutsy or downgrade hardy.

might have to do as suggested and run gutsy on both machines as hardy is not an option on the server as the sound card is not supported (m-audio audiophile 2496)

---

### Post by superprash2003 on 2008-07-12
since 5900 is the default port you can do vncviewer x.x.x.x:0

---

### Post by ZootHornRollo on 2008-07-12
> **superprash2003 said:**
> since 5900 is the default port you can do vncviewer x.x.x.x:0

that worked!!

why does that work and not remote desktop viewer?
 and why not x.x.x.x:5900 for that matter???

                       :confused:

---

### Post by superprash2003 on 2008-07-12
i just now tried using x.x.x.x:5900 and it worked :D.. strange!!!

---

### Post by ZootHornRollo on 2008-07-12
and now remote desktop viewer is working!

i'm very confused!!!

---

### Post by ZootHornRollo on 2008-07-12
double post...sorry

---

### Post by bo_n_tulsa on 2008-10-19
I had this same weirdness happen to me.
I have no idea why the following works for me, but when I receive the "closed" message, I open up a terminal and ping the machines IP address that I'm trying to connect to. 
Every time I've done this, the remote desktop software immediately connects.

---

### Post by cabomix on 2008-12-29
Sorry wrong forum!

---

