---
title: "Remmina RDP Broken?"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by d4m1r on 2012-08-14
Hey guys, I need to use Remote Desktop to be able to connect to my Windows XP machine at work and I am really disappointed with the state of RDP clients in Ubuntu.....In 11.10, at least the basic stuff was working, but with 12.04 and ANY RDP client available in the software centre, very very basic functionality is broken....

Most recently, I have been using Remmina because it is the least broken but even now recent updates to **libfreerdp** packages has further broken functionality...What are some of the things no longer even possible to do Ubuntu -> RDP -> Windows XP? Find the list below:

1) copy/paste within the remote machine
2) screenshot remote machine
3) right click on remote machine
4) keyboard shortcuts for remote machine

Does anyone know how to fix these things or know of a linux RDP client that isn't as broken as Remmina/Remote Desktop Viewer/KVpnc/etc? I tried forcing back the old versions of the **libfreerdp **packages using Synaptic but no use :confused:

---

### Post by d4m1r on 2012-08-15
60 view and nobody else using Remmina RDP? :confused:

What RDP clients are you guys using and how well do they work connecting to Windows XP machines?

---

### Post by QIII on 2012-08-15
60 views means 60 people looked and didn't have an answer for you.  That's all.

I'll take a look at this when I get home.

---

### Post by JKyleOKC on 2012-08-15
I'm using rdesktop, but only to connect to an XP VM across my LAN. It has no problem with any of the points you mention, but that may be due to its server in the VM rather than to the client.

Have you looked at xfreerdp? It appears to support the clipboard though I haven't tried it.

---

### Post by d4m1r on 2012-08-15
> **JKyleOKC said:**
> I'm using rdesktop, but only to connect to an XP VM across my LAN. It has no problem with any of the points you mention, but that may be due to its server in the VM rather than to the client.

Have you looked at xfreerdp? It appears to support the clipboard though I haven't tried it.


Are rdesktop and xfreerdp 2 different clients? Are they both available in the software centre? I believe rdesktop is also known as remote desktop viewer and I have tried that one recently and it has the same issue...

---

### Post by d4m1r on 2012-08-16
> **QIII said:**
> 60 views means 60 people looked and didn't have an answer for you.  That's all.

I'll take a look at this when I get home.

Hey, any update? ;)

---

### Post by QIII on 2012-08-16
1 and 3 work for me.  2 and 4 may be key binding on the client taking precedence.  

I'll see how thqt works Windows to Windows today.

---

### Post by d4m1r on 2012-08-16
> **QIII said:**
> 1 and 3 work for me.  2 and 4 may be key binding on the client taking precedence.  

I'll see how thqt works Windows to Windows today.

What client (and version) are you using and what Windows OS are you connecting to?

I was using Remmina over Cisco VPNC to a Windows XP machine and none of those 4 were working....

---

### Post by QIII on 2012-08-16
Xubuntu 12.04 to Win XP Pro via home router.

Edit:  supposedly Reminna has a keyboard grabbing feature that will allow you to send special key combos to the host.  There is supposed to be a keyboard button on the floating toolbar.  Not at home so I can't test.

---

### Post by d4m1r on 2012-08-16
> **QIII said:**
> Xubuntu 12.04 to Win XP Pro via home router.

Edit:  supposedly Reminna has a keyboard grabbing feature that will allow you to send special key combos to the host.  There is supposed to be a keyboard button on the floating toolbar.  Not at home so I can't test.


I am aware of that feature and have tried it but it does nothing....What client do you use btw? Also, had a chance to see if any of my issues work Windows -> Windows?

Thanks in advance!

---

