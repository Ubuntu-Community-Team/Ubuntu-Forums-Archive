---
title: "IP messenger for ubuntu"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by 7raTEYdCql on 2008-04-23
Is there any IP messenger for ubuntu just like the one for Windows

---

### Post by spone on 2008-04-23
Do you mean to use instant messaging protocols like MSN, Yahoo or AIM? If that is the case you can use Gaim, which should be installed by default.

---

### Post by bluefrog on 2008-04-23
applications/internet/pidgin

---

### Post by philinux on 2008-04-23
> **spone said:**
> Do you mean to use instant messaging protocols like MSN, Yahoo or AIM? If that is the case you can use Gaim, which should be installed by default.

I'm afraid gaim, if you liked it, has been replaced by pidgin as the default. Kopete is also good as is amsn.

---

### Post by Boyohazard on 2008-04-23
> **i.mehrzad said:**
> Is there any IP messenger for ubuntu just like the one for Windows

Pidgin is the default install for Gnome

---

### Post by Confuzius on 2008-04-23
I think he's looking for something more like the netsend command in windows.
Not an instant messenger client.
Unfortunately I'm not sure what the Ubuntu/Linux equiv would be.

---

### Post by spone on 2008-04-23
> **philinux said:**
> I'm afraid gaim, if you liked it, has been replaced by pidgin as the default. Kopete is also good as is amsn.

My bad, I'm still thinking of it as Gaim despite it being renamed Pidgin :)

---

### Post by philinux on 2008-04-23
xipmsg

It's in synaptic.

---

### Post by 7raTEYdCql on 2008-04-23
I am looking for something that will allow me to transfer files from one computer to the other within the intranet.

---

### Post by 7raTEYdCql on 2008-04-23
I installed xipmsf from synaptic and what do i do after that. How am i supposed to make it run.
Can somebody please help, there are important files that need to be transferred.

Thanking you anyway.

---

### Post by Dr Small on 2008-04-23
> **i.mehrzad said:**
> I am looking for something that will allow me to transfer files from one computer to the other within the intranet.
SSH with SCP should do that.

---

### Post by PeterJS on 2008-04-23
> **Dr Small said:**
> SSH with SCP should do that.

I would suggest SSH with sshfs, or even the ssh/sftp handlers for nautilus. Either way, ssh is the way to go for fast easy linux to linux file transfers.

---

### Post by nhandler on 2008-04-23
One tool that you can use to chat between two computers is netcat. One computer acts as the server, and the other computer connects to the server. You can then chat between the two computers. NOTE: This is NOT secure, but it does get the job done quickly and easily.

Netcat can also be used to send file from one computer to another.

Here is one guide I found: [http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples/](http://www.g-loaded.eu/2006/11/06/netcat-a-couple-of-useful-examples/)
A google search will yield many more results.

Keep in mind, ssh would probably be the best option for transferring a file since it is secure. The only advantage of using netcat is that it is quick and easy to set it up. You also don't need to leave a server constantly running.

---

### Post by PeterJS on 2008-04-23
The need here appears to be file transfer, but getting back to the thread title, your best bet for IM over a local network would be Pidgin's implementation of Bonjour (aka Rendezvous, aka the iChat protocol).

---

### Post by quinnten83 on 2008-04-23
> **spone said:**
> Do you mean to use instant messaging protocols like MSN, Yahoo or AIM? If that is the case you can use Gaim, which should be installed by default.

it's pidgin now.
also amsnor emescene for live messenger clones.
if you mean an IP messenger as the messages you can send in windows using net send, then I don't know..

---

### Post by loell on 2008-04-23
yep,pidgin bonjour does file transfer too so it might be the best and the easiest solution.

---

