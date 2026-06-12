---
title: "Unable to add to sudoers list"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by chinna saaeb on 2013-04-25
I am using ubuntu 12.04 lts
I created a user and added to sudoers list using
sudo adduser username sudo.

Then in the /etc/sudoers i  made the following change
%sudo   ALL=(ALL:ALL) ALL
to 
sudo   ALL=(ALL:ALL) ALL

Now after that neither me nor the new user are in sudoers list (
I had to set root passwd and only root has the rootly power. neither me nor the newuser has
Can anybody advise?

---

### Post by Cheesemill on 2013-04-25
> **chinna saaeb said:**
> Then in the /etc/sudoers i  made the following change
%sudo   ALL=(ALL:ALL) ALL
to 
sudo   ALL=(ALL:ALL) ALL

You shouldn't have done this.

The % means group, that line meant that everyone in the sudo group has sudo privileges.

By removing the % you changed the line to mean that the user sudo (instead of the group) has sudo privileges (this user doesn't exist), thereby removing everyone in the sudo group from your sudoers declarations and locking them out.

Change that line back to what it was originally, either by booting in recovery mode or from a live CD.

---

### Post by schragge on 2013-04-25
You also can try
```
pkexec visudo
``` to edit */etc/sudoers* without rebooting. It should work on newer Ubuntu releases as PolicyKit can grant you root privileges independent of sudo.

---

### Post by chinna saaeb on 2013-04-25
Thans It worked

---

### Post by erniej on 2013-05-10
schragge, I have tried every suggestion for editing the /etc/sudoers.d/ or the /etc/sudoers.d/README file, including the new one (pkexec visudo) you posted above (I'm running Ringtail 13.02). In every case I get Permission Denied, whether I'm root or not. Both you and Chinna saabe seem to have no problem opening and editing the file. I can open /etc/sudoers.d as a tmp file, but it won't let me save the changes. 

I've been working on this off and on for two weeks without success. I have new software to install and I dread the endless authentication calls I know I'm going to face if I try to do it without changing the etc/sudoers.d/ file. Any suggestions will be deeply appreciated. I've run out of suggestions to try in the Ubuntu Forums.

---

### Post by matt_symes on 2013-05-10
Hi

/etc/sudoers.d/ is a directory, although /etc/sudoers.d/README is a file.

Are you sure your not trying to edit the file /etc/sudoers instead ?

You should be able to edit it from a root shell from the recovery menu from grub. 

You may have to remount the root partition read/write.

```
mount -o remount,rw /
```

then edit the file.

If not please post back

```
ls -l /etc/sudoers
```

and 

```
lsattr /etc/sudoers
```

from the recovery console.

EDIT:

If for some really odd reason you can't change it from the recovery consoles root shell, edit your kernel command line and add

```
init=/bin/bash
```

to boot into a bash shell. Mount the root partition read/write and edit it that way.

BTW: Your root partition is being mounted read/write ? Check in dmesg or by using the mount command (i assume you're using ext4 ?)

Kind regards

---

