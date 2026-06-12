---
title: "Connecting windows 7 with Kubuntu 10.04"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2011-10-16
I have Kubuntu 10.04 installed in my desktop and Windows 7 installed in acer AOD52. My question is how to create work group in Kubuntu and how to add the windoes7 installed laptop to that linux work group. I have a Huawei Broadband modem come router.

Thank you

---

### Post by Lisiano on 2011-10-16
Linux has no concept of Workgroups (There are domains though, all have the default .local domain by default, Windows too)
To access the files on Kubuntu from Win7, right click any folder you wish to share, Properties and Share. Now just either find the Kubuntu box on the network in Win7 or type it's IP. Reverse is the same, cept if you wish to enter by IP, you need to prepend it by smb://

Note that even though Linux has no concept of Workgroups, Samba (The system that allows you to share files between computers) will tell the network that your Kubuntu box is in the Workgroup group (The default for Windows if you don't change it).

---

