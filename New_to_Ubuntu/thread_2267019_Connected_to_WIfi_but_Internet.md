---
title: "Connected to WIfi but Internet"
date: 2015-02-26
forum: New to Ubuntu
---

### Post by Amber_McCrea on 2015-02-26
Hello,  

I am trying to update some laptops at work but in order to do so I need to download the files.  I have managed to reset the root password and restart the network manager.  I am getting a wifi signal but when I check ifconfig I am getting an odd address (we are a 192 network and the address is a 10 network).  My best guess is that I am not getting DNS service on the laptops.  The current release is ubuntu 10.04 (no I can't wipe them using a usb install - tried that first and cd-rw not dvd so no go on that route either).  

Is there anyway it force it to update the DNS ?

Thank you in advance.

---

### Post by TheFu on 2015-02-26
a) 10.04 desktop support ended 2 yrs ago.

b) I think it is a DHCP issue. Are you connecting to the correct AP?

c) If you need to support more than 5 systems, a tool like Ansible will really make that faster, but a solid network will be needed.

d) Ubuntu doesn't use root. We use sudo and any devops tool will support that method.

---

### Post by mörgæs on 2015-02-27
Yes: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I would go for a fresh install of 14.04.2 using wired internet access to begin with, wifi comes later. If the computers are old then Lubuntu is an option.

---

### Post by sandyd on 2015-02-27
> **mörgæs said:**
> Yes: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I would go for a fresh install of 14.04.2 using wired internet access to begin with, wifi comes later. If the computers are old then Lubuntu is an option.

They will have to use Lubuntu as they have no dvd drive. If you want to use CD over USB to install, you can only install Lubuntu 14.04 LTS. Otherwise, other lighter distributions recommended in the thread will be fine

Don't use Lubuntu 14.10 (the option on the download site by default). It doesn't fit on CD.
Lubuntu 14.04 LTS seems to be the way to go. [http://cdimages.ubuntu.com/lubuntu/releases/14.04.1/release/](http://cdimages.ubuntu.com/lubuntu/releases/14.04.1/release/)

---

### Post by TheFu on 2015-02-27
> **sandyd said:**
> They will have to use Lubuntu as they have no dvd drive.

Don't use Lubuntu 14.10 (the option on the download site by default). It doesn't fit on CD.
Lubuntu 14.04 LTS seems to be the way to go. [http://cdimages.ubuntu.com/lubuntu/releases/14.04.1/release/](http://cdimages.ubuntu.com/lubuntu/releases/14.04.1/release/)

Or use a USB flash drive?

---

### Post by sandyd on 2015-02-28
> **TheFu said:**
> Or use a USB flash drive?

Gak, read the first post wrong, thought it said they couldn't boot using USB

---

### Post by TheFu on 2015-02-28
> **sandyd said:**
> Gak, read the first post wrong, thought it said they couldn't boot using USB

I can only imagine the number of posts you see daily. Easy to mix some up - I do, often.

---

