---
title: "Network Manager + MadWiFi Drivers"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by Blackcabs on 2008-06-27
Hi there everyone, I am total newbie to Ubuntu and so far I'm enjoying every minute. However i am stuck with a couple of things, please can someone tell me how to disable network manager and how to enable it again should i get stuck setting up my accounts manually. Also i am trying to install the  madwifi-ng drivers for my WiFi card but when i try to remove the already loaded modules,, I am told "permission denied cant remove" even though i am logged in as root.:confused:

Thanks Paul

---

### Post by caljohnsmith on 2008-06-27
> **Blackcabs said:**
> Hi there everyone, I am total newbie to Ubuntu and so far I'm enjoying every minute. However i am stuck with a couple of things, please can someone tell me how to disable network manager and how to enable it again should i get stuck setting up my accounts manually. Also i am trying to install the  madwifi-ng drivers for my WiFi card but when i try to remove the already loaded modules,, I am told "permission denied cant remove" even though i am logged in as root.:confused:

Thanks Paul
When you say you are setting up your accounts manually, do you mean with ifconfig and iwconfig? You don't need to disable network manager that I'm aware of if you set up your connection manually with ifconfig/iwconfig; just don't open network manager and change anything with it. :)

And are you aware that Ubuntu all ready comes with the madwifi drivers preinstalled? You shouldn't need to install madwifi unless for some reason you need the latest svn release or something. Also, to remove modules you would use "sudo modprobe -r <module name>", and you don't want to physically move the module file to uninstall it. 

What is your atheros chipset that you are trying to use with madwifi? (i.e. what does the output of "sudo lshw -C network" return for your wireless card?)

---

### Post by Blackcabs on 2008-06-28
Thanks for replying caljohnsmith for some reason i thought that if i disabled Network manager i would no longer be able to connect to the net unless i configured my eth0 & ath0 devices manually ifconfig iwconfig etc. Also i did'nt realize that Ubuntu came with the madwifi drivers already installed, as for the chipset its a ar5212. Maybe i should start over as i have already updated to the most recent madwifi drivers

---

