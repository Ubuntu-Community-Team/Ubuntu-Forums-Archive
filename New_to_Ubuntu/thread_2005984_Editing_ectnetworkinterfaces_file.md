---
title: "Editing ect/network/interfaces file"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by SpitCat on 2012-06-18
Hi everybody, 
Can anyone tell me how to edit my ect/network/interfaces file. - when I try to save it it tells me It's read only. How do I get permission to save it, do I have to run it as a root user & if so how ?(do I have to run it from Terminal ?).

---

### Post by papibe on 2012-06-18
Hi SpitCat. Welcome to the forums!

First of all, depending on your Ubuntu version, some changes made on /etc/network/interfaces will be ignored.

For example if you are running Ubuntu Desktop, all network interfaces are manage by a package called network-manager. The way to configure your network with this is by using the GUI tools (including 'Network Connections').

If you have uninstalled network-manager, or your are running the Server Edition, you need to edit the file as superuser (admin).

Using a GUI: either open a terminal or press Alt+F2 and then run:
```
gksudo gedit /etc/network/interfaces
```

On a server (no GUI) run this:
```
sudo nano /etc/network/interfaces
```

I hope that helps, and tell us how it goes.
Regards.

---

### Post by anewguy on 2012-06-18
> **papibe said:**
> Hi SpitCat. Welcome to the forums!

First of all, depending on your Ubuntu version, some changes made on /etc/network/interfaces will be ignored.

For example if you are running Ubuntu Desktop, all network interfaces are manage by a package called network-manager. The way to configure your network with this is by using the GUI tools (including 'Network Connections').

If you have uninstalled network-manager, or your are running the Server Edition, you need to edit the file as superuser (admin).

Using a GUI: either open a terminal or press Alt+F2 and then run:There may be many backups in there, we just want each client-folder be deleted 3 days after we created that folder and copied client's stuff in it.
```
gksudo gedit /etc/network/interfaces
```There may be many backups in there, we just want each client-folder be deleted 3 days after we created that folder and copied client's stuff in it.

On a server (no GUI) run this:
```
sudo nano /etc/network/interfaces
```

I hope that helps, and tell us how it goes.
Regards.

Just a small reason why you need to do the above:  by default, there are many system folders where everything is owned by root.  So, your login account can only read those, not update those.  sudo is used to grant temporary priviledges so you can access those files.  The gksudo should be used when using any type of graphical interface to those files - such as the above mentioned gedit.  Yes, these would be run from a terminal window/command line.

Dave ;)

---

### Post by SpitCat on 2012-06-19
I'm trying to add a Static IP address to eth0 to connect to a router. The Router is not an access router to the internet but acts as a gateway to another network (studying for CCNA}.I managed to configure a static IP address in network tools & connect to the router, but was under the impression that changing the ect/network/interfaces file was more permanent.

---

### Post by SpitCat on 2012-06-19
Cheers for the help

---

### Post by SpitCat on 2012-06-19
Cheers Dave

---

