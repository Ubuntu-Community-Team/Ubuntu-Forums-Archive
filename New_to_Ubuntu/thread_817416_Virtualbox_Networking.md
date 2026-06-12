---
title: "Virtualbox Networking"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by seuzy13 on 2008-06-03
I have virtualbox with an ubuntu 8.04 host, and am wondering how to connect to the internet with my openSUSE 10.3 guest.

I have tried reading the help manual that comes with virtualbox, but it is kind of cryptic, so I thought I would ask here. I can use either a wired or wireless connection. It doesn't really matter which, but I assume wired is easier? 

Really all I need to do is share files between my guest and host, but it appears you have to install virtualbox on the guest as well which would require a download.

Thanks!

---

### Post by useResa on 2008-06-03
Let me see if I understand correctly. You have Ubuntu 8.04 as host with VBox installed and inside VBox you have installed openSUSE 10.3 as guest.

Now you like to share data between the guest and the host. You can do this by simply sharing the folder in which the files are located by means of Samba. Click on the folder you like to share and choose Sharing options. Looking for network places in the guest should give you access to these files now.

If you like to connect to the internet from openSUSE 10.3. Normally this works out of the box.
What is required is that your host does have internet access. Between the guest and the host is always a "wired" connection (although virtual ;) ).

---

### Post by cosine352 on 2008-06-03
open virtual box. 

settings ----> network

make sure to Enable network adapter and cable connection

---

### Post by seuzy13 on 2008-06-03
I have already gone into the guest's network settings and activated them (I'm not sure of all the drop-down boxes, however). I then plugged it into my router, which has worked before on my host, and I could not connect in firefox. I thought maybe I was overlooking something important.

Here are my network settings-
--Adapter 0 tab--
Enable Network Adapter (checked)
Adapter type-- (the second out of three is selected)
Attached to-- NAT
Network name-- (grayed out)
MAC adress--(random)
Cable connected (checked)
--Host interface settings--(grayed out)



For file sharing, as I understand it, you must have virtualbox installed on the guest as well. Is this true? In any case I had already set up the file sharing to share my host's Desktop folder as read-only. I couldn't find it anywhere in my guest either.

---

### Post by v8YKxgHe on 2008-06-04
I'm also having this exact same problem, I have my host PC (running Ubuntu 8.04/Hardy) that is on a LAN and connects to the Internet through the main router (all wired, not Wireless).

The settings that seuzy13 have is the same as mine, and I just can't access the ground outside world within my guest OS (in my case, KDE4Daily - so I can't update it).

Regards,

---

### Post by purplepaint on 2008-06-13
I'm  having the same problem.

I'm running OpenSUSE as a guest in VBox and I can't get it to connect to the internet.  I'm using a wireless laptop, and the internet works perfectly when I run the LiveCD version of Damn Small Linux and, as far as I can tell, both guests are set up with the same network settings in VBox.

---

### Post by hyper_ch on 2008-06-13
that's one of the reasons I prefer vmware... networking is a lot simpler there...

---

### Post by purplepaint on 2008-06-13
After getting hold of the latest version of VirtualBox, I messed about with my virtual network settings a bit and OpenSUSE seems to connect now, but very slow and unreliable (so far only successfully displaying the default home page and Wikipedia - slowly - in Firefox and failing to update the OS or connect through the default instant messenger application).

---

### Post by Jose Catre-Vandis on 2008-06-13
Have a read through this, most of which should also apply to an openSuse guest
[http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/](http://bimma.me.uk/2007/09/30/ubuntu-creating-host-interface-networking-for-virtualbox/)

---

### Post by RAWdeal101 on 2008-06-13
> **seuzy13 said:**
> I have virtualbox with an ubuntu 8.04 host, and am wondering how to connect to the internet with my openSUSE 10.3 guest.

I have tried reading the help manual that comes with virtualbox, but it is kind of cryptic, so I thought I would ask here. I can use either a wired or wireless connection. It doesn't really matter which, but I assume wired is easier? 

Really all I need to do is share files between my guest and host, but it appears you have to install virtualbox on the guest as well which would require a download.

Thanks!

Seuzy,

I believe inside virtual box when you right click on the guest machine that you made you can setup nat so the guest can use your internet connection through your host. Like said above it should automatically detect it, but if it doesn't you may need to changed the "attached to" settings in this window as well. Some machines require to see the host's Mac address so if the other settings don't work all I can think of is to enable PAE/NX under the advanced tab when right clicking on a guest and going to general.

As far as the sharing of folders you can go the Samba route or in virtual bo 1.6 you can share folder's between virtual guests by again right clicking on a guest and then going to shared folders and creating a share there. You might have to restart the guest machine in order for it to see it either in network neighborhood ( for windows os) or network folders in other os's.

Hope this helps and clears things up! 

It took me a while of playing with virtual box to get some of the things working but I like the features they are coming up with these days ( I have worked with vmware and virtual pc ).

---

