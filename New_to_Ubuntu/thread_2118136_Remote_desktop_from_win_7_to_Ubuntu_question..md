---
title: "Remote desktop from win 7 to Ubuntu question."
date: 2013-02-20
forum: New to Ubuntu
---

### Post by Tecco on 2013-02-20
Hello All you linux wizards out there. :)
I Yesterday installed my first linux system on an old labtop i had in a closet for a while. the idea is for it to act as a small download station ,my buddies can access, manage files, start downloads and what have you.
I with the help from the internetz, got the remote desktop to work fairly easy, but we have a slightly odd problem i dont remember from normal win to win remote desktopping. 
We basically share same user and pass, but, when my buddy logs on while i am logged on it does not Log me off, he aparantly gets his own desktop, with none of the things opened ive opened. :(   Now this geives some odd stuff with different programs that Ubuntu seems to register from both "desktops" but only show on one. Eg. I could not open firefox, since it said it was already open. My buddy then closed firefox on his instance and i could suddently open fire fox. 
How do i make this "go away" and get remote desktop to work as a "singleton" so it logs me off when he logs on or something similar, that will get us access to the same desktop whenever we log in on the same useraccount.
Thanks in advance :)
Kim M Jensen

---

### Post by NigO on 2013-02-20
> **Tecco said:**
> Hello All you linux wizards out there. :)
I Yesterday installed my first linux system on an old labtop i had in a closet for a while. the idea is for it to act as a small download station ,my buddies can access, manage files, start downloads and what have you.
I with the help from the internetz, got the remote desktop to work fairly easy, but we have a slightly odd problem i dont remember from normal win to win remote desktopping. 
We basically share same user and pass, but, when my buddy logs on while i am logged on it does not Log me off, he aparantly gets his own desktop, with none of the things opened ive opened. 

What are you doing to run remote desktop, is it RDP/VNC?  Or to put it more simply, what do you run to access the remote desktop?

You might be easiest to just use VNC if you want everyone to access the same desktop, which can be the desktop you see on the monitor or a separate one.  The latter option is probably better, so you can use the laptop screen if you need to go in and do maintenance things.  Unlike Windows, you're not limited on how many remote sessions you can run, so alternatively you could give each of your users their own desktop login and they could all connect at the same time

---

### Post by Tecco on 2013-02-20
Thank you for the answer. :)
I was following a tutorial that told me to install something called xrdp. 
This made it possible to log on with the remote desktop client in windows. 
We dont really have any use for different desktops, or different users. We need to be able to log on and see what the other person has been doing, reading messages written in open windows and such. 
We dont need to be able to be logged on on the same time either, just acces to the same desktop when we are actually logged in. 

Since i am completeley new to Linux i am not sure what VNC is :) 
I assume it is some sort of other remote desktop software? 
Will that maybe be able to solve my problem with less hassle than i currently have? 
Thanks again :)
KMJ

---

### Post by steeldriver on 2013-02-20
Probably the easiest way would be to forget about xrdp, and use the default 'Desktop Sharing' option from Ubuntu

Since that uses the VNC protocol (rather then the RDP protocol that Windows understands natively) you would then need to install a Windows VNC client on each Windows box - the TightVNC viewer is a pretty good free one, IMHO

There supposedly *are* ways to share a single xrdp session - but it's more work, I think

---

### Post by Tecco on 2013-02-20
Cool, ill try to install tightvnc and see how that works out :) 
Thanks :)

---

### Post by Tecco on 2013-02-20
So Tried setting up TightVNC.
Seems TightVNC Server only allow 8digit passwords, so that is no good for over the net remote desktop :( 
So i am back at start again :|

---

### Post by steeldriver on 2013-02-20
If you want to do this over a public network, you can still use VNC but you should tunnel the traffic via ssh

---

### Post by Tecco on 2013-02-20
Wait, i get it! I realise now there is build in desktop sharing in ubuntu :KS
i started that and could connect with the tightVNC viewer! 
Dynamite! :D
Now i just need to put in portforwarding and such in router and im good to go. 
Ty for the help people! 
:D

---

### Post by steeldriver on 2013-02-21
Just be aware that the default 'Desktop Sharing' application (vino-server) is no more secure than any other VNC connection and should still be tunneled over SSH if you are connecting via a public network

**The length of the password is not he issue here - the traffic itself is not secure**

For vino-server, a method that seems to work is:

0. install openssh-server on the target machine (you will be using an SSH connection to securely tunnel the VNC traffic)

1. install the dconf editor app (package name is dconf-tools iirc - or find it in the software center)

2. run dconf editor and navigate to desktop --> gnome --> remote-access

3. change the value of **network-interface** to **lo** (default is empty - allows connections via any interface) and close

4. return to the 'Desktop Sharing' item in the dash settings and disable and re-enable 'Allow other users to view your desktop' (this restarts the vino-server and applies the changes)

After that you will need to use putty on your Win boxes to connect via SSH and set up a tunnel - the tunnel options are in the putty Connection --> SSH --> Tunnels menu, if you are using default ports you can just add 

Source port = 5900
Destination = localhost:5900

You will then need to tell your VNC client to connect to localhost:5900 instead of your remote desktop machine. You can close any VNC ports that you opened / forwarded.

Hope this helps

---

