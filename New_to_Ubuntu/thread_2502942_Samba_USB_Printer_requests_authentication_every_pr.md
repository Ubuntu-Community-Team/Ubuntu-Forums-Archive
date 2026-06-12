---
title: "Samba USB Printer requests authentication every print job"
date: 2024-12-06
forum: New to Ubuntu
---

### Post by jwcalvert on 2024-12-06
New to Ubuntu.  Here is my problem!
I am trying to print to a USB printer shared from a Windows PC.
It all works _fine_  but the Ubuntu PC _always _requests an authentication for every print job.
I created a new User ( and password) in Windows with Administrator authority and I successfully use it to authenticate each print job.

I have a Ubuntu 24.04 PC
I have a Windows 11 Pro PC.

I have installed samba in the Ubuntu PC.
I have tried several different things; no luck.

Does anyone have a solution please.

---

### Post by him610 on 2024-12-07
I don't know your setup, but maybe a couple of ideas:

a.  If printer (you did not specify brand/model) is network capable then connect it to your LAN. They work great with different OS-powered systems.

b.  Connect USB printer to your Ubuntu 24.04 machine and share with Win11 PC.

---

### Post by jwcalvert on 2024-12-07
Thanks Him610
I may try your networking idea if all else fails.
But I should be able to fix the samba/cups issue.

I can't share from Ubuntu as there are other PCs that depend on the Win 11 PC.

Cheers

---

### Post by yancek on 2024-12-07
Did you read the instructions at the link below to ubuntu.com explaining this?

[https://documentation.ubuntu.com/server/how-to/samba/print-server/?_ga=2.72564051.1153972298.1733513697-1234211060.1662380174](https://documentation.ubuntu.com/server/how-to/samba/print-server/?_ga=2.72564051.1153972298.1733513697-1234211060.1662380174)

---

### Post by jwcalvert on 2024-12-07
Thanks yancek
Sadly, I tried that and it didn't solve the problem.
It still asks for authentication to print.

Is there any log or other tool that may shed some light on this?
Cheers

---

### Post by yancek on 2024-12-08
You might try posting the contents of the /etc/samba/smb.conf file, at least the printer section of it.  You need to post more than 'it didn't solve the problem'.  What happened?  Did you see any warning/error messages when trying to configure it?  I don't use windows and have never used Samba so can't help with that.

---

### Post by jwcalvert on 2024-12-11
To anyone:
I have been reading somewhat about this issue and am not sure which is causing the authentication request.
Is it Samba or Cups that is doing this?

I need to better understand this, to know which Config file is the problem.
Any ideas?

---

