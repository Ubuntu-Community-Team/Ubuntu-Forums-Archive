---
title: "Plesk upload"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by dunbrokin on 2008-07-19
I am trying to upload a HTML site to set up a web page on Plesk....I get the following error when I try to upload the file....

 Unable to upload StrongboxWebPage.html to /StrongboxWebPage.html: filemng failed: cp: /usr/local/www/vhosts/strongboxwealth.co.nz/StrongboxWebPage.html: Permission denied
filemng: Error occured during /bin/cp command.

What am I doing wrong?.....Ah...I am using Linux...so I need a different way of doing things....but what does this mean?


If your are using a Linux or FreeBSD operating system on your local computer and
have access to server shell, use the &#8216;scp&#8217; command to copy files and directories to the
server: scp your_file_name [email]login@remoteserver.com[/email]:path to copy files, and scp
&#8211;r your_directory_name [email]login@remoteserver.com[/email]:path to copy entire directories.
After publishing, you will be able to work with files and directories on your account
using SSH terminal web application integrated in your Plesk control panel (Home > SSH
Terminal).

---

### Post by pavel989 on 2008-07-19
well first, it could be permission issues. but all it means is u use a terminal to do those commands. how r you trying to upload right now?
and who owns the files?

try doing a "sudo chmod 777 ./FILE_NAME" and try again maybe.

---

### Post by dunbrokin on 2008-07-19
> **pavel989 said:**
> well first, it could be permission issues. but all it means is u use a terminal to do those commands. how r you trying to upload right now?
and who owns the files?

try doing a "sudo chmod 777 ./FILE_NAME" and try again maybe.

Nope chmod 777 did not work....

---

### Post by pavel989 on 2008-07-19
did u try the scp stuff?

---

### Post by dunbrokin on 2008-07-19
> **pavel989 said:**
> did u try the scp stuff?


Yup...but not sure if I did it right....Did not appear anywhere on the Plesk server.....well not that I can see anyway...Did not get any error messages...but that means squat ..

---

### Post by pavel989 on 2008-07-19
have u ssh 'd to it?

---

### Post by pavel989 on 2008-07-19
er exactly what was the code u used?

---

### Post by dunbrokin on 2008-07-19
> **pavel989 said:**
> er exactly what was the code u used?


Cant find the SSH....have scp'd it in the format suggested (least my interpretation of the format)

---

### Post by pavel989 on 2008-07-19
if you know the address, u can use ssh from a terminal:

```
ssh address
```

it could be ssh open address, idr

---

