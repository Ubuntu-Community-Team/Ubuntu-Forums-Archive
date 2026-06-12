---
title: "network problem"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by prifer on 2008-08-31
Hi,
I am facing problem with networking. I can not be connected to others computers and so I can't print on other computer using network. But I can use my local Network email and browsing internet.
please your suggest, thank you

---

### Post by mellowd on 2008-08-31
More info is needed about the network itself. More details about the other pc's and routers/switches involved

---

### Post by pi.boy.travis on 2008-08-31
> **prifer said:**
> Hi,
I am facing problem with networking. I can not be connected to others computers and so I can't print on other computer using network. But I can use my local Network email and browsing internet.
please your suggest, thank you

What do you mean by "local network email and browsing internet?"  Do you mean that your router isn't working but you can connect directly to your modem?  Can you see other computers on the network, but you can't use SAMBA to access printers or files?   More info please.

---

### Post by prifer on 2008-08-31
it used to work normally printing out on other computer using network, but after I installed some softwares, etc..and maybe accidentally pushed wrong button, now I can't print through network anymore

---

### Post by pi.boy.travis on 2008-08-31
What software did you install?

---

### Post by prifer on 2008-08-31
> **pi.boy.travis said:**
> What do you mean by "local network email and browsing internet?"  Do you mean that your router isn't working but you can connect directly to your modem?  Can you see other computers on the network, but you can't use SAMBA to access printers or files?   More info please.


I am in my office and using LAN for networking and internet browsing. I have explored network computers but I didnt see others computers as before. I have also tried using Samba to browse available printer on other computers but now it doesnt work (it used to work)

---

### Post by prifer on 2008-09-01
> **pi.boy.travis said:**
> What software did you install?

I dont remember, plenty softwares.
is it related to network setting? bcoz I have tried to change it again and again

---

### Post by pi.boy.travis on 2008-09-01
> **prifer said:**
> I am in my office and using LAN for networking and internet browsing. I have explored network computers but I didnt see others computers as before. I have also tried using Samba to browse available printer on other computers but now it doesnt work (it used to work)

> **prifer said:**
> I dont remember, plenty softwares.
is it related to network setting? bcoz I have tried to change it again and again


When you say that browsing available printers doesn't work, do you mean that you can't see them or they don't print?

What network settings have you changed?  Have you edited and SAMBA configuration files?

---

### Post by prifer on 2008-09-01
> **pi.boy.travis said:**
> When you say that browsing available printers doesn't work, do you mean that you can't see them or they don't print?

What network settings have you changed?  Have you edited and SAMBA configuration files?



I can't see them and I can't print.
Browsing, I mean internet browsing.
I dont remember what network setting I have done. I haven't edited SAMBA config files, I was just seraching printers using SAMBA but failed, nothing appears

---

### Post by pi.boy.travis on 2008-09-01
I occasionally have problems where I can't see SAMBA shares or printers.  I believe there is a bug report filed on Launchpad.  Usually a reboot fixes it for me.

Try going to System-Administration-Printing, and clicking on server settings.  Make sure you have the appropriate boxes checked.  Here is a  screenshot.

[ATTACH]83703[/ATTACH]

Hope this helps. . .

---

