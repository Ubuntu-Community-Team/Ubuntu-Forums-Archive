---
title: "ssh"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-30
Hi,
Can I install ssh from Synaptic and then access my home computer remotely?
If so, is this a very complicated process for a noob?

---

### Post by eightmillion on 2008-07-30
Yeah, look for openssh-client

---

### Post by Claus7 on 2008-07-30
Hello,

to install it, it ain't. To connect correctly it might be. In order to connect to a remote pc, first of all you have to have enabled the access of this pc from the outside world (from System->Preferences->Remote Desktop). 
Now if you are in your computer, what you have to do is to type :
```
ssh -Y user_name_of_remote_pc@ip_address
```
and if you give your password you will be able to connect (the password in the remote pc).

With the -Y option you will be able to have some additional options. For example if you type :
opera
in the remote pc, this will open a window of opera, something that you won't be able to do without the -Y option.

Regards!

---

### Post by bodhi.zazen on 2008-07-30
See :

[uwiki]SSHHowto[/uwiki]

and

[uwiki]AdvancedOpenSSH[/uwiki]

If you are on windows, check out putty

---

### Post by cariboo on 2008-07-30
You also have to set up port forwarding in your router. If you are going to be doing this on a regular basis, it is best to set up a static ip address on your computer. Have look at this link to setup a static ip:

[http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html](http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html)

Depending on your router you will have to look at the documentation to set up port forwarding.

Jim

---

