---
title: "[SOLVED] X fails to start; suspected reseting of /home permissions."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Crandom on 2008-10-22
I tried to do a hibernate using the new intrepid beta and it went to sleep alright, but then refused to wake up. I left it for ten minutes then turned off the power at the switch. When I turn it off again, X fails to start giving a generic "X failed to start" error.

I log in using the text base stuff but it continually gives me errors about "locks" and read only permissions in my /home directory.

I booted up a livecd and looked at the /home section's properties (on my local hdd - it's ext3) and it gave this:

Owner: 1000
Folder access: Create and Delete
File Access: ---

Group: 1000
Folder access: Access files
File Access: ---

Others
Folder access: Access files
File Access: ---

To me this dosn't look right (0 means no access - x000 means no access to anything?), what are the standard permissions for the /home directory and is this the problem?

Thanks in advance.

---

### Post by prshah on 2008-10-22
> **Crandom said:**
> 
I booted up a livecd and looked at the /home section's properties (on my local hdd - it's ext3) and it gave this:
Owner: 1000
Folder access: Create and Delete
File Access: ---
Group: 1000
Folder access: Access files
File Access: ---
Others
Folder access: Access files
File Access: ---


First of all, booting off a live CD and (manually) mounting an ext3 partition will not show the actual permissions on the running system (ie, when you have booted normally).

Secondly, the "/home" off the live CD is different from the "/home" on your HDD.

Thirdly, the "1000" shown above is the Group ID / User ID (GID/UID) and has nothing to do with permissions.

The permissions for home (live CD) look fine.

Boot back into your (broken) system, and from the console, give the command ```
startx
```; post back error messages. Also the output of the following commands will be useful```
tail /var/log/Xorg.0.log
tail /var/log/messages
```

---

### Post by Crandom on 2008-10-22
Ok, the problem wasn't with permissions (as prshah guessed) but that the filesystem was locked or something. I booted up in recovery mode and did fsck to both my / and /home, then mounted them. I then fixed X using "sudo aticonfig -f --initial" and did "startx". Now it works!

Thanks,prshah, for your help and helping me to understand that permissions problem.

---

