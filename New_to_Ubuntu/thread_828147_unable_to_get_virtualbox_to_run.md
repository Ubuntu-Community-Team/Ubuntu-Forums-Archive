---
title: "unable to get virtualbox to run"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by hazman on 2008-06-13
unable to get virtual box to run keep getting error 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 unable to get my head round it

---

### Post by forestpixie on 2008-06-13
I gave you that in the other thread you need to add yourself to the vbox users group, there is a command line way to do it as well but I can't remember it

> Open Users and groups in the Admin menu, unlock it, then manage groups - find vbox users, then properties and make sure you enable your user.

---

### Post by sam_delta on 2008-06-13
go into system>admin>users and groups then click on "unlock" in the bottom of the window, then click on "manage groups" on the right side. then go to the very bottom of the list and select the group "vboxusers" and click "properties" , in the pup-up that opens, select the check-box on your user, to make yourself part of that group. click ok, ok, ok, and log-out and in

sam

---

### Post by Oldsoldier2003 on 2008-06-13
> **hazman said:**
> unable to get virtual box to run keep getting error 
The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

 unable to get my head round it

```
sudo usermod -aG vboxusers <your_user_name>
``` or use sytem>Administration>Users and Groups

---

### Post by linux6994 on 2008-06-13
Go to System > Administration > Groups and Users, then unlock to achieve access. Next  go to Manage Groups, go to vboxusers and select yourself as user. Close and logout and back in again and give vbox a try.

---

### Post by bumanie on 2008-06-13
By cli, I think it is > sudo adduser <your username> vboxusers

---

### Post by hazman on 2008-06-13
thanks your a star

---

### Post by jerome1232 on 2008-06-15
Wow, I'm a retard... It's official. After a Kernel update virtual box stopped working for me giving me that error code, I tried installing different modules and everything, I tried what was suggested here, I was already a user. I went to go get jack in the box, then remembered I changed some network settings in Virtual Box before the update, and guess what editing them back fixed it. Took me 2 weeks to remember that I had done that lol.

---

