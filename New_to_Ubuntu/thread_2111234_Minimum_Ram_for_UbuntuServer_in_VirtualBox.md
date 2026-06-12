---
title: "Minimum Ram for UbuntuServer in VirtualBox?"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by Roskow on 2013-02-01
I'm trying a new setup for learning Linux OSes. 

I put the Debian Squeeze Graphical install on as the host OS on an old Desktop PC which has 1GB of Ram.  

I have installed Virtual Box and so far added Ubuntu Server to it and everything is working and updating. (I did change a Network setting from NAT to Bridge)

The question of Memory is that I would like to install more virtual machines and run them at the same time if I can. I would like to have Virtual Box run Ubuntu Server, Debian(command line install), and CentOS. 

I'm learning these for a college project. 

Ubuntu Server will run "Moodle" and DNS. Also, hopefully Nagios and maybe Suricata

CentOS: will run an e-Commerce site

Debian(CLI): will run email

It doesn't seem like this should be memory intensive stuff especially if two OSes are CLI.

---

### Post by snowpine on 2013-02-01
The bare minimum RAM for Ubuntu Server is 128mb according to the official page: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Server Guide has more info: [https://help.ubuntu.com/12.04/serverguide/preparing-to-install.html](https://help.ubuntu.com/12.04/serverguide/preparing-to-install.html)

---

### Post by kanikilu on 2013-02-01
So you have a machine running Debian with X/GUI, acting as the VirtualBox host, and want to run 3 VM's simultaneously? On 1GB of RAM?

Seems like it wouldn't be enough, but since they are just VM's, there's nothing stopping you from trying, just keep lowering the allocated RAM until you find how far you can take it, I guess..

To more directly answer your question, technically 128MB of RAM is the minimum:

[https://help.ubuntu.com/12.04/serverguide/preparing-to-install.html](https://help.ubuntu.com/12.04/serverguide/preparing-to-install.html)

// too slow^ ;-)

---

### Post by Roskow on 2013-02-01
Okay thanks. Just wondering how much I can squeeze out of this old Desktop. 

For now I gave Ubuntu Server 200 MB. I'll see how it goes when I add other machines.

---

### Post by Roskow on 2013-02-01
Yeah I don't think I can pull of 3 lol. Maybe 2. 

Oh well thanks for the quick replies.

---

