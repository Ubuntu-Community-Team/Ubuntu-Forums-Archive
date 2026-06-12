---
title: "Home network and file share"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by corkscrew on 2008-10-26
I have a network at home which is comprised of 2 desktops and 2 laptops and 1 LAN hardrive (for backups) win xp on all pc's.

I have installed ubuntu hardy heron to 1 desktop and  1 laptop (dualboot).

Currently under windows i can transfer files back and forth between any of the machines. Under ubuntu i can see the windows network and move files back and forth.

How can i transfer files between the laptop and desktop when they are both on ubuntu, all i can see in the network places is the windows network?

---

### Post by Amarsingh0793 on 2008-10-26
If I were you, I would right click on the Public Folder (located in your Home Folder), go to properties, click on "Share" and tick the check box that says "Share this Folder" and also the "Allow other people to write in this folder" checkbox. 

After doing this, the public folder will be visible on the Network folder (Places > Network ....).

Hope this Helps :)

---

### Post by HellNoire on 2008-10-26
> **Amarsingh0793 said:**
> If I were you, I would right click on the Public Folder (located in your Home Folder), go to properties, click on "Share" and tick the check box that says "Share this Folder" and also the "Allow other people to write in this folder" checkbox. 

After doing this, the public folder will be visible on the Network folder (Places > Network ....).

Hope this Helps :)

Personally, I find I need to install Samba as well. It's in the repositories, just search Samba. Install it, select the folder you want to share, hit Add, choose to allow everyone and the guest account enable.

Then I do what Amarsingh suggests, because for me, it often told me you need root access or something (I don't remember to be honest) but it didn't work out of the box.

---

### Post by corkscrew on 2008-10-26
When I select share this folder i get a message "windows networks sharing service needs to be installed" 
If i just have the 2 linux boxes running why would i need this?

---

### Post by handydan918 on 2008-10-26
> **corkscrew said:**
> When I select share this folder i get a message "windows networks sharing service needs to be installed" 
If i just have the 2 linux boxes running why would i need this?

You don't need to . There are other file sharing protocols that Linux can use. But if you  are in a mixed environment anyway, Samba is the simplest way to get all the machines talking.

---

