---
title: "No users in new install"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by newinstall1 on 2012-07-25
Had trouble installing downloaded 12.04 to my older laptop.  All files would install during system install from iso, but would hang every time at end of install. Tried 4 installs, none would finish.

After search, I found several suggestions to use boot repair to get the system to boot from hard drive.

It boots fine, but there are no users on the system.  I can only use the system as "guest", and am not allowed to modify files or add a user.

I tried repair boot and adduser and  useradd as root, but the attempts all fail, as do attempt to change password for root.

Is there a way to add user names and passwords to my install, or do I need to try a  reinstall?

---

### Post by Bufeu on 2012-07-25
Can be a corrupt .iso-file, a bad burner or a bad harddisk in the laptop.

---

### Post by steeldriver on 2012-07-25
> **newinstall1 said:**
> 
I tried repair boot and adduser and  useradd as root, but the attempts all fail, as do attempt to change password for root.

Is there a way to add user names and passwords to my install, or do I need to try a  reinstall?

how does it fail, exactly? what error message do you get?

newer distributions mount the filesystem readonly in recovery mode - which prevents password changes unless you remount rw

---

### Post by newinstall1 on 2012-07-25
> **steeldriver said:**
> how does it fail, exactly? what error message do you get?

newer distributions mount the filesystem readonly in recovery mode - which prevents password changes unless you remount rw

The message was "unrecoverable error".  It appeared to happen as the boot sector was being written.

This is a new hard drive, and is booting properly now, but there are no users installed on the system.  I tried to remount the filesystem "rw" in the recovery console, nogo there either.

In other, older linux systems, I could easily login as root and fix all this.

---

### Post by d4m1r on 2012-07-25
Is it an old machine? Specs of the hardware? If it is, try installing 11.10 instead. I had a similar issue.....

---

### Post by newinstall1 on 2012-07-26
> **d4m1r said:**
> Is it an old machine? Specs of the hardware? If it is, try installing 11.10 instead. I had a similar issue.....

From 2005, didn't think it was too old for the install.  Tried your suggestion, and it worked.

Now I am afraid to let it auto-upgrade, will that cause me problems?

Thanks for the reply and the suggestion.

---

