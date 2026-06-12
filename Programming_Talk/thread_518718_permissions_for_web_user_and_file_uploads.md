---
title: "permissions for web user and file uploads"
date: 2007-08-06
forum: Programming Talk
---

### Post by adza on 2007-08-06
hi there, i've just deployed a neat little app to my website that allows me to upload and download files etc. Thus allowing me a little code management tool at work :) I have a security concern however, the move_uploaded_file() function doesn't seem to want to work unless the permission on the target directory (not web root) are set to 777. Doesn't this then allow the potential for malicious code to be executed in this dir? I tried setting it to 766 however the function doesn't work then... any suggestions?

---

### Post by jnorthr on 2007-08-06
The code 766 does remove some rights to the folder for 'group users' and 'all others' but since you have '7' for the superuser you should be able to log yourself on as root and make it work like before. Just a guess, though. sorry.

---

### Post by pmasiar on 2007-08-06
Hosted web account? you are not superuser? Or is it your own box?

---

### Post by bbzbryce on 2007-08-07
> **adza said:**
> hi there, i've just deployed a neat little app to my website that allows me to upload and download files etc. Thus allowing me a little code management tool at work :) I have a security concern however, the move_uploaded_file() function doesn't seem to want to work unless the permission on the target directory (not web root) are set to 777. Doesn't this then allow the potential for malicious code to be executed in this dir? I tried setting it to 766 however the function doesn't work then... any suggestions?

Yes you will have this problem and thus it is important to know what is being uploaded or take precautions to only allow specific types of files. The folder that you are uploading to needs to be writable by the apache user thus unless it's owned by the apache user, or similar group, it needs to be 777. However this is why there is also a file execute privilege. Thus make sure after uploading that the execute permission is not granted on uploaded files. In addition as long as the location being uploaded to is not web accessible then you shouldn't have a problem with a file being executed in that way.

---

### Post by adza on 2007-08-08
So i could chown the folder that is being written to (this isn't web accessable btw) to the apache user then? i am comfortable with this folder being away from the web root, and the upload mechanism is 'protected' behind a password protected logon.. but still i would like to take  every protection...

---

