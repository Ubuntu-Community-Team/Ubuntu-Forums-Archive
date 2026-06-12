---
title: "Virtualbox Website Sharing"
date: 2010-06-26
forum: Programming Talk
---

### Post by volobiz on 2010-06-26
I have Oracle Virtualbox installed on Windows 7 and I boot Ubuntu 10.04 LTS inside that. I have my PHP website working successfully locally inside of Ubuntu. Now I want to flip back to Windows 7 outside of the VM and connect to that new website. How is this accomplished?

I did ifconfig to find the VM IP address and tried to attach to that, but it failed. I then tried on Win 7 as well to connect to [http://127.0.0.1/](http://127.0.0.1/), but that failed too.

---

### Post by Milliways on 2010-06-26
> **volobiz said:**
> I have Oracle Virtualbox installed on Windows 7 and I boot Ubuntu 10.04 LTS inside that. I have my PHP website working successfully locally inside of Ubuntu. Now I want to flip back to Windows 7 outside of the VM and connect to that new website. How is this accomplished?

I did ifconfig to find the VM IP address and tried to attach to that, but it failed. I then tried on Win 7 as well to connect to [http://127.0.0.1/](http://127.0.0.1/), but that failed too.

It depends on how you have VirtualBox networking setup.
The default NAT allows the VM to access the network, but not the host machine.

You will need to set up Bridged networking. I use this for filesharing.

Read the section in help. This is rather confusing, but worth the effort to understand.

---

### Post by volobiz on 2010-06-26
Thanks, that fixed it! I needed to go into Virtualbox, disable the regular NAT adapter, create a new adapter, set it to Bridged, choose my physical adapter in the host OS (like wired or wireless adapter), click OK, and then boot the Ubuntu VM. Once up, I ensured my Linux firewall was down (or recommend one brings it up on Linux and poke holes out for what you need to share), and then did 'ifconfig' to find the local IP address. From there, I went to the Windows host OS and typed that address into a browser, and *kapoof* I could now start testing websites with my LAMP development.

---

