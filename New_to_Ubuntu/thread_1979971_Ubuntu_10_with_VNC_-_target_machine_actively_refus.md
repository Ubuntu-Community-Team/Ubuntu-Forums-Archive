---
title: "Ubuntu 10 with VNC - target machine actively refused it"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by rohit09 on 2012-05-14
I'm using Ubuntu 10 I correctly installed VNC and over 7 months I'm running that without any issue. But suddenly yesterday when I'm trying to connect my VNC I got > "no connection could be made because the target machine actively refused it" ](*,)

This massage over and over again. I'm using tightVNC Viewer. Could you help me please. :-k

MY PC -
Windows 7 x64
All Firewall: Down 

I can access my server by SSh (Putty) :?

Help me Plz!

---

### Post by steeldriver on 2012-05-14
what vnc server did you install? how are you invoking it?

are you sure you are trying to connect to the correct screen / port?

---

### Post by rohit09 on 2012-05-14
I'm using tightVNC
I'm using tightVNC viewer
yes.


> **steeldriver said:**
> what vnc server did you install? how are you invoking it?

are you sure you are trying to connect to the correct screen / port?

---

### Post by steeldriver on 2012-05-14
so how are you authenticating? if it is via ~/.vnc/passwd have you tried regenerating the password?

---

### Post by rohit09 on 2012-05-14
That password thing is not coming even, just click connect and the daam text is poped up! I don't know what to do :(

P.S. SSH password I'm using and it's fine.. 

> **steeldriver said:**
> so how are you authenticating? if it is via ~/.vnc/passwd have you tried regenerating the password?

---

### Post by pbvijay on 2012-05-15
Hi Rohit,
   Try to connect using the port number 
for example
 VNC server running on port 5901
the type following while connect using VNC Viewer 
10.101.01.10::5901 or mypc::5901

You can find out the port information from the vnc log file. The log file will be located at 
/root/.vnc/mypc:1.log

15/05/12 17:08:22 Xvnc version TightVNC-1.3.9
15/05/12 17:08:22 Copyright (C) 2000-2007 TightVNC Group
15/05/12 17:08:22 Copyright (C) 1999 AT&T Laboratories Cambridge
15/05/12 17:08:22 All Rights Reserved.
15/05/12 17:08:22 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
15/05/12 17:08:22 Desktop name 'X' (mypc:1)
15/05/12 17:08:22 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
15/05/12 17:08:22 Listening for VNC connections on TCP port 5901

---

