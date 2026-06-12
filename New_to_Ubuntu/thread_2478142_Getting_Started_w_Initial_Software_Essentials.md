---
title: "Getting Started w Initial Software Essentials"
date: 2022-08-17
forum: New to Ubuntu
---

### Post by dmacpeak on 2022-08-17
This going to seem like a very dumb post, but I was excited to hit the ground running w Ubuntu 20.04 and I haven't gotten very far.

I thought you could download software from the store, but everything I want seems to have a 50 step installation process and can't be download from the store.  

I knew there'd be a learning curve but I wanted my firewall and VPN functioning before I started the learning process and I'm not even sure I'm going to be able to handle that?

Why can't I just download a VPN and use it from the software store and same with firewall?

---

### Post by poorguy on 2022-08-17
Ubuntu 20.04 comes with a default ufw firewall and the default settings have always worked well from my experience.

Open the terminal Ctrl+Alt+t and copy and paste this command and press enter and then enter your password.

```

sudo ufw enable

```

To check the ufw status enter this command.

```

sudo ufw status

```

Or

```

sudo ufw status verbose

```

---

### Post by poorguy on 2022-08-17
A good read.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)


This may be helpful.

[https://www.tutorialspoint.com/ubuntu/ubuntu_software_center.htm](https://www.tutorialspoint.com/ubuntu/ubuntu_software_center.htm)

---

### Post by Impavidus on 2022-08-18
There are zillions of software packages in the wild and only a few thousand in the Ubuntu repositories, from where you can install them with a few clicks. If you're somewhat flexible in what you need, you can get most things from there. What's in the repos is generally better maintained and checked for bugs and security holes than what you find on random websites. Those 50 steps to install something, you want to avoid. It's also 20 steps to install the bugfixes and a nightmare to keep things secure and working together. Currently, I've just two applications not from the official repos.

A firewall is built-in. What isn't built-in is a GUI to configure it.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by dmacpeak on 2022-08-18
Thanks for all the posts. I am very grateful and have what I need for the VFW.
Can I get a VPN from the software repository? I'd imagine I'd have to configure it with ports and so forth which I may not be able to do but I'd love to hear any suggestions.

---

### Post by ActionParsnip on 2022-08-18
openvpn is available as a client but you need a VPN endpoint to connect to. You don't just "get a VPN" in any OS, Ubuntu or otherwise.

---

### Post by dmacpeak on 2022-08-18
Thanks guys, I did both the VPN and the firewall!!!!

---

### Post by TheFu on 2022-08-19
Linux and Unix have steep learning curves. This is because prior skills are necessary to move onto more complex tasks.  It is like a human learning to crawl, stand, wobble, walk, jog, run, sprint, sprinting with hurdles, and then an obstacle course.  Don't expect to walk immediately.  Running simple server stuff is "walking" level, but some server things are sprinting and some are obstacle courses.

Unix and Linux systems are all a little different, because there are 50-500 different ways to do anything.

There are 5+ firewall interfaces into the kernel firewall.  Each is a little different, each has different capabilities, strengths and weaknesses.  ufw is one, gufw, iptables, nftables, firewalld, and a few others exist.

There are 50+ different VPNs.  Most of the time, a paid VPN service is required, so we are limited to what the paid provider supports. If you aren't paying to use a VPN, chances are good that it isn't very secure or anonymous.  All your browsing and connection data is being sold. Some is used for espionage by state actors.
There are IPSec, openvpn, wireguard, L2TP VPNs.  I think the security industry considers IPSec to be the most secure, but using it is a hassle.  Wireguard is good and fast, for simple setups. It is relatively new, so security, which is believed to be good, is unproven.  openvpn has been around a long time and supports all sorts of options for almost any need, but it is complex to setup and uses SSL/TLS, which gets cracked every few years.  This ignores all the other VPNs, like tinc or nebula. They have a place too.  Just depends on your needs.

Using a VPN client is fairly straight forward, but only if the server-side team did a good job.  Also, the client setup has very little control over the security, so if you want true security in a VPN, I wouldn't trust it unless I'd setup the server myself.  Nobody cares about your security and privacy as much as you. Nobody.

Firewalls are just 1 aspect of the require security layers.  You want 3+ layers, more if possible.

---

### Post by iamjiwjr on 2023-02-01
Install gufw. Easy gui to enable firewall. I add synaptic, gdebi, neoftech, nautilus-admin, gnome-cards-data, lm-sensors, ubuntu-restricted-extras, gnome-tweaks, and gnome-shell-extensions-manager. My Brother printer does not like the auto-printer-id function, so I also delete ipp-usb and sane-airscan before adding my scanner driver manually (printer driver installed by default). Personal choice - I add gstreamer-plugins-bad because I can't play some videos if I don't. Also personal choice, I add flatpak. Then I add the flatpak repo (flathub web site) and reboot. After all this I'm ready to start to fine tune my settings and tweaks and extensions. Then I can install my apps via debs, snaps, or (by command line copy paste) flatpaks.

---

