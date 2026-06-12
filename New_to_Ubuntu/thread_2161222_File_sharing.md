---
title: "File sharing"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by anthonyc42 on 2013-07-09
Hello all, I am trying to have my Ubuntu server and windows 7 machine talk to each other I have installed samba with no luck and I continue to get an error message on the windows side saying I do not have the correct permissions. then on the Ubuntu side I do not see windows at all. any thoughts on how I may be able to fix this? thanks

---

### Post by sandyd on 2013-07-09
Generally, you can share folders on Ubuntu by right clicking on a folder, selecting properties, and enabling sharing from the properties window.

This does not work if your Windows 7 installation has homegroups enabled.

---

### Post by anthonyc42 on 2013-07-09
hello sandyd, I turned off the homegroup setting but it says I am still not authorized to access the drive. it gives this error message "The account is not authorized to log in from this station".

---

### Post by Iowan on 2013-07-09
I haven't dealt with Windows 7. Have you created user accounts (Linux and Samba) on the Ubuntu machine?

---

### Post by anthonyc42 on 2013-07-09
I have two accounts right now on the Ubuntu machine they are both admin accounts one has no password I thought that might make it easier but it did not :(.

---

### Post by Iowan on 2013-07-09
I haven't tried the right-click/share method, either. :oops:
I've always used smb.conf which requires the user to have both a Linux account AND a Samba account.
If I click on the Home folder, then **Browse Net...**, I can see my Samba server and a Windows 7 machine (not mine).

---

### Post by sandyd on 2013-07-10
> **anthonyc42 said:**
> hello sandyd, I turned off the homegroup setting but it says I am still not authorized to access the drive. it gives this error message "The account is not authorized to log in from this station".

I remember a setting I had to set on the windows side....except that I am running windows 8.

Give me a sec, and I will tell you the options you have to set

---

