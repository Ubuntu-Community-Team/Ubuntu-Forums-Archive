---
title: "[SOLVED] Virtual box-- How to add user to group"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by rraj.be on 2008-06-03
when i satrted my virtual box its displaying that

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 
```

How can i add myself to that user group

---

### Post by mjskia1 on 2008-06-03
Unless I'm mistaken, the command to add yourself to a group is

```

sudo usermod -a -G <groupname> <yourlogin>

```

This should add you to a group without changing any of your other group settings.  And yes, you'll need to log out and log back in again before the change takes effect.

---

### Post by akiratheoni on 2008-06-03
sudo adduser yourusername vboxusers

---

### Post by wormser on 2008-06-03
The GUI method:

System> Administration> Users and Groups> Unlock> Manage Groups> Highlight desired group> Properties> Check mark the user and exit out.

---

