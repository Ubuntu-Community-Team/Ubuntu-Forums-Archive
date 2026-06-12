---
title: "File permissions after system reinstallation"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by liherb on 2013-01-08
If I set all my files' ownership to my current username, and later on I re-install Ubuntu with another username, will I have problem opening my files? I mean after backing up and restoring to the new username.  Does the permission system recognize that I am Not who I was just because I re-installed Ubuntu and choose a new username?  Many thanks.

---

### Post by Cheesemill on 2013-01-08
Permissions are based on your UID (user ID) and GID (group ID).

Ubuntu uses UID's starting at 1000 for any users you create on your system, the user that you create during installation will have a UID and a GID of 1000.

If you re-install Ubuntu and then restore users home directory's the permissions will be OK as long as the users were created on the new machine in the same order that they were created on the old machine.

---

### Post by liherb on 2013-01-08
Thank you for your reply. However it begs another question.  If it is based on UID/GID, then there could be a potential security hole. 
For example, if on computer A I am not a root user and I don't have permission to certain files. But no problem, I could simply copy those files from computer A to computer B(on which I am the root user), then Bingo. My UID is 1000 and all of sudden I have all the permission.
Is my understanding correct?

---

### Post by Cheesemill on 2013-01-08
How are you going to copy the files from machine A if you don't have read access to the files? Anyway, if anyone has physical access to any of your machines they can access whatever files they want by just booting it from a Live CD.

Physical access = Root access.

The only way to protect against this is to use encryption on either individual files, your /home directory or the entire drive.

---

