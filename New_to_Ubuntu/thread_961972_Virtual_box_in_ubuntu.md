---
title: "Virtual box in ubuntu"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by elleppahc on 2008-10-28
Re Virtual Box.
Can someone help me.
I'm a newbie to ubuntu, well its good but what a learning curve.
I am trying to run virtual box and now get the following message

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).

Can you tell me what to do to resolve this in simple terms of code.Many thanks in advance.

---

### Post by brandoncolorado on 2008-10-28
[http://tinyurl.com/69smx](http://tinyurl.com/69smx)

"if u get error message after load iso Operation System like :

VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE

fix with this command

sudo chmod 666 /dev/vboxdrv

---

### Post by brandoncolorado on 2008-10-28
Another helpful post:

[http://forums.virtualbox.org/viewtopic.php?t=3776](http://forums.virtualbox.org/viewtopic.php?t=3776)

---

### Post by stonecoldjha on 2008-10-28
go to system>administration>users and groups.key in your password and unlock it,look for a group called vbox users(after clicking manage groups),click on properties,and change the group ID to 1001,now make it accessible to the root and the username(Group members).click OK.things should now work.

---

### Post by elleppahc on 2008-10-29
I cannot add to user.
How do I do this?

---

### Post by Drakkor on 2008-10-29
I think you have to "unlock" it

---

### Post by elleppahc on 2008-10-29
OK.
How do I do that?

---

### Post by Therion on 2008-10-29
Go here: [http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

See the section: **Prepare booting your VM** for step-by-step instructions.

---

### Post by elleppahc on 2008-10-29
can open  system/admin/users and groups/manage groups.
at this point the next screen is all greyed and I can do nothing to add myself to the vbox group??

---

### Post by uidb4056 on 2008-10-29
> **elleppahc said:**
> can open  system/admin/users and groups/manage groups.
at this point the next screen is all greyed and I can do nothing to add myself to the vbox group??

You must press the button Unlock before pressing Manage Groups button, you will be asked for your password and the you will be able to modify.

---

### Post by elleppahc on 2008-10-29
Yes tried that and got message could not validate

---

### Post by uidb4056 on 2008-10-29
Are you sure to enter the password right?

---

